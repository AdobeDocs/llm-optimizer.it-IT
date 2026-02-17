---
title: Ottimizzazione nella rete Edge
description: Scopri come applicare le ottimizzazioni in LLM Optimizer direttamente a livello di CDN senza la necessità di apportare modifiche di authoring.
feature: Opportunities
source-git-commit: ae37ef578f279eae6ea51fd8aed5c6b91c8e1088
workflow-type: tm+mt
source-wordcount: '4843'
ht-degree: 45%

---


# Ottimizzazione nella rete Edge

Questa pagina fornisce una panoramica dettagliata su come applicare le ottimizzazioni a livello di CDN senza alcuna modifica all’authoring. Descrive il processo di onboarding, le opportunità di ottimizzazione disponibili e la procedura di ottimizzazione automatica nella rete Edge.

>[!NOTE]
>Questa funzionalità è attualmente in fase di accesso anticipato. Ulteriori informazioni su i programmi di accesso anticipato sono disponibili [qui](https://experienceleague.adobe.com/it/docs/experience-manager-cloud-service/content/release-notes/release-notes/release-notes-current#aem-beta-programs).

## Che cos’è l’ottimizzazione nella rete Edge?

L’ottimizzazione nella rete Edge è una funzionalità di implementazione basata su Edge in LLM Optimizer che fornisce modifiche AI descrittive agli agenti utente degli LLM. Nel contesto corrente, “Edge” indica che l’ottimizzazione viene applicata a livello della CDN. Poiché distribuisce le ottimizzazioni a livello della CDN, non sono necessarie modifiche di authoring nel Sistema di gestione dei contenuti (CMS), lasciando invariato il CMS di origine. Questa separazione ti consente di migliorare la visibilità degli LLM senza modificare i flussi di lavoro di pubblicazione esistenti. Si rivolge solo al traffico da IA agentica e non influisce né sugli utenti né sui bot SEO. Quando LLM Optimizer rileva opportunità per ottimizzare una pagina, gli utenti possono implementare correzioni direttamente a livello della CDN.

L’ottimizzazione nella rete Edge rappresenta un’alternativa più veloce e più snella alle correzioni tradizionali che richiedono attività tecniche complesse. Come accennato, una volta completata la configurazione una tantum, non dovrai apportare modifiche alle piattaforme né eseguire lunghi cicli di sviluppo per applicare i cambiamenti. Puoi pubblicare miglioramenti in pochi minuti senza richiedere il coinvolgimento degli sviluppatori. È una soluzione senza codice per ottimizzare il tuo sito web per gli agenti IA.

L’ottimizzazione nella rete Edge è progettata per gli utenti business nei team di marketing e responsabili della SEO, dei contenuti e delle strategie digitali. Consente agli utenti business di completare l’intero percorso in LLM Optimizer: identificando le opportunità, comprendendo i suggerimenti e implementando facilmente le correzioni. Con l’ottimizzazione nella rete Edge, gli utenti possono visualizzare in anteprima le modifiche, implentarle rapidamente a livello di CDN e verificare che le ottimizzazioni siano live. Le prestazioni possono essere tracciate nell’ecosistema di LLM Optimizer.

### Vantaggi principali

* **Distribuzione solo con IA:** fornisce HTML ottimizzato solo agli agenti IA, senza alcun impatto sui visitatori o sui bot SEO.
* **Cicli più veloci:** pubblica le modifiche in pochi minuti anziché settimane. Non sono necessarie modifiche alla piattaforma o lunghi cicli di progettazione.
* **Reversibile:** supportata da una funzionalità di rollback con un solo clic in grado di ripristinare la pagina in pochi minuti.
* **Nessun impatto sulle prestazioni:** le ottimizzazioni basate su Edge e la memorizzazione in cache non influiscono sulla latenza del sito.
* **Indipendente da CDN e CMS:** funziona con qualsiasi configurazione CDN e front-end indipendentemente dal sistema di gestione dei contenuti.

### Quali opportunità sono supportate con l’ottimizzazione nella rete Edge?

Con l’ottimizzazione nella rete Edge, sono supportate le opportunità che possono migliorare l’esperienza da IA agentica sul web. Ulteriori informazioni su ciascuna opportunità sono disponibili sia nella pagina della [Dashboard Opportunità](/help/dashboards/opportunities.md) che nella sezione Opportunità della pagina corrente.

## Onboarding

Per iniziare il processo di onboarding, contatta il team Adobe Account o il team FDE. Il tuo team IT o responsabile della CDN deve inoltre completare i prerequisiti e il processo di configurazione. Inoltre, puoi inviare un’e-mal all’indirizzo `llmo-at-edge@adobe.com` per ricevere ulteriore assistenza sull’onboarding.

Prerequisiti per l’onboarding per l’ottimizzazione nella rete Edge:

* Completamento del processo di onboarding in LLM Optimizer.
* Completamento del processo di inoltro dei registri per i registri della CDN.

Requisiti per il team IT/CDN:
* Aggiungi l&#39;agente utente `*AdobeEdgeOptimize/1.0*` al Inserisco nell&#39;elenco Consentiti di gestione del traffico da bot nel file robots.txt del sito o alle regole di gestione del traffico da bot.
* Assicurati che le pagine non siano bloccate a livello di dominio o CDN.
* Aggiungere le regole di indirizzamento per l’ottimizzazione della rete Edge nella CDN.
* Confermare l’indirizzamento dell’ottimizzazione della rete Edge nell’interfaccia di LLM Optimizer.

Per una guida al processo di configurazione, di seguito sono riportati alcuni esempi per diverse impostazioni della rete CDN. Tieni presente che questi esempi devono essere adattati alla tua configurazione live effettiva. È consigliabile applicare prima le modifiche negli ambienti inferiori.

>[!BEGINTABS]

>[!TAB CDN gestito da AEM Cloud Service (Fastly)]

**Ottimizzazione Edge - CDN gestita AEM Cloud Service (Fastly)**

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

Per testare la configurazione, esegui un comando cURL con il seguente risultato:

```
curl -svo /dev/null https://www.example.com/page.html --header "user-agent: chatgpt-user"
< HTTP/2 200
< x-edgeoptimize-request-id: 50fce12d-0519-4fc6-af78-d928785c1b85
```

Lo stato del routing del traffico può essere controllato anche nell’interfaccia utente di LLM Optimizer. Passa a **Configurazione cliente** e seleziona la scheda **Configurazione rete CDN**.

![Stato routing traffico IA con routing abilitato](/help/assets/optimize-at-edge/adobe-CDN-traffic-routed-tick.png)

>[!TAB Fastly (BYOCDN)]

**Ottimizzazione Edge - Fastly (BYOCDN)**

Questa configurazione indirizza il traffico agente (richieste da bot di IA e agenti utente LLM) al servizio back-end Edge Optimize (`live.edgeoptimize.net`). I visitatori umani e i bot SEO continuano a essere serviti dalla tua origine come al solito. Per verificare la configurazione, al termine dell&#39;installazione, cercare l&#39;intestazione `x-edgeoptimize-request-id` nella risposta.

**Prerequisiti**

Prima di impostare le regole VCL Fastly, assicurati di disporre di:

* Accesso a Fastly per il dominio.
* Processo di onboarding in LLM Optimizer completato.
* Inoltro del registro CDN a LLM Optimizer completato.
* Chiave API di ottimizzazione Edge recuperata dall’interfaccia utente di LLM Optimizer.

**Passaggi per recuperare la chiave API:**

1. Passa a **Configurazione cliente** e seleziona la scheda **Configurazione rete CDN**.

   ![Passa a Configurazione cliente](/help/assets/optimize-at-edge/prereq-customer-config-nav.png)

2. In **Routing traffico IA per distribuire ottimizzazioni**, selezionare la casella di controllo **Distribuisci ottimizzazioni agli agenti IA**.

   ![Distribuisci ottimizzazioni agli agenti di intelligenza artificiale](/help/assets/optimize-at-edge/prereq-deploy-checkbox.png)

3. Copia la chiave API e procedi con i passaggi di configurazione dell’indirizzamento riportati di seguito.

   ![Copia la chiave API](/help/assets/optimize-at-edge/prereq-copy-api-key.png)

   >[!NOTE]
   >A questo punto, lo stato potrebbe mostrare una croce rossa che indica che la configurazione non è ancora stata completata. Questo è previsto: una volta completata la configurazione di indirizzamento seguente e il traffico da bot AI inizia a fluire, lo stato si aggiorna a un segno di spunta verde che conferma che il routing è stato abilitato correttamente.

Inoltre, se hai bisogno di assistenza per i passaggi precedenti, contatta il team del tuo account Adobe o `llmo-at-edge@adobe.com`.

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

Per testare la configurazione, esegui un comando cURL con il seguente risultato:

```
curl -svo /dev/null https://www.example.com/page.html --header "user-agent: chatgpt-user"
< HTTP/2 200
< x-edgeoptimize-request-id: 50fce12d-0519-4fc6-af78-d928785c1b85
```

Lo stato del routing del traffico può essere controllato anche nell’interfaccia utente di LLM Optimizer. Passa a **Configurazione cliente** e seleziona la scheda **Configurazione rete CDN**.

![Stato routing traffico IA con routing abilitato](/help/assets/optimize-at-edge/byocdn-CDN-traffic-routed-tick.png)

>[!TAB Akamai (BYOCDN)]

**Ottimizzazione Edge - Akamai (BYOCDN)**

Questa configurazione indirizza il traffico agente (richieste da bot di IA e agenti utente LLM) al servizio back-end Edge Optimize (`live.edgeoptimize.net`). I visitatori umani e i bot SEO continuano a essere serviti dalla tua origine come al solito. Per verificare la configurazione, al termine dell&#39;installazione, cercare l&#39;intestazione `x-edgeoptimize-request-id` nella risposta.

**Prerequisiti**

Prima di impostare le regole di Gestione proprietà Akamai, assicurati di disporre dei seguenti elementi:

* Accesso ad Akamai Property Manager per il dominio.
* Processo di onboarding in LLM Optimizer completato.
* Inoltro del registro CDN a LLM Optimizer completato.
* Chiave API di ottimizzazione Edge recuperata dall’interfaccia utente di LLM Optimizer.

**Passaggi per recuperare la chiave API:**

1. Passa a **Configurazione cliente** e seleziona la scheda **Configurazione rete CDN**.

   ![Passa a Configurazione cliente](/help/assets/optimize-at-edge/prereq-customer-config-nav.png)

2. In **Routing traffico IA per distribuire ottimizzazioni**, selezionare la casella di controllo **Distribuisci ottimizzazioni agli agenti IA**.

   ![Distribuisci ottimizzazioni agli agenti di intelligenza artificiale](/help/assets/optimize-at-edge/prereq-deploy-checkbox.png)

3. Copia la chiave API e procedi con i passaggi di configurazione dell’indirizzamento riportati di seguito.

   ![Copia la chiave API](/help/assets/optimize-at-edge/prereq-copy-api-key.png)

   >[!NOTE]
   >A questo punto, lo stato potrebbe mostrare una croce rossa che indica che la configurazione non è ancora stata completata. Questo è previsto: una volta completata la configurazione di indirizzamento seguente e il traffico da bot AI inizia a fluire, lo stato si aggiorna a un segno di spunta verde che conferma che il routing è stato abilitato correttamente.

Inoltre, se hai bisogno di assistenza per i passaggi precedenti, contatta il team del tuo account Adobe o `llmo-at-edge@adobe.com`.

**Configurazione**

La regola di Akamai Property Manager seguente indirizza gli agenti utente LLM ad Edge Optimize. La configurazione include i seguenti passaggi:

**1. Imposta i criteri di indirizzamento (corrispondenza agente utente)**

Imposta il routing per i seguenti agenti utente:

```
 *AdobeEdgeOptimize-AI*,
 *ChatGPT-User*,
 *GPTBot*,
 *OAI-SearchBot*,
 *PerplexityBot*,
 *Perplexity-User*
```

![Imposta i criteri di indirizzamento](/help/assets/optimize-at-edge/akamai-step1-routing.png)

**2. Imposta il comportamento di origine e SSL**

Imposta origine come `live.edgeoptimize.net` e abbina SAN a `*.edgeoptimize.net`

![Imposta il comportamento di origine e SSL](/help/assets/optimize-at-edge/akamai-step2-origin.png)

**3. Imposta la variabile chiave della cache**

Imposta la variabile chiave della cache `PMUSER_EDGE_OPTIMIZE_CACHE_KEY` su `LLMCLIENT=TRUE;X_FORWARDED_HOST={{builtin.AK_HOST}}`

![Imposta la variabile chiave della cache](/help/assets/optimize-at-edge/akamai-step3-cachekey.png)

**4. Regole di memorizzazione in cache**

![Regole di memorizzazione in cache](/help/assets/optimize-at-edge/akamai-step4-rules.png)

**5. Modifica le intestazioni delle richieste in ingresso**

Imposta le seguenti intestazioni di richiesta in ingresso:
`x-edgeoptimize-api-key` alla chiave API recuperata da LLMO
Da `x-edgeoptimize-config` a `LLMCLIENT=TRUE;`
Da `x-edgeoptimize-url` a `{{builtin.AK_URL}}`

![Modifica le intestazioni delle richieste in ingresso](/help/assets/optimize-at-edge/akamai-step5-request.png)

**6. Modifica le intestazioni delle risposte in ingresso**

![Modifica le intestazioni delle risposte in ingresso](/help/assets/optimize-at-edge/akamai-step6-response.png)

**7. Modifica l’ID cache**

![Modifica l’ID cache](/help/assets/optimize-at-edge/akamai-step7-cacheid.png)

**8. Modifica intestazioni richieste in uscita**

Imposta intestazione `x-forwarded-host` su `{{builtin.AK_HOST}}`

![Modifica intestazioni richieste in uscita](/help/assets/optimize-at-edge/akamai-step8-outgoing-request.png)

**9. Failover del sito**

![Failover del sito](/help/assets/optimize-at-edge/akamai-step9-failover.png)

![Comportamenti di failover](/help/assets/optimize-at-edge/akamai-step9-failover-behaviors.png)

![Regole di failover](/help/assets/optimize-at-edge/akamai-step9-failover-rules.png)

Il failover del sito garantisce che se Edge Optimize restituisce un errore `4XX` o `5XX`, la richiesta venga automaticamente indirizzata all&#39;origine predefinita, in modo che l&#39;utente finale riceva comunque una risposta.

| Scenario | Comportamento |
| --- | --- |
| Edge Optimize restituisce `2XX` | Al client viene fornita una risposta ottimizzata. |
| Edge Optimize restituisce `4XX` o `5XX` | La richiesta viene indirizzata all’origine predefinita. |

**Verifica installazione**

Per testare la configurazione, esegui un comando cURL con il seguente risultato:

```
curl -svo /dev/null https://www.example.com/page.html --header "user-agent: chatgpt-user"
< HTTP/2 200
< x-edgeoptimize-request-id: 50fce12d-0519-4fc6-af78-d928785c1b85
```

Lo stato del routing del traffico può essere controllato anche nell’interfaccia utente di LLM Optimizer. Passa a **Configurazione cliente** e seleziona la scheda **Configurazione rete CDN**.

![Stato routing traffico IA con routing abilitato](/help/assets/optimize-at-edge/byocdn-CDN-traffic-routed-tick.png)

>[!TAB Cloudflare (BYOCDN)]

**Ottimizzazione Edge - Cloudflare (BYOCDN)**

Questa configurazione indirizza il traffico agente (richieste da bot di IA e agenti utente LLM) al servizio back-end Edge Optimize (`live.edgeoptimize.net`). I visitatori umani e i bot SEO continuano a essere serviti dalla tua origine come al solito. Per verificare la configurazione, al termine dell&#39;installazione, cercare l&#39;intestazione `x-edgeoptimize-request-id` nella risposta.

**Prerequisiti**

Prima di impostare le regole di instradamento di Cloud Worker, verificare di disporre dei seguenti elementi:

* Un account Cloudflare con processi di lavoro abilitati nel dominio.
* Accedere alle impostazioni DNS del dominio in Cloud Flare.
* Processo di onboarding in LLM Optimizer completato.
* Inoltro del registro CDN a LLM Optimizer completato.
* Chiave API di ottimizzazione Edge recuperata dall’interfaccia utente di LLM Optimizer.

**Passaggi per recuperare la chiave API:**

1. Passa a **Configurazione cliente** e seleziona la scheda **Configurazione rete CDN**.

   ![Passa a Configurazione cliente](/help/assets/optimize-at-edge/prereq-customer-config-nav.png)

2. In **Routing traffico IA per distribuire ottimizzazioni**, selezionare la casella di controllo **Distribuisci ottimizzazioni agli agenti IA**.

   ![Distribuisci ottimizzazioni agli agenti di intelligenza artificiale](/help/assets/optimize-at-edge/prereq-deploy-checkbox.png)

3. Copia la chiave API e procedi con i passaggi di configurazione dell’indirizzamento riportati di seguito.

   ![Copia la chiave API](/help/assets/optimize-at-edge/prereq-copy-api-key.png)

   >[!NOTE]
   >A questo punto, lo stato potrebbe mostrare una croce rossa che indica che la configurazione non è ancora stata completata. Questo è previsto: una volta completata la configurazione di indirizzamento seguente e il traffico da bot AI inizia a fluire, lo stato si aggiorna a un segno di spunta verde che conferma che il routing è stato abilitato correttamente.

Inoltre, se hai bisogno di assistenza per i passaggi precedenti, contatta il team del tuo account Adobe o `llmo-at-edge@adobe.com`.

**Funzionamento del routing**

Una volta configurata correttamente, una richiesta al tuo dominio (ad esempio, `www.example.com/page.html`) da un agente utente agente viene intercettata da Cloud Worker e indirizzata al backend Edge Optimize. La richiesta di back-end include le intestazioni richieste.

**Verifica della richiesta di back-end**

Puoi verificare il ciclo effettuando una richiesta diretta al backend di Edge Optimize.

```
curl -svo /dev/null https://live.edgeoptimize.net/page.html \
  -H 'x-forwarded-host: www.example.com' \
  -H 'x-edgeoptimize-url: /page.html' \
  -H 'x-edgeoptimize-api-key: $EDGE_OPTIMIZE_API_KEY' \
  -H 'x-edgeoptimize-config: LLMCLIENT=TRUE;'
```

**Intestazioni richieste**

Le seguenti intestazioni devono essere impostate sulle richieste al backend di Edge Optimize:

| Intestazione | Descrizione | Esempio |
|--------|-------------|---------|
| `x-forwarded-host` | Host originale della richiesta. Obbligatorio per identificare il dominio del sito. | `www.example.com` |
| `x-edgeoptimize-url` | Percorso URL originale e stringa di query della richiesta. | `/page.html` oppure `/products?id=123` |
| `x-edgeoptimize-api-key` | La chiave API fornita da Adobe per il dominio. | `your-api-key-here` |
| `x-edgeoptimize-config` | Stringa di configurazione per la differenziazione della chiave della cache. | `LLMCLIENT=TRUE;` |

**Passaggio 1: creare il processo di lavoro Cloudflare**

1. Accedi al dashboard di Cloudflare.
2. Passa a **Lavoratori e pagine** nella barra laterale.
3. Fare clic su **Crea applicazione** e quindi su **Crea lavoratore**.
4. Assegna un nome al lavoratore (ad esempio, `edge-optimize-router`).
5. Fare clic su **Distribuisci** per creare il processo di lavoro con il codice predefinito.

![Dashboard dei processi di lavoro Cloudflare](/help/assets/optimize-at-edge/cloudflare-workers-dashboard.png)

**Passaggio 2: aggiungere il codice Worker**

Dopo aver creato il processo di lavoro, fare clic su **Modifica codice** e sostituire il codice predefinito con il seguente:

```javascript
/**
 * Edge Optimize BYOCDN - Cloudflare Worker
 *
 * This worker routes requests from agentic bots (AI/LLM user agents) to the
 * Edge Optimize backend service for optimized content delivery.
 *
 * Features:
 * - Routes agentic bot traffic to Edge Optimize backend
 * - Failover to origin on Edge Optimize errors (any 4XX or 5XX errors)
 * - Loop protection to prevent infinite redirects
 * - Human visitors and SEO bots are served from the origin as usual
 */

// List of agentic bot user agents to route to Edge Optimize
const AGENTIC_BOTS = [
  'AdobeEdgeOptimize-AI',
  'ChatGPT-User',
  'GPTBot',
  'OAI-SearchBot',
  'PerplexityBot',
  'Perplexity-User'
];

// Targeted paths for Edge Optimize routing
// Set to null to route all HTML pages, or specify an array of paths
const TARGETED_PATHS = null; // e.g., ['/', '/page.html', '/products']

// Failover configuration
// Failover on any 4XX client error or 5XX server error from Edge Optimize
const FAILOVER_ON_4XX = true; // Failover on any 4XX error (400-499)
const FAILOVER_ON_5XX = true; // Failover on any 5XX error (500-599)

export default {
  async fetch(request, env, ctx) {
    return await handleRequest(request, env, ctx);
  },
};

async function handleRequest(request, env, ctx) {
  const url = new URL(request.url);
  const userAgent = request.headers.get("user-agent")?.toLowerCase() || "";

  // Check if request is already processed (loop protection)
  const isEdgeOptimizeRequest = !!request.headers.get("x-edgeoptimize-request");

  // Construct the original path and query string
  const pathAndQuery = `${url.pathname}${url.search}`;

  // Check if the path matches HTML pages (no extension or .html extension)
  const isHtmlPage = /(?:\/[^./]+|\.html|\/)$/.test(url.pathname);

  // Check if path is in targeted paths (if specified)
  const isTargetedPath = TARGETED_PATHS === null
    ? isHtmlPage
    : (isHtmlPage && TARGETED_PATHS.includes(url.pathname));

  // Check if user agent is an agentic bot
  const isAgenticBot = AGENTIC_BOTS.some((ua) => userAgent.includes(ua.toLowerCase()));

  // Route to Edge Optimize if:
  // 1. Request is NOT already from Edge Optimize (prevents infinite loops)
  // 2. User agent matches one of the agentic bots
  // 3. Path is targeted for optimization
  if (!isEdgeOptimizeRequest && isAgenticBot && isTargetedPath) {

    // Build the Edge Optimize request URL
    const edgeOptimizeURL = `https://live.edgeoptimize.net${pathAndQuery}`;

    // Clone and modify headers for the Edge Optimize request
    const edgeOptimizeHeaders = new Headers(request.headers);

    // Remove any existing Edge Optimize headers for security
    edgeOptimizeHeaders.delete("x-edgeoptimize-api-key");
    edgeOptimizeHeaders.delete("x-edgeoptimize-url");
    edgeOptimizeHeaders.delete("x-edgeoptimize-config");

    // x-forwarded-host: The original site domain
    // Use environment variable if set, otherwise use the request host
    edgeOptimizeHeaders.set("x-forwarded-host", env.EDGE_OPTIMIZE_TARGET_HOST ?? url.host);

    // x-edgeoptimize-api-key: Your Adobe-provided API key
    edgeOptimizeHeaders.set("x-edgeoptimize-api-key", env.EDGE_OPTIMIZE_API_KEY);

    // x-edgeoptimize-url: The original request URL path and query
    edgeOptimizeHeaders.set("x-edgeoptimize-url", pathAndQuery);

    // x-edgeoptimize-config: Configuration for cache key differentiation
    edgeOptimizeHeaders.set("x-edgeoptimize-config", "LLMCLIENT=TRUE;");

    try {
      // Send request to Edge Optimize backend
      const edgeOptimizeResponse = await fetch(new Request(edgeOptimizeURL, {
        headers: edgeOptimizeHeaders,
        redirect: "manual", // Preserve redirect responses from Edge Optimize
      }), {
        cf: {
          cacheEverything: true, // Enable caching based on origin's cache-control headers
        },
      });

      // Check if we need to failover to origin
      const status = edgeOptimizeResponse.status;
      const is4xxError = FAILOVER_ON_4XX && status >= 400 && status < 500;
      const is5xxError = FAILOVER_ON_5XX && status >= 500 && status < 600;

      if (is4xxError || is5xxError) {
        console.log(`Edge Optimize returned ${status}, failing over to origin`);
        return await failoverToOrigin(request, env, url);
      }

      // Return the Edge Optimize response
      return edgeOptimizeResponse;

    } catch (error) {
      // Network error or timeout - failover to origin
      console.log(`Edge Optimize request failed: ${error.message}, failing over to origin`);
      return await failoverToOrigin(request, env, url);
    }
  }

  // For all other requests (human users, SEO bots), pass through unchanged
  return fetch(request);
}

