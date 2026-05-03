---
title: Ottimizzazione nella rete edge - Fastly (BYOCDN)
description: Scopri come configurare Fastly BYOCDN per l’ottimizzazione nella rete edge in LLM Optimizer.
feature: Opportunities
source-git-commit: 13d2f4bbd1f9d3886f89f80df0e76093f2afdf13
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 93%

---


# Fastly (BYOCDN)

Questa configurazione indirizza il traffico da IA agentica (richieste da bot IA e da agenti utente LLM) al servizio back-end Edge Optimize (`live.edgeoptimize.net`). Le persone e i bot SEO continuano a ricevere come al solito i contenuti trasmessi dalla tua origine. Per testare la configurazione, al termine cerca nella risposta l’intestazione `x-edgeoptimize-request-id`.

**Prerequisiti**

Prima di configurare le regole Fastly VCL, assicurati di:

* aver accesso a Fastly per il tuo dominio;
* aver recuperato una chiave API di ottimizzazione edge dall’interfaccia di LLM Optimizer. Per i passaggi, consulta [Recuperare le chiavi API](/help/dashboards/optimize-at-edge/retrieve-api-keys.md#production-api-key).
* (Facoltativo) Per verificare il routing dell&#39;area di gestione temporanea, vedere [Chiave API di gestione temporanea](/help/dashboards/optimize-at-edge/retrieve-api-keys.md#staging-api-key-optional).

**Configurazione**

Aggiungi al tuo servizio Fastly i tre snippet VCL seguenti. Questi snippet gestiscono l’indirizzamento delle richieste agentiche al servizio Edge Optimize, la separazione delle chiavi nella cache e il failover all’origine predefinita.

![Fastly VCL](/help/assets/optimize-at-edge/fastly-vcl.png)

![Aggiungi snippet VCL](/help/assets/optimize-at-edge/add-vcl-snippets.png)

**snippet vcl_recv**

```
unset req.http.x-edgeoptimize-url;
unset req.http.x-edgeoptimize-config;
unset req.http.x-edgeoptimize-api-key;
unset req.http.x-edgeoptimize-fetcher-key; # Optional (required only in case of WAF)

if (!req.http.x-edgeoptimize-request
    && req.http.user-agent ~ "(?i)(AdobeEdgeOptimize-AI|ChatGPT-User|GPTBot|OAI-SearchBot|PerplexityBot|Perplexity-User)") {
  set req.http.x-forwarded-host = req.http.host; # required for identifying the original host
  set req.http.x-edgeoptimize-url = req.url; # required for identifying the original url
  set req.http.x-edgeoptimize-config = "LLMCLIENT=TRUE;"; # required for cache key
  set req.http.x-edgeoptimize-api-key = "<YOUR API KEY>"; # required for identifying the client
  set req.http.x-edgeoptimize-fetcher-key = "<YOUR FETCHER KEY>"; # Optional (required only in case of WAF)
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

Lo snippet `vcl_deliver` gestisce il failover in automatico. Se il servizio Edge Optimize restituisce un errore `4XX` o `5XX`, la richiesta viene riavviata e indirizzata all’origine predefinita, affinché l’utente finale riceva comunque una risposta. Le risposte di failover includono l’intestazione `x-edgeoptimize-fo: 1`.

| Scenario | Comportamento |
| --- | --- |
| Il servizio Edge Optimize restituisce `2XX` | Al client viene trasmessa una risposta ottimizzata. |
| Il servizio Edge Optimize restituisce `4XX` o `5XX` | La richiesta viene riavviata e trasmessa dall’origine predefinita. |
| Risposta in caso di failover | Include l’intestazione `x-edgeoptimize-fo: 1`. |

**Consenti ottimizzazione in Edge tramite regole firewall (facoltativo)**

{{waf-allowlist-setup}}

**Verificare la configurazione**

Dopo aver completato la configurazione, verifica che il traffico proveniente da bot venga indirizzato al servizio Edge Optimize e che il traffico da persone non sia interessato da alcuna modifica.

**1. Test del traffico da bot (deve risultare ottimizzato)**

Simula una richiesta da un bot IA utilizzando un agente utente da IA agentica:

```
curl -svo /dev/null https://www.example.com/page.html \
  --header "user-agent: chatgpt-user"
```

Se il test ha esito positivo, la risposta contiene l’intestazione `x-edgeoptimize-request-id`, a conferma che la richiesta è stata indirizzata tramite il servizio Edge Optimize:

```
< HTTP/2 200
< x-edgeoptimize-request-id: 50fce12d-0519-4fc6-af78-d928785c1b85
```

**2. Test del traffico da persone (deve risultare NON interessato da modifiche)**

Simula una normale richiesta inserita da una persona nel browser:

```
curl -svo /dev/null https://www.example.com/page.html \
  --header "user-agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36"
```

La risposta **non** deve contenere l’intestazione `x-edgeoptimize-request-id`. Il contenuto della pagina e il tempo di risposta devono risultare identici rispetto a prima che sia stata abilitata la funzione Ottimizza su rete edge.

**3. Differenze tra i due scenari**

| Intestazione | Traffico da bot (ottimizzato) | Traffico da persone (non interessato da modifiche) |
|---|---|---|
| `x-edgeoptimize-request-id` | Presente: contiene un ID di richiesta univoco | Assente |
| `x-edgeoptimize-fo` | Presente solo in caso di failover (valore: `1`) | Assente |

{{verify-routing-status-in-ui}}

{{return-to-overview}}
