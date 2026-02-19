---
title: Ottimizza in Edge - CDN gestita da AEM Cloud Service (Fastly)
description: Scopri come configurare AEM Cloud Service Managed CDN (Fastly) per l’ottimizzazione in Edge in LLM Optimizer.
feature: Opportunities
source-git-commit: 9230e525340bb951fcd9f2ae1f88bad557d5b7d7
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 12%

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

![Stato routing traffico IA con routing abilitato](/help/assets/optimize-at-edge/adobe-CDN-traffic-routed-tick.png)

{{return-to-overview}}