/**
 * Failover to origin server when Edge Optimize returns an error
 * @param {Request} request - The original request
 * @param {Object} env - Environment variables
 * @param {URL} url - Parsed URL object
 */
async function failoverToOrigin(request, env, url) {
  // Build origin URL
  const originURL = `${url.protocol}//${env.EDGE_OPTIMIZE_TARGET_HOST}${url.pathname}${url.search}`;

  // Prepare headers - clean Edge Optimize headers and add loop protection
  const originHeaders = new Headers(request.headers);
  originHeaders.set("Host", env.EDGE_OPTIMIZE_TARGET_HOST);
  originHeaders.delete("x-edgeoptimize-api-key");
  originHeaders.delete("x-edgeoptimize-url");
  originHeaders.delete("x-edgeoptimize-config");
  originHeaders.delete("x-forwarded-host");
  originHeaders.set("x-edgeoptimize-request", "fo");

  // Create and send origin request
  const originRequest = new Request(originURL, {
    method: request.method,
    headers: originHeaders,
    body: request.body,
    redirect: "manual",
  });

  const originResponse = await fetch(originRequest);

  // Add failover marker header to response
  const modifiedResponse = new Response(originResponse.body, {
    status: originResponse.status,
    statusText: originResponse.statusText,
    headers: originResponse.headers,
  });
  modifiedResponse.headers.set("x-edgeoptimize-fo", "1");
  return modifiedResponse;
}
```

Fai clic su **Salva e distribuisci** per pubblicare il processo di lavoro.

![Editor codice di lavoro Cloudflare](/help/assets/optimize-at-edge/cloudflare-worker-editor.png)

**Passaggio 3: configurare le variabili di ambiente**

Le variabili di ambiente memorizzano in modo sicuro la configurazione sensibile come la chiave API.

1. Nelle impostazioni del lavoratore, passa a **Impostazioni** > **Variabili**.
2. In **Variabili di ambiente**, fare clic su **Aggiungi variabile**.
3. Aggiungi le seguenti variabili:

   | Nome della variabile | Descrizione | Obbligatorio |
   |---------------|-------------|----------|
   | `EDGE_OPTIMIZE_API_KEY` | La chiave API Edge Optimize fornita da Adobe. | Sì |
   | `EDGE_OPTIMIZE_TARGET_HOST` | L&#39;host di destinazione per le richieste Edge Optimize (inviate come intestazione `x-forwarded-host`) e il dominio di origine per il failover. Deve essere solo il dominio senza protocollo (ad esempio, `www.example.com`, non `https://www.example.com`). | Sì |

