---
title: Ottimizza in Edge - Fastly (BYOCDN)
description: Scopri come configurare Fastly BYOCDN per ottimizzare in Edge in LLM Optimizer.
feature: Opportunities
source-git-commit: 8cdd15413555057165f69ea4d5a15b243ab9098d
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 6%

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

{{verify-setup-byocdn}}

{{return-to-overview}}
