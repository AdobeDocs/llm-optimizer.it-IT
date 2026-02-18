---
title: Ottimizza in Edge - Cloudflare (BYOCDN)
description: Scopri come configurare Cloudflare BYOCDN per l’ottimizzazione in Edge in LLM Optimizer.
feature: Opportunities
source-git-commit: 23752b30294c3d467ca477b085aa521cad0f72ca
workflow-type: tm+mt
source-wordcount: '1250'
ht-degree: 1%

---


# Cloudflare (BYOCDN)

Questa configurazione indirizza il traffico agente (richieste da bot di IA e agenti utente LLM) al servizio back-end Edge Optimize (`live.edgeoptimize.net`). I visitatori umani e i bot SEO continuano a essere serviti dalla tua origine come al solito. Per verificare la configurazione, al termine dell&#39;installazione, cercare l&#39;intestazione `x-edgeoptimize-request-id` nella risposta.

**Prerequisiti**

Prima di impostare le regole di instradamento di Cloud Worker, verificare di disporre dei seguenti elementi:

* Un account Cloudflare con processi di lavoro abilitati nel dominio.
* Accedere alle impostazioni DNS del dominio in Cloud Flare.
* Processo di onboarding in LLM Optimizer completato.
* Inoltro del registro CDN a LLM Optimizer completato.
* Chiave API di ottimizzazione Edge recuperata dall’interfaccia utente di LLM Optimizer.

{{retrieve-byocdn-api-key}}

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

{{verify-setup-byocdn}}

{{return-to-overview}}