4. Per la chiave API, fai clic su **Crittografa** per memorizzarla in modo sicuro.
5. Fare clic su **Salva e distribuisci**.

![Variabili di ambiente Cloudflare](/help/assets/optimize-at-edge/cloudflare-env-variables.png)

**Passaggio 4: aggiungi una route al dominio**

Per attivare il lavoratore nel dominio:

1. Vai a **Impostazioni** del tuo lavoratore > **Trigger**.
2. In **Routes**, fare clic su **Aggiungi route**.
3. Immettere il proprio modello di dominio, ad esempio `www.example.com/*` o `example.com/*`.
4. Seleziona la zona dal menu a discesa.
5. Fai clic su **Salva**.

In alternativa, è possibile configurare le route a livello di zona:

1. Passa al dominio in Cloud Flare.
2. Vai a **Route processi di lavoro**.
3. Fare clic su **Aggiungi route** e specificare il pattern e il worker.

![Route di lavoro Cloudflare](/help/assets/optimize-at-edge/cloudflare-worker-routes.png)

**Passaggio 5: verificare la configurazione**

Dopo la distribuzione, verifica la configurazione effettuando una richiesta con un agente utente agente.

```
curl -svo /dev/null https://www.example.com/page.html \
  --header "user-agent: chatgpt-user"
```

