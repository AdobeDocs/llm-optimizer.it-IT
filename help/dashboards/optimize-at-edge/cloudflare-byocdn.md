---
title: Ottimizzazione nella rete edge - Cloudflare (BYOCDN)
description: Scopri come configurare Cloudflare BYOCDN per l’ottimizzazione nella rete edge in LLM Optimizer.
feature: Opportunities
autotag-review: '2026-05-15T17:40:49.847Z'
TQID: 'https://experienceleague.adobe.com/HkaDwdHRGZJnip-1Bp-4Z-ovwcBPxFUSDqeLUVNu0zo'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: d1956731-2adb-4bb7-8301-2b239254ac72
subfeature_v2: id: d23587d6-14d6-4e3f-9ee1-cc18623832e1
source-git-commit: c5a8f033aac85913b56a40bb1560537da04847f2
workflow-type: tm+mt
source-wordcount: 1916
ht-degree: 96%

---


# Cloudflare (BYOCDN)

Questa configurazione indirizza il traffico da IA agentica (richieste da bot IA e da agenti utente LLM) al servizio back-end Edge Optimize (`live.edgeoptimize.net`). Le persone e i bot SEO continuano a ricevere come al solito i contenuti trasmessi dalla tua origine. Per testare la configurazione, al termine cerca nella risposta l’intestazione `x-edgeoptimize-request-id`.

**Prerequisiti**

Prima di impostare le regole di instradamento di Cloud Worker, verificare di disporre dei seguenti elementi:

