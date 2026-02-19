---
title: Ottimizza in Edge - Fastly (BYOCDN)
description: Scopri come configurare Fastly BYOCDN per ottimizzare in Edge in LLM Optimizer.
feature: Opportunities
source-git-commit: 9230e525340bb951fcd9f2ae1f88bad557d5b7d7
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 5%

---


# Fastly (BIOCDN)

Questa configurazione indirizza il traffico agente (richieste da bot di IA e agenti utente LLM) al servizio back-end Edge Optimize (`live.edgeoptimize.net`). I visitatori umani e i bot SEO continuano a essere serviti dalla tua origine come al solito. Per verificare la configurazione, al termine dell&#39;installazione, cercare l&#39;intestazione `x-edgeoptimize-request-id` nella risposta.

**Prerequisiti**

Prima di impostare le regole VCL Fastly, assicurati di disporre di:

* Accesso a Fastly per il dominio.
* Processo di onboarding in LLM Optimizer completato.
* Inoltro del registro CDN a LLM Optimizer completato.
* Chiave API di ottimizzazione Edge recuperata dall’interfaccia utente di LLM Optimizer.

{{retrieve-byocdn-api-key}}

**Configurazione**

Aggiungi i tre snippet VCL seguenti al tuo servizio Fastly. Questi snippet gestiscono il routing delle richieste di agenti ad Edge Optimize, la separazione delle chiavi della cache e il failover all’origine predefinita.

![Fastly VCL](/help/assets/optimize-at-edge/fastly-vcl.png)

![Aggiungi snippet VCL](/help/assets/optimize-at-edge/add-vcl-snippets.png)

**snippet vcl_recv**

```
unset req.http.x-edgeoptimize-url;
unset req.http.x-edgeoptimize-config;
unset req.http.x-edgeoptimize-api-key;

if (!req.http.x-edgeoptimize-request
    && req.http.user-agent ~ "(?i)(AdobeEdgeOptimize-AI|ChatGPT-User|GPTBot|OAI-SearchBot|PerplexityBot|Perplexity-User)") {
  set req.http.x-forwarded-host = req.http.host; # required for identifying the original host
  set req.http.x-edgeoptimize-url = req.url; # required for identifying the original url
  set req.http.x-edgeoptimize-config = "LLMCLIENT=TRUE;"; # required for cache key
  set req.http.x-edgeoptimize-api-key = "<YOUR API KEY>"; # required for identifying the client
  set req.backend = F_EDGE_OPTIMIZE;
}
```

**snippet vcl_hash**

```
if (req.http.x-edgeoptimize-config) {
  set req.hash += "edge-optimize";
  set req.hash += req.http.x-edgeoptimize-config;
}
```

**snippet vcl_deliver**

```
if (req.http.x-edgeoptimize-config && resp.status >= 400) {
  set req.http.x-edgeoptimize-request = "failover";
  set req.backend = F_Default_Origin;
  restart;
}

if (!req.http.x-edgeoptimize-config && req.http.x-edgeoptimize-request == "failover") {
  set resp.http.x-edgeoptimize-fo = "1";
}
```

**Failover**

Lo snippet `vcl_deliver` gestisce automaticamente il failover. Se Edge Optimize restituisce un errore `4XX` o `5XX`, la richiesta viene riavviata e indirizzata all&#39;origine predefinita in modo che l&#39;utente finale riceva comunque una risposta. Le risposte di failover includono l&#39;intestazione `x-edgeoptimize-fo: 1`.

| Scenario | Comportamento |
| --- | --- |
| Edge Optimize restituisce `2XX` | Al client viene fornita una risposta ottimizzata. |
| Edge Optimize restituisce `4XX` o `5XX` | La richiesta viene riavviata e servita dall’origine predefinita. |
| Risposta di failover | Include l&#39;intestazione `x-edgeoptimize-fo: 1`. |

**Verifica installazione**

Dopo aver completato la configurazione, verifica che il traffico da bot venga indirizzato ad Edge Optimize e che non venga influenzato dal traffico umano.

**1. Verifica traffico da bot (deve essere ottimizzato)**

Simulare una richiesta bot di intelligenza artificiale utilizzando un agente utente:

```
curl -svo /dev/null https://www.example.com/page.html \
  --header "user-agent: chatgpt-user"
```

Una risposta corretta include l&#39;intestazione `x-edgeoptimize-request-id`, a conferma che la richiesta è stata instradata tramite Edge Optimize:

```
< HTTP/2 200
< x-edgeoptimize-request-id: 50fce12d-0519-4fc6-af78-d928785c1b85
```

**2. Test del traffico umano (non dovrebbe essere interessato)**

Simula una richiesta browser umana regolare:

```
curl -svo /dev/null https://www.example.com/page.html \
  --header "user-agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36"
```

La risposta deve **non** contenere l&#39;intestazione `x-edgeoptimize-request-id`. Il contenuto della pagina e il tempo di risposta devono rimanere identici a prima di abilitare l’opzione Ottimizza in Edge.

**3. Come distinguere tra i due scenari**

| Intestazione | Traffico bot (ottimizzato) | Traffico umano (non interessato) |
|---|---|---|
| `x-edgeoptimize-request-id` | Presente — contiene un ID richiesta univoco | Assente |
| `x-edgeoptimize-fo` | Presente solo se si è verificato il failover (valore: `1`) | Assente |

Lo stato del routing del traffico può essere controllato anche nell’interfaccia utente di LLM Optimizer. Passa a **Configurazione cliente** e seleziona la scheda **Configurazione rete CDN**.

![Stato routing traffico IA con routing abilitato](/help/assets/optimize-at-edge/byocdn-CDN-traffic-routed-tick.png)

{{return-to-overview}}