Una risposta corretta include l&#39;intestazione `x-edgeoptimize-request-id`:

```
< HTTP/2 200
< x-edgeoptimize-request-id: 50fce12d-0519-4fc6-af78-d928785c1b85
```

Lo stato del routing del traffico può essere controllato anche nell’interfaccia utente di LLM Optimizer. Passa a **Configurazione cliente** e seleziona la scheda **Configurazione rete CDN**.

![Stato routing traffico IA con routing abilitato](/help/assets/optimize-at-edge/byocdn-CDN-traffic-routed-tick.png)

Puoi anche verificare che il traffico normale continui a funzionare:

```
curl -svo /dev/null https://www.example.com/page.html \
  --header "user-agent: Mozilla/5.0"
```

Questa richiesta deve essere servita dalla tua origine senza l&#39;intestazione `x-edgeoptimize-request-id`.

**Verifica del comportamento di failover**

Se Edge Optimize non è disponibile o restituisce un errore, il processo di lavoro passa automaticamente all&#39;origine. Le risposte di failover includono l&#39;intestazione `x-edgeoptimize-fo`:

```
< HTTP/2 200
< x-edgeoptimize-fo: 1
```

È possibile monitorare gli eventi di failover nei registri di Cloud Workers per la risoluzione dei problemi.

