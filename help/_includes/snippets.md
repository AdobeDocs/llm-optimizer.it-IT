---
source-git-commit: b13f91d144d4899198891c4dcd841de8cfbb2355
workflow-type: tm+mt
source-wordcount: '157'
ht-degree: 0%

---
# Snippet

## Verifica dello stato di indirizzamento in LLM Optimizer {#verify-routing-status-in-ui}

Lo stato del routing del traffico può essere controllato anche nell’interfaccia utente di LLM Optimizer. Passa a **Configurazione cliente** e seleziona la scheda **Configurazione CDN**.

![Distribuzione delle ottimizzazioni agli agenti di IA - completata](/help/assets/optimize-at-edge/byocdn-CDN-traffic-routed-tick.png)

## Consentire l’ottimizzazione in Edge tramite le regole del firewall (facoltativo) {#waf-allowlist-setup}

Se la rete CDN utilizza un WAF o un Bot Manager:

* Inserire nell&#39;elenco Consentiti l&#39;agente utente `*AdobeEdgeOptimize/1.0*` nel WAF o nel gestore bot in modo che il servizio Optimize at Edge possa recuperare il contenuto di origine.
* Se il firewall richiede ulteriori verifiche oltre all&#39;agente utente, generare un segreto (ad esempio, `openssl rand -hex 32`) e:
   * Aggiungi `x-edgeoptimize-fetcher-key` con il segreto nelle regole di routing insieme alle altre intestazioni `x-edgeoptimize-*`.
   * Aggiungi una regola di WAF o Bot Manager per consentire le richieste in cui `x-edgeoptimize-fetcher-key` corrisponde allo stesso segreto.
* Ottimizza in Edge inoltra questa intestazione così com’è, sei il proprietario dell’intero ciclo di vita delle chiavi.

## Torna alla panoramica {#return-to-overview}

Per ulteriori informazioni su Ottimizza in Edge, tra cui le opportunità disponibili, i flussi di lavoro di ottimizzazione automatica e le domande frequenti, torna alla [Panoramica sull&#39;ottimizzazione in Edge](/help/dashboards/optimize-at-edge/overview.md).
