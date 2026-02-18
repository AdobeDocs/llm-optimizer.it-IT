---
title: Ottimizza in Edge - CDN gestita da AEM Cloud Service (Fastly)
description: Scopri come configurare AEM Cloud Service Managed CDN (Fastly) per l’ottimizzazione in Edge in LLM Optimizer.
feature: Opportunities
source-git-commit: 8cdd15413555057165f69ea4d5a15b243ab9098d
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 16%

---


# CDN gestito da AEM Cloud Service (Fastly)

Questa configurazione indirizza il traffico agente (richieste da bot di IA e agenti utente LLM) al servizio back-end Edge Optimize (`live.edgeoptimize.net`). I visitatori umani e i bot SEO continuano a essere serviti dalla tua origine come al solito. Per verificare la configurazione, al termine dell&#39;installazione, cercare l&#39;intestazione `x-edgeoptimize-request-id` nella risposta.

**Prerequisiti**

Per iniziare a instradare il traffico agente ad Edge Optimize:

1. Passa a **Configurazione cliente** e seleziona la scheda **Configurazione rete CDN**.

   ![Passa a Configurazione cliente](/help/assets/optimize-at-edge/prereq-customer-config-nav.png)

2. In **Routing traffico IA per distribuire ottimizzazioni**, selezionare la casella di controllo **Distribuisci ottimizzazioni agli agenti IA**. Il team Adobe gestirà la configurazione di indirizzamento per tuo conto.

   ![Distribuisci ottimizzazioni agli agenti di intelligenza artificiale](/help/assets/optimize-at-edge/prereq-deploy-checkbox.png)

3. Dopo aver attivato la casella di controllo, lo stato indica che la configurazione è in corso. Il team Adobe completerà la configurazione di indirizzamento.

   ![Configurazione del routing del traffico AI in corso](/help/assets/optimize-at-edge/prereq-traffic-routing-progress.png)

   Una volta configurato e attivato il routing, lo stato viene aggiornato in modo da mostrare un segno di spunta verde che indica che il routing è stato abilitato correttamente. Non sono richieste ulteriori azioni da parte tua.

Inoltre, se hai bisogno di assistenza per i passaggi precedenti, contatta il team del tuo account Adobe o `llmo-at-edge@adobe.com`.

**Routing self-service tramite pipeline Cloud Manager**

Se preferisci configurare autonomamente l’instradamento tramite la pipeline Cloud Manager, segui i passaggi seguenti. La configurazione dell’indirizzamento viene eseguita utilizzando una [regola CDN originSelector](https://experienceleague.adobe.com/it/docs/experience-manager-cloud-service/content/implementing/content-delivery/cdn-configuring-traffic#origin-selectors). I prerequisiti sono i seguenti:

* Decidi il dominio da instradare.
* Decidere i percorsi da instradare.
* Decidi gli agenti utente da instradare (regime consigliato).

Per distribuire la regola, devi:

* Crea una [pipeline di configurazione](https://experienceleague.adobe.com/it/docs/experience-manager-cloud-service/content/operations/config-pipeline).
* Eseguire il commit del file di configurazione `cdn.yaml` nel repository.
* Esegui la pipeline di configurazione.

```
kind: "CDN"
version: "1"
data:
  # Origin selectors to route to Edge Optimize backend
  originSelectors:
    rules:
      - name: route-to-edge-optimize-backend
        when:
          allOf:
            - reqHeader: x-edgeoptimize-request
              exists: false # avoid loops when requests comes from Edge Optimize
            - reqHeader: user-agent
              matches: "(?i)(AdobeEdgeOptimize-AI|ChatGPT-User|GPTBot|OAI-SearchBot|PerplexityBot|Perplexity-User)" # routed user agents
            - reqProperty: domain
              equals: "example.com" # routed domain
            - reqProperty: originalPath
              matches: '(/[^./]+|\.html|/)$' # routed extensions, with .html extension or without extension
            - anyOf:
              - { reqProperty: originalPath, in: [ "/page.html" ] } # routed pages, exact path matching
              - { reqProperty: originalPath, like: "/dir/*" } # routed pages, wildcard path matching
        action:
          type: selectOrigin
          originName: edge-optimize-backend
    origins:
      - name: edge-optimize-backend
        domain: "live.edgeoptimize.net"
```

{{verify-setup-adobe-aem-cs-cdn}}

{{return-to-overview}}