**Informazioni sulla logica di lavoro**

Cloudflare Worker implementa la logica seguente:

1. **Rilevamento agente utente:** verifica se l&#39;agente utente della richiesta in ingresso corrisponde ai bot dell&#39;agente definiti (senza distinzione tra maiuscole e minuscole).

2. **Il targeting del percorso:** filtra facoltativamente le richieste in base ai percorsi di destinazione. Per impostazione predefinita, tutte le pagine HTML (URL che terminano con `/`, nessuna estensione o `.html`) sono instradate. È possibile specificare percorsi specifici utilizzando l&#39;array `TARGETED_PATHS`.

3. **Protezione loop:** L&#39;intestazione `x-edgeoptimize-request` impedisce cicli infiniti. Quando Edge Optimize invia nuovamente le richieste all&#39;origine, questa intestazione viene impostata su `"1"` e il processo di lavoro trasmette la richiesta senza inviarla nuovamente ad Edge Optimize.

4. **Sicurezza intestazione:** Prima di impostare le intestazioni Edge Optimize, il processo di lavoro rimuove le intestazioni esistenti `x-edgeoptimize-*` dalla richiesta in ingresso per evitare attacchi di inserimento di intestazioni.

5. **Mappatura intestazione:** Il processo di lavoro imposta le intestazioni richieste per Edge Optimize:
   * `x-forwarded-host` - Identifica il dominio del sito originale.
   * `x-edgeoptimize-url` - Mantiene il percorso della richiesta originale e la stringa di query.
   * `x-edgeoptimize-api-key` - Autentica la richiesta con Edge Optimize.
   * `x-edgeoptimize-config` - Fornisce la configurazione della chiave della cache.

6. **Logica di failover:** Se Edge Optimize restituisce un codice di stato di errore (errori del client 4XX o errori del server 5XX) o la richiesta non riesce a causa di un errore di rete, il processo di lavoro esegue automaticamente il failover all&#39;origine utilizzando `EDGE_OPTIMIZE_TARGET_HOST`. La risposta di failover include l&#39;intestazione `x-edgeoptimize-fo: 1` per indicare che si è verificato il failover.

7. **Gestione reindirizzamento:** L&#39;opzione `redirect: "manual"` garantisce che le risposte di reindirizzamento da Edge Optimize vengano passate al client senza che il processo di lavoro le segua.

**Personalizzazione della configurazione**

Puoi personalizzare il comportamento del lavoratore modificando le costanti di configurazione nella parte superiore del codice:

**Elenco bot agenti**

Modificare l&#39;array `AGENTIC_BOTS` per aggiungere o rimuovere agenti utente:

```javascript
const AGENTIC_BOTS = [
  'AdobeEdgeOptimize-AI',
  'ChatGPT-User',
  'GPTBot',
  'OAI-SearchBot',
  'PerplexityBot',
  'Perplexity-User',
  // Add additional user agents as needed
  'ClaudeBot',
  'Anthropic-AI'
];
```

**Percorsi di destinazione**