* disporre di un account Cloudflare con processi di lavoro abilitati nel tuo dominio.
* avere acceso alle impostazioni DNS del tuo dominio in Cloudflare.
* aver recuperato dall’interfaccia di LLM Optimizer una chiave API del servizio Edge Optimize. Per la procedura, consulta [Recuperare le chiavi API](/help/dashboards/optimize-at-edge/retrieve-api-keys.md#production-api-key).
* (Facoltativo) Per verificare l’indirizzamento in fase di staging, consulta [Chiave API di staging](/help/dashboards/optimize-at-edge/retrieve-api-keys.md#staging-api-key-optional).

**Come funziona l’indirizzamento**

Una volta configurata correttamente, una richiesta al tuo dominio (ad esempio, `www.example.com/page.html`) proveniente da un agente utente agentico viene intercettata dal processo di lavoro Cloudflare e indirizzata al back-end del servizio Edge Optimize. La richiesta al back-end include le intestazioni necessarie.

**Test della richiesta al back-end**

Puoi verificare l’indirizzamento effettuando una richiesta diretta al back-end del servizio Edge Optimize.

```
curl -svo /dev/null https://live.edgeoptimize.net/page.html \
  -H 'x-forwarded-host: www.example.com' \
  -H 'x-edgeoptimize-url: /page.html' \
  -H 'x-edgeoptimize-api-key: $EDGE_OPTIMIZE_API_KEY' \
  -H 'x-edgeoptimize-config: LLMCLIENT=TRUE;'
```

**Intestazioni necessarie**

Le seguenti intestazioni devono essere impostate sulle richieste al back-end del servizio Edge Optimize:

| Intestazione | Descrizione | Esempio |
|--------|-------------|---------|
| `x-forwarded-host` | Host originale della richiesta. Necessario per identificare il dominio del sito. | `www.example.com` |
| `x-edgeoptimize-url` | Percorso URL originale e stringa di query della richiesta. | `/page.html` oppure `/products?id=123` |
| `x-edgeoptimize-api-key` | Chiave API fornita da Adobe per il tuo dominio. | `your-api-key-here` |
| `x-edgeoptimize-config` | Stringa di configurazione per la differenziazione delle chiavi nella cache. | `LLMCLIENT=TRUE;` |

## Opzioni di configurazione

Sono disponibili due modi per configurare Cloudflare Worker per l’Ottimizzazione sulla rete Edge:

* [**Opzione 1: implementazione in Cloudflare (scelta consigliata)**](#option-1-deploy-to-cloudflare): crea automaticamente un nuovo processo di lavoro e richiede di specificare le variabili di ambiente e i segreti richiesti. Utilizza questa opzione se per questo dominio non disponi di un processo di lavoro Cloudflare esistente.
* [**Opzione 2: configurazione manuale**](#option-2-manual-setup): istruzioni dettagliate per la creazione e la configurazione del processo di lavoro. Utilizza questa opzione se nel dominio è già configurato un Cloudflare Worker. Sarà necessario unire il codice di Ottimizzazione sulla rete Edge nel processo di lavoro esistente (consulta [Passaggio 2: aggiungere il codice del processo di lavoro](#option-2-manual-setup)) oppure se si preferisce il controllo completo sulla distribuzione.

Indipendentemente dall’opzione scelta, è necessario collegare manualmente il processo di lavoro al dominio. Consulta [Passaggio: aggiungere un indirizzamento al dominio](#add-a-route-to-your-domain).

## Opzione 1: implementazione in Cloudflare

Questa opzione utilizza il pulsante **Implementazione in Cloudflare** per creare automaticamente il processo di lavoro e configurare le variabili di ambiente e i segreti richiesti nell’account Cloudflare. Questo è il modo più rapido per iniziare se si sta configurando un nuovo processo di lavoro.

>[!IMPORTANT]
>
>Utilizza questa opzione solo se **non** disponi di un Cloudflare Worker esistente nel dominio. Se disponi già di un processo di lavoro, utilizza [Opzione 2: configurazione manuale](#option-2-manual-setup) per aggiungere la logica di indirizzamento dell’Ottimizzazione sulla rete Edge al processo di lavoro esistente.

**Passaggio 1: implementare il processo di lavoro**

Fai clic sul pulsante seguente per implementare il processo di lavoro dell’Ottimizzazione sulla rete Edge nell’account Cloudflare:

[![Implementazione in Cloudflare](https://deploy.workers.cloudflare.com/button)](https://deploy.workers.cloudflare.com/?url=https://github.com/adobe/llmo-code-samples/tree/main/optimize-at-edge/cloudflare/automation)

**Passaggio 2: compilare il modulo di implementazione**

Facendo clic sul pulsante, si apre la pagina di configurazione dei processi di lavoro. Compila il modulo come segue:

![Pagina di configurazione di Cloudflare Workers](/help/assets/optimize-at-edge/cloudflare-deploy-form.png)

1. **Account Git** - Seleziona l’account GitHub o GitLab dal menu a discesa. Cloudflare effettua il fork del codice del processo di lavoro in un archivio nel tuo account. Se nessun account è elencato, puoi aggiungere una nuova connessione direttamente dal menu a discesa selezionando **+ Nuova connessione GitHub** o **+ Nuova connessione GitLab**. Per ulteriori informazioni, consulta [Guida all’integrazione di Cloudflare con Git](https://developers.cloudflare.com/workers/ci-cd/builds/git-integration/github-integration/).

   ![Menu a discesa dell’account Git che mostra le opzioni Nuova connessione GitHub e Nuova connessione GitLab](/help/assets/optimize-at-edge/cloudflare-git-connection.png)
2. **Creare archivio Git privato** - Lascia questa opzione selezionata (impostazione predefinita).
3. **Nome del progetto** - Lascia `edge-optimize-router` o inserisci un nome a tua scelta.
4. **EDGE_OPTIMIZE_API_KEY** - Incolla la chiave API del servizio di Ottimizzazione sulla rete Edge fornita da Adobe. Questo valore viene memorizzato come segreto crittografato.
5. **EDGE_OPTIMIZE_TARGET_HOST** - Inserisci il dominio del tuo sito senza il protocollo (ad esempio,`www.example.com`).
6. **Comando di compilazione** - Lascia vuoto questo campo.
7. **Comando di implementazione** - Lascia `npm run deploy` (precompilato).
8. **Compila per rami non di produzione** - Non selezionare questo campo. Questa è una funzionalità del flusso di lavoro degli sviluppatori e non è necessaria per questa implementazione.
9. Fai clic su **Crea e implementa**.

Dopo aver implementato il processo di lavoro, procedi con [Aggiungere un indirizzamento al dominio](#add-a-route-to-your-domain) per collegare il processo di lavoro al dominio. L’indirizzamento non viene configurato automaticamente e deve essere completato manualmente.

## Opzione 2: configurazione manuale

Segui questi passaggi per creare e configurare manualmente il processo di lavoro.

**Passaggio 1: creare il processo di lavoro Cloudflare**

1. Accedi alla dashboard di Cloudflare.
2. Passa a **Workers &amp; Pages** (Processi di lavoro e pagine) nella barra laterale.
3. Fai clic su **Create application** (Crea applicazione), quindi su **Create Worker** (Crea processo di lavoro).
4. Assegna un nome al processo di lavoro, ad esempio `edge-optimize-router`.
5. Fai clic su **Deploy** (Implementa) per creare il processo di lavoro con il codice predefinito.

![Dashboard dei processi di lavoro Cloudflare](/help/assets/optimize-at-edge/cloudflare-workers-dashboard.png)

**Passaggio 2: aggiungere il codice del processo di lavoro**

Dopo aver creato il processo di lavoro, fare clic su **Modifica codice** e sostituire il codice predefinito con il codice di [worker.js](https://github.com/adobe-rnd/llmo-edge-optimize-samples/blob/main/cloudflare/worker.js). Se disponi già di Cloud Worker, unisci il codice con il codice del processo di lavoro esistente invece di sostituirlo completamente.

Fai clic su **Save and deploy** (Salva e implementa) per pubblicare il processo di lavoro.

**Passaggio 3: configurare i segreti e le variabili di ambiente**

Le variabili di ambiente memorizzano in modo sicuro le configurazioni sensibili, come la chiave API.

1. Nelle impostazioni del processo di lavoro, passa a **Settings** > **Variables** (Impostazioni > Variabili).
2. In **Environment Variables** (Variabili ambiente), fai clic su **Add variable** (Aggiungi variabile).
3. Aggiungi le seguenti variabili:

   | Nome della variabile | Descrizione | Obbligatorio |
   |---------------|-------------|----------|
   | `EDGE_OPTIMIZE_API_KEY` | Chiave API del servizio Edge Optimize fornita da Adobe. | Sì |
   | `EDGE_OPTIMIZE_TARGET_HOST` | Host target per le richieste al servizio Edge Optimize (inviate come intestazione `x-forwarded-host`) e il dominio di origine per il failover. Deve essere solo il dominio, senza protocollo (ad esempio: `www.example.com`, e non `https://www.example.com`). | Sì |

4. Per la chiave API, fai clic su **Encrypt** (Crittografa) per memorizzarla in modo sicuro.
5. Fai clic su **Save and deploy** (Salva e implementa).

![Variabili di ambiente Cloudflare](/help/assets/optimize-at-edge/cloudflare-env-variables.png)

## Aggiungere un indirizzamento al dominio {#add-a-route-to-your-domain}

Indipendentemente dall’opzione di configurazione utilizzata, devi collegare manualmente il processo di lavoro al tuo dominio. Questo passaggio attiva il processo di lavoro sul tuo traffico.

1. Per il tuo processo di lavoro, passa a **Settings** > **Triggers** (Impostazioni > Trigger).
2. In **Routes** (Indirizzamenti), fai clic su **Add route** (Aggiungi indirizzamento).
3. Inserisci il pattern del tuo dominio, ad esempio `www.example.com/*` o `example.com/*`.
4. Seleziona la zona dal menu a discesa.
5. Fai clic su **Salva**.

In alternativa, puoi configurare gli indirizzamenti a livello di zona:

1. Passa al tuo dominio in Cloudflare.
2. Passa a **Workers Routes** (Indirizzamenti dei processi di lavoro).
3. Fai clic su **Add route** (Aggiungi indirizzamento) e specifica il pattern e il processo di lavoro.

![Indirizzamenti del processo di lavoro Cloudflare](/help/assets/optimize-at-edge/cloudflare-worker-routes.png)

**Verifica del comportamento di failover**

Se il servizio Edge Optimize non è disponibile o restituisce un errore, il processo di lavoro esegue automaticamente il failover sulla tua origine. Le risposte di failover includono l’intestazione `x-edgeoptimize-fo`:

```
< HTTP/2 200
< x-edgeoptimize-fo: 1
```

Per la risoluzione di eventuali problemi, puoi monitorare gli eventi di failover nei registri dei processi di lavoro di Cloudflare.

**Logica del processo di lavoro**

Il processo di lavoro Cloudflare implementa la logica seguente:

1. **Rilevamento dell’agente utente:** verifica se l’agente utente della richiesta in ingresso corrisponde a uno dei bot agentici definiti, senza distinzione maiuscole/minuscole.

2. **Targeting del percorso:** facoltativamente, filtra le richieste in base ai percorsi di destinazione. Per impostazione predefinita, vengono indirizzate tutte le pagine HTML (URL che terminano con `/`, nessuna estensione o `.html`). Per percorsi specifici, puoi utilizzare l’array `TARGETED_PATHS`.

3. **Protezione da cicli infiniti:** l’intestazione `x-edgeoptimize-request` impedisce cicli infiniti. Quando il servizio Edge Optimize invia richieste alla tua origine, questa intestazione viene impostata su `"1"` e il processo di lavoro trasmette la richiesta senza indirizzarla nuovamente al servizio Edge Optimize.

4. **Sicurezza delle intestazioni:** prima di impostare le intestazioni del servizio Edge Optimize, il processo di lavoro rimuove le intestazioni `x-edgeoptimize-*` esistenti dalla richiesta in ingresso per evitare attacchi di inserimento di intestazioni.

5. **Mappatura delle intestazione:** il processo di lavoro imposta le intestazioni necessarie per Edge Optimize:
   * `x-forwarded-host` - Identifica il dominio del sito originale.
   * `x-edgeoptimize-url` - Mantiene il percorso della richiesta originale e la stringa di query.
   * `x-edgeoptimize-api-key` - Autentica la richiesta con il servizio Edge Optimize.
   * `x-edgeoptimize-config` - Fornisce la configurazione delle chiavi nella cache.

6. **Logica di failover:** se il servizio Edge Optimize restituisce un codice di stato di errore (errori client 4XX o errori server 5XX) o la richiesta non riesce a causa di un errore di rete, il processo di lavoro esegue automaticamente il failover sulla tua origine utilizzando `EDGE_OPTIMIZE_TARGET_HOST`. La risposta di failover include l’intestazione `x-edgeoptimize-fo: 1` per indicare che si tratta di failover.

7. **Gestione del reindirizzamento:** l’opzione `redirect: "manual"` fa sì che le risposte di reindirizzamento dal servizio Edge Optimize vengano trasmesse al client senza che il processo di lavoro le segua.

**Personalizzazione della configurazione**

Puoi personalizzare il comportamento del processo di lavoro modificando le costanti di configurazione all’inizio del codice:

**Elenco dei bot agentici**

Modifica l’array `AGENTIC_BOTS` per aggiungere o rimuovere agenti utente:

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

Per impostazione predefinita, tutte le pagine HTML vengono indirizzate al servizio Edge Optimize. Per limitare l’indirizzamento a percorsi specifici, modifica l’array `TARGETED_PATHS`:

```javascript
// Route all HTML pages (default)
const TARGETED_PATHS = null;

// Or specify exact paths to route
const TARGETED_PATHS = ['/', '/page.html', '/products', '/about-us'];
```

**Cofigurazione del failover**

Per impostazione predefinita, il processo di lavoro esegue il failover in caso di errori 4XX o 5XX dal servizio Edge Optimize. Personalizza questo comportamento:

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

* **Comportamento di failover:** se il servizio Edge Optimize restituisce un errore (con codici di stato 4XX o 5XX) o se la richiesta non riesce a causa di un errore di rete, il processo di lavoro esegue automaticamente il failover sull’origine. Il failover utilizza `EDGE_OPTIMIZE_TARGET_HOST` come dominio di origine, simile a `F_Default_Origin` di Fastly o `Default_Origin` di CloudFront. Le risposte di failover includono l’intestazione `x-edgeoptimize-fo: 1`, che puoi utilizzare a scopo di monitoraggio e debug.

* **Memorizzazione in cache:** per impostazione predefinita, Cloudflare memorizza le risposte nella cache in base all’URL. Poiché il traffico da IA agentica riceve contenuti diversi rispetto al traffico da persone, assicurati che la configurazione della cache tenga conto di tali differenze. Per distinguere i contenuti memorizzati in cache, puoi utilizzare l’API cache o intestazioni per la cache. L’intestazione `x-edgeoptimize-config` deve essere inclusa nella chiave della cache.

* **Limite di frequenza:** monitora l’utilizzo del servizio Edge Optimize e, se necessario, puoi implementare un limite di frequenza per il traffico da IA agentica.

* **Test:** prima di implementare in produzione, verifica sempre la configurazione in un ambiente di staging. Verifica che il sia traffico agentico sia quello da persone si comportino come previsto. Verifica il comportamento di failover simulando errori del servizio Edge Optimize.

* **Registrazione:** abilita la registrazione dei processi di lavoro Cloudflare per monitorare le richieste e risolvere eventuali problemi. Passa a **Workers** (Processi di lavoro) > **tuo processo di lavoro** > **Logs** (Registri) per visualizzare i registri in tempo reale. Il processo di lavoro registra gli eventi di failover a scopo di debug.

**Risoluzione dei problemi**

| Problema | Causa possibile | Soluzione |
|-------|----------------|----------|
| Nessuna intestazione `x-edgeoptimize-request-id` nella risposta | Indirizzamento del processo di lavoro non corrispondente oppure agente utente non presente nell’elenco dei bot agentici. | Verifica che il pattern di indirizzamento corrisponda all’URL della richiesta. Verifica che l’agente utente si trovi nell’array `AGENTIC_BOTS`. |
| Errori 401 o 403 dal servizio Edge Optimize | Chiave API non valida o mancante. | Verifica che `EDGE_OPTIMIZE_API_KEY` sia impostato correttamente nei segreti e nelle variabili di ambiente. Contatta Adobe per verificare che la tua chiave API sia attiva. |
| Reindirizzamenti o cicli infiniti | Intestazione di protezione del ciclo non impostata o controllata correttamente. | Assicurati che il controllo dell’intestazione `x-edgeoptimize-request` sia attivo. |
| Traffico da persone interessato da modifiche | Logica di indirizzamento del processo di lavoro troppo ampia. | Verifica che la logica di corrispondenza dell’agente utente sia corretta e senza distinzione minuscole/maiuscole. Verifica che `TARGETED_PATHS` sia configurato correttamente. |
| Tempi di risposta lenti | Latenza di rete verso il back-end del servizio Edge Optimize. | È un comportamento normale per la prima richiesta; le richieste successive vengono memorizzate nella cache del servizio Edge Optimize. |
| Intestazione `x-edgeoptimize-fo: 1` nella risposta | Il servizio Edge Optimize ha restituito un errore e si è verificato il failover sull’origine. | Individua il codice di errore specifico nei registri dei processi di lavoro di Cloudflare. Verifica lo stato del servizio Edge Optimize presso Adobe. |
| Failover non funzionante | Flag di failover disabilitati o errore nella logica di failover. | Verifica che `FAILOVER_ON_4XX` e `FAILOVER_ON_5XX` siano impostati su `true`. Verifica la presenza di messaggi di errore nei registri del processo di lavoro. |
| Alcuni percorsi non sono ottimizzati | Il percorso non corrisponde ai percorsi di destinazione o al pattern della pagina HTML. | Verifica che il percorso sia in `TARGETED_PATHS` (se specificato) e che corrisponda al pattern regex della pagina HTML. |
| Richieste non riuscite con host non valido | `EDGE_OPTIMIZE_TARGET_HOST` include il protocollo, ad esempio `https://`. | Utilizza solo il nome di dominio senza protocollo (ad esempio: `example.com` e non `https://example.com`). |
| Errore 530 durante il failover | Cloudflare non è in grado di connettersi all’origine oppure la richiesta di failover contiene intestazioni non valide. | Assicurati che la funzione di failover rimuova le intestazioni del servizio Edge Optimize. Verifica che l’origine sia accessibile e che il DNS sia configurato correttamente. |

**Consenti Ottimizza su rete Edge tramite le regole del firewall (facoltativo)**

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