Per impostazione predefinita, tutte le pagine HTML vengono instradate ad Edge Optimize. Per limitare il routing a percorsi specifici, modificare l&#39;array `TARGETED_PATHS`:

```javascript
// Route all HTML pages (default)
const TARGETED_PATHS = null;

// Or specify exact paths to route
const TARGETED_PATHS = ['/', '/page.html', '/products', '/about-us'];
```

**Configurazione failover**

Per impostazione predefinita, il processo di lavoro esegue il failover in caso di errori 4XX o 5XX di Edge Optimize. Personalizza questo comportamento:

```javascript
// Default: failover on any 4XX or 5XX error
const FAILOVER_ON_4XX = true;
const FAILOVER_ON_5XX = true;

// Failover only on 5XX server errors (not 4XX client errors)
const FAILOVER_ON_4XX = false;
const FAILOVER_ON_5XX = true;

// Disable automatic failover (not recommended)
const FAILOVER_ON_4XX = false;
const FAILOVER_ON_5XX = false;
```

**Considerazioni importanti**

* **Comportamento di failover:** Se Edge Optimize restituisce un errore (codici di stato 4XX o 5XX) o se la richiesta non riesce a causa di un errore di rete, il processo di lavoro esegue automaticamente il failover nell&#39;origine. Il failover utilizza `EDGE_OPTIMIZE_TARGET_HOST` come dominio di origine (simile al `F_Default_Origin` di Fastly o al `Default_Origin` di CloudFront). Le risposte di failover includono l&#39;intestazione `x-edgeoptimize-fo: 1`, che è possibile utilizzare per il monitoraggio e il debug.

* **Memorizzazione in cache:** Cloudflare memorizza nella cache le risposte in base all&#39;URL per impostazione predefinita. Poiché il traffico agente riceve contenuti diversi dal traffico umano, assicurati che gli account di configurazione della cache siano corretti. Prendi in considerazione l’utilizzo delle intestazioni cache API o cache per distinguere i contenuti memorizzati in cache. L&#39;intestazione `x-edgeoptimize-config` deve essere inclusa nella chiave cache.

* **Limitazione di frequenza:** Monitora l&#39;utilizzo di Edge Optimize e, se necessario, valuta l&#39;implementazione di una limitazione di frequenza per il traffico agente.

* **Test:** Prima di distribuire la configurazione in produzione, verifica sempre la configurazione in un ambiente di staging. Verifica che il traffico sia agente che umano si comporti come previsto. Verificare il comportamento di failover simulando gli errori di Edge Optimize.

* **Registrazione:** abilita la registrazione di Cloudflare Workers per monitorare le richieste e risolvere i problemi. Passa a **Lavoratori** > **il tuo lavoratore** > **Registri** per visualizzare i registri in tempo reale. Il processo di lavoro registra gli eventi di failover a scopo di debug.

**Risoluzione dei problemi**

| Problema | Causa possibile | Soluzione |
|-------|----------------|----------|
| Nessuna intestazione `x-edgeoptimize-request-id` nella risposta | Route di lavoro non corrispondente o agente utente non presente nell&#39;elenco dei bot agente. | Verifica che il pattern di indirizzamento corrisponda all’URL della richiesta. Verificare che l&#39;agente utente si trovi nell&#39;array `AGENTIC_BOTS`. |
| Errori 401 o 403 da Edge Optimize | Chiave API non valida o mancante. | Verificare che `EDGE_OPTIMIZE_API_KEY` sia impostato correttamente nelle variabili di ambiente. Contatta Adobe per verificare che la chiave API sia attiva. |
| Reindirizzamenti o cicli infiniti | Intestazione di protezione del ciclo non impostata o controllata correttamente. | Verificare che il controllo dell&#39;intestazione `x-edgeoptimize-request` sia attivo. |
| Traffico umano interessato | Logica di routing dei lavoratori troppo ampia. | Verifica che la logica di corrispondenza dell’agente utente sia corretta e senza distinzione tra maiuscole e minuscole. Verificare che `TARGETED_PATHS` sia configurato correttamente. |
| Tempi di risposta lenti | Latenza di rete per il back-end Edge Optimize. | Ciò è previsto per la prima richiesta; le richieste successive vengono memorizzate nella cache in Edge Optimize. |
| Intestazione `x-edgeoptimize-fo: 1` in risposta | Edge Optimize ha restituito un errore e si è verificato il failover all’origine. | Controlla i registri di Cloud Workers per il codice di errore specifico. Verifica lo stato del servizio Edge Optimize con Adobe. |
| Failover non funzionante | Flag di failover disabilitati o errore nella logica di failover. | Verificare che `FAILOVER_ON_4XX` e `FAILOVER_ON_5XX` siano impostati su `true`. Verificare la presenza di messaggi di errore nei registri di lavoro. |
| Alcuni percorsi non vengono ottimizzati | Il percorso non corrisponde ai percorsi di destinazione o al pattern di pagina HTML. | Verificare che il percorso sia in `TARGETED_PATHS` (se specificato) e che corrisponda al pattern regex della pagina HTML. |
| Richieste non riuscite con host non valido | `EDGE_OPTIMIZE_TARGET_HOST` include il protocollo, ad esempio `https://`. | Utilizzare solo il nome di dominio senza protocollo, ad esempio `example.com` e non `https://example.com`. |
| Errore 530 durante il failover | Cloudflare non è in grado di connettersi all&#39;origine oppure la richiesta di failover contiene intestazioni non valide. | Assicurati che la funzione di failover rimuova le intestazioni Edge Optimize. Verificare che l&#39;origine sia accessibile e che il DNS sia configurato correttamente. |

>[!ENDTABS]

>[!NOTE]
>Per gli altri provider CDN, contatta `llmo-at-edge@adobe.com` per assistere i team IT/CDN durante l’onboarding. Una volta completate le configurazioni, puoi implementare i suggerimenti per le opportunità di ottimizzazione nella rete Edge in LLM Optimizer.

## Opportunità

Nella tabella seguente sono presentate le opportunità che possono migliorare l’esperienza web agentica e che sono supportate dall’ottimizzazione nella rete Edge.

| Opportunità | Tipo | Identificazione automatica | Suggerimento automatico | Ottimizzazione automatica |
|---------|----------|----------|----------|----------|
| Recupera visibilità dei contenuti | GEO tecnica | Rileva le pagine in cui i contenuti critici sono nascosti dagli agenti IA. Mostra gli URL interessati e i contenuti previsti che possono essere recuperati. | Evidenzia i contenuti che possono essere resi disponibili per gli agenti IA e consiglia di abilitare il pre-rendering per le pagine. | Fornisce al traffico da IA agentica un’istantanea HTML completamente sottoposta a rendering e ottimizzata per l’IA che recupera i contenuti precedentemente nascosti. |
| Ottimizza titoli per gli LLM | Ottimizzazione dei contenuti | Esegue la scansione per rilevare titoli vuoti, duplicati, mancanti o ambigue che possono ridurre la leggibilità automatica. | Propone una gerarchia di intestazioni più pulita ed etichette migliorate oltre a mostrare un’anteprima della struttura aggiornata per ciascuna pagina. | Inserisce la struttura dell’intestazione migliorata per gli agenti IA, preservando la progettazione visiva e rendendo al contempo la pagina più leggibile per gli LLM. |
| Aggiungi riepiloghi ottimizzati per gli LLM | Ottimizzazione dei contenuti | Identifica pagine lunghe o complesse prive di riepiloghi concisi a livello di pagina o di sezione che risultano più difficili da scansionare e comprendere rapidamente per l’IA. | Consiglia brevi riepiloghi generati dall’IA a livello di pagina e di sezione, per l’acquisizione di contenuti chiave. | Inserisce i riepiloghi nelle sezioni HTML pertinenti, migliorando il modo in cui i modelli interpretano e descrivono i contenuti della pagina. |
| Aggiungi domande frequenti pertinenti | Ottimizzazione dei contenuti | Rileva le lacune nell’intento dei contenuti della pagina esistente che potrebbero trarre vantaggio dalle domande frequenti. | Suggerisce contenuti per le domande frequenti generati dall’IA in linea con l’intento utente e gli argomenti esistenti. | Inserisce i contenuti delle domande frequenti nell’HTML, rendendo le pagine più individuabili e pertinenti nelle risposte basate sull’IA. |
| Semplifica contenuti complessi | Ottimizzazione dei contenuti | Contrassegna le pagine con testi complessi che possono ostacolare la comprensione da parte dell’IA. | Fornisce versioni semplificate generate dall’IA di testi complessi mantenendone il significato originale. | Riscrive sezioni complesse della pagina, migliorando la leggibilità per l’IA. |

### Strumenti aggiuntivi

[Adobe LLM Optimizer: la tua pagina Web è citabile?](https://chromewebstore.google.com/detail/adobe-llm-optimizer-is-yo/jbjngahjjdgonbeinjlepfamjdmdcbcc) L’estensione Chrome mostra la quantità di contenuti della tua pagina web a cui gli LLM possono accedere e ciò che invece rimane nascosto. Progettata come strumento diagnostico indipendente e gratuito, non richiede alcuna licenza né configurazione del prodotto.

Con un solo clic, puoi valutare la leggibilità automatica di qualsiasi sito. Puoi visualizzare un confronto affiancato tra ciò che vedono gli agenti IA rispetto a ciò che vedono gli utenti, e stimare quanto contenuto potrebbe essere recuperato utilizzando LLM Optimizer. Consulta la pagina [L’IA può leggere il tuo sito web?](https://business.adobe.com/blog/introducing-the-llm-optimizer-chrome-extension) per ulteriori informazioni.

## Opportunità dettagliate

Nelle sezioni seguenti, puoi visualizzare ulteriori dettagli per ogni opportunità supportata dalla funzione Ottimizzazione nella rete Edge.

### Recupera visibilità dei contenuti

Questa opportunità segnala le pagine in cui il contenuto chiave risulta nascosto per gli agenti IA a causa del rendering lato client. Per ogni pagina identificata, vengono mostrati mostri esattamente i contenuti che l’agente IA non può “vedere”, evidenzia le lacune di visibilità e consente di applicare direttamente le modifiche necessarie per recuperare i contenuti nascosti. Quando implementi questa opportunità con Ottimizzazione nella rete Edge, agli agenti utente LLM viene presentata una versione della pagina pre-renderizzata e ottimizzata per l’IA, affinché possano accedere all’intero contesto senza eseguire alcun codice Javascript.
In questo modo la pagina sarà completamente visibile agli agenti IA. Ulteriori miglioramenti vengono poi applicati all’HTML pre-renderizzato.

>[!IMPORTANT]
>Questa funzionalità di pre-rendering si applica in automatico a tutte le opportunità presentate di seguito quando vengono implementate con la funzione Ottimizzazione nella rete Edge, affinché la pagina sia completamente visibile agli agenti IA.

### Ottimizza titoli per gli LLM

Questa opportunità rileva le pagine in cui la struttura dei titoli ostacola la comprensione della pagina da parte degli agenti IA, a causa di titoli vuoti, duplicati, mancanti o ambigui. Per ogni pagina interessata, l’opportunità rileva i titoli non ottimali e consiglia una gerarchia più chiara. Quando vengono implementati con Ottimizzazione nella rete Edge, i titoli migliorati vengono applicati nell’HTML che viene presentato al traffico da IA agentica. In questo modo puoi migliorare la leggibilità automatica lasciando invariato il layout rivolto agli utenti veri e propri.

### Aggiungi riepiloghi ottimizzati per gli LLM

Questa opportunità identifica le pagine che possono trarre vantaggio da riepiloghi concisi per aiutare gli LLM a comprendere rapidamente il contenuto della pagina. Per ogni pagina, l’opportunità rileva dove è più necessario un riepilogo e crea riepiloghi generati dall’IA a livello di pagina o di sezione. Quando vengono implementati con Ottimizzazione nella rete Edge, questi riepiloghi vengono inseriti nell’HTML recuperato dagli agenti IA, in modo da migliorare le probabilità di una descrizione più accurata del tuo contenuto.

### Aggiungi domande frequenti pertinenti

Questa opportunità segnala le pagine in cui contenuti aggiuntivi composti da domande e risposte potrebbero rispondere meglio all’intento degli utenti e ai prompt utilizzati nella ricerca basata sull’IA. Per ogni pagina, propone blocchi di domande frequenti generati dall’IA associati all’intento degli utenti e al contenuto della pagina. Con Ottimizzazione nella rete Edge, le domande frequenti vengono inserite nell’HTML, in modo da rendere la pagina maggiormente compatibile con l’IA e aumentare la probabilità che le risposte fornite dall’IA siano in linea con le tue indicazioni.

### Semplifica contenuti complessi

Questa opportunità trova le pagine con paragrafi lunghi e complessi che potrebbero non essere compresi correttamente dall’IA. Per ogni pagina che supera le soglie di leggibilità, vengono creati contenuti generati dall’IA più semplici e facili da analizzare, mantenendo il significato originale. Quando viene implementata sulla rete Edge, il contenuto semplificato viene presentato al traffico da IA agentica e consente agli LLM di interpretare e riepilogare i contenuti in modo più fedele.

## Ottimizzazione automatica sulla rete Edge

Per ogni opportunità, puoi visualizzare in anteprima e live, modificare e implementare, le ottimizzazioni sulla rete Edge, nonché ripristinare la versione precedente.

>[!VIDEO](https://video.tv.adobe.com/v/3477983/?learn=on&enablevpops)

### Anteprima

**Anteprima** consente di visualizzare l’impatto di un suggerimento prima che venga pubblicato. Presenta in modalità affiancata le differenze tra la pagina corrente e la versione risultante dall’ottimizzazione IA, una volta applicato il suggerimento. Questa vista si basa sulla stessa logica utilizzata da Ottimizzazione sulla rete Edge per il traffico live, ma applicata in modalità di anteprima isolata. Non influisce sul traffico live, in quanto si tratta di una simulazione di sola lettura a scopo di revisione.

![Anteprima](/help/assets/optimize-at-edge/preview.png)

### Modifica

**Modifica** consente di perfezionare o riscrivere completamente il suggerimento generato in automatico prima di implementarlo. Invece di accettare il suggerimento, puoi mantenere il controllo completo tramite il flusso di lavoro di modifica. Questa vista mostra le modifiche proposte in un editor strutturato, dove puoi modificare il testo per soddisfare meglio l’intento originale. Una volta implementata, la versione modificata verrà quindi trasmessa agli agenti IA.

![Modifica](/help/assets/optimize-at-edge/edit.png)

### Implementa

**Implementa** pubblica i suggerimenti selezionati in modo che le esperienze ottimizzate possano essere trasmesse dalla rete Edge agli agenti IA. Se la CDN è completamente indirizzata, in genere tutte le pagine del dominio vengono pubblicate con le nuove modifiche in pochi minuti. Se l’indirizzamento è stato configurato solo per alcuni percorsi, solo le pagine inserite nell’elenco consentiti vengono pubblicate con le ottimizzazioni.

![Implementazione](/help/assets/optimize-at-edge/deploy.png)

### Visualizza live

**Visualizza live** ti consente di verificare che l’ottimizzazione sia live e funzioni come previsto per il traffico da IA agentica, offrendo una visualizzazione a cui altrimenti sarebbe difficile accedere. Puoi visualizzare la pagina live in Suggerimenti risolti, che esegue il rendering della pagina come mostrato agli agenti IA.

![Visualizza live](/help/assets/optimize-at-edge/view-live.png)

### Rollback

Il rollback ripristina in modo sicuro un’ottimizzazione implementata in precedenza. In genere, la versione della pagina solo per l’IA viene ripristinata allo stato precedente in pochi minuti, rendendo sicuro testare diverse ottimizzazioni in caso di necessità.

![Rollback](/help/assets/optimize-at-edge/rollback.png)

## Domande frequenti

D. Per quali tipi di LLM viene eseguito il targeting con l’ottimizzazione nella rete Edge?

Puoi definire l’elenco degli agenti utente di cui eseguire il targeting durante il processo di onboarding.

<!--Q. What does "Edge" in Optimize at Edge mean?

In our context, "Edge" means that the optimization is applied at the CDN layer and not inside your CMS.

Q. Why does this optimization require a CDN?

The CDN is where the optimized version of the page is assembled and delivered to AI agents. We leverage the CDN to ensure your origin CMS remains unchanged. This separation lets you improve LLM visibility without altering your existing publishing workflows.-->

D. Cosa succede se non ho ancora effettuato l’onboarding per l’otttimizzazione nella rete Edge?

Se fai clic su **Implementa ottimizzazioni** prima aver completato la configurazione richiesta, non verrà applicata alcuna modifica al tuo sito. Viene invece visualizzata una finestra di dialogo a comparsa in cui ti verrà richiesto di contattare il nostro team all’indirizzo `llmo-at-edge@adobe.com` per ricevere assistenza sull’onboarding. Fino a quando l’onboarding non è completato, puoi ancora esplorare le opportunità e i suggerimenti rilevati, ma il flusso di lavoro di implementazione con un solo clic rimarrà inattivo.

D. Cosa succede quando i contenuti vengono aggiornati all’origine?

Distribuiamo la versione ottimizzata della pagina dalla cache, purché la pagina sorgente sottostante non sia cambiata. Tuttavia, quando l&#39;origine cambia per **Recupera Visibilità dei contenuti**, il sistema si aggiorna automaticamente in modo che gli agenti di IA ricevano sempre il contenuto più aggiornato. Questo perché utilizziamo impostazioni TTL (time-to-live) della cache ridotte (in ordine di minuti) in modo che qualsiasi aggiornamento del contenuto sul sito attivi una nuova ottimizzazione all’interno di tale finestra. Per opportunità di contenuto come **Aggiungi riepiloghi compatibili con LLM**, LLM Optimizer controlla la pagina di origine per eventuali modifiche. Se viene rilevata una modifica, l’ottimizzazione viene sospesa e contrassegnata per la revisione umana per evitare la deviazione del contenuto tra la pagina visibile dall’agente e la pagina visibile dall’uomo.
<!--As there is no universal TTL that fits every site, we can configure this TTL based on your cache invalidation rules to ensure both systems stay in sync.-->

D. L’ottimizzazione nella rete Edge è valida solo per i siti che utilizzano il servizio Adobe Edge Delivery (EDS)?

No. L’ottimizzazione nella rete Edge è indipendente dalla CDN e funziona con qualsiasi architettura front-end, non solo quelle implementate sullo Stack EDS di Adobe.

D. In che modo il pre-rendering dell’ottimizzazione nella rete Edge è diverso dal rendering lato server tradizionale (SSR)?

Entrambi risolvono problemi diversi e possono essere utilizzati insieme. Il rendering SSR tradizionale esegue il rendering dei contenuti lato server, ma non include i contenuti caricati successivamente nel browser. Il pre-rendering dell’ottimizzazione nella rete Edge acquisisce la pagina dopo il caricamento di JavaScript e dei dati lato client, generando la versione completamente assemblata sul lato della CDN. Il rendering SSR si concentra sul miglioramento dell’esperienza utente, mentre l’ottimizzazione nella rete Edge migliora l’esperienza web per gli LLM.

D. Cosa succede se distribuisco ottimizzazioni per alcuni URL nel mio dominio ma non per tutti?

Vengono modificati solo gli URL esplicitamente ottimizzati. Per gli URL con opportunità distribuite, gli agenti di IA ricevono la versione ottimizzata. Per gli URL senza opportunità distribuite, il nostro servizio effettua semplicemente il proxy della pagina originale così com’è, senza applicare modifiche o memorizzarla nel livello della cache di ottimizzazione. In questo modo puoi distribuire selettivamente le ottimizzazioni senza influire sul resto del sito.
