---
title: Ottimizza in Edge
description: Scopri come distribuire le ottimizzazioni in LLM Optimizer al server Edge di CDN senza alcuna modifica di authoring necessaria.
feature: Opportunities
source-git-commit: 0e48118b823686d3b86fb3bb83a091340ca577b8
workflow-type: tm+mt
source-wordcount: '2149'
ht-degree: 1%

---


# Ottimizza in Edge

Questa pagina fornisce una panoramica dettagliata su come distribuire ottimizzazioni al server Edge di CDN senza alcuna modifica di authoring. Descrive il processo di onboarding, le opportunità di ottimizzazione disponibili e come ottimizzare automaticamente in Edge.

>[!NOTE]
>Questa funzionalità è attualmente in fase di accesso anticipato. Ulteriori informazioni sui programmi con accesso anticipato [sono disponibili qui](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/release-notes/release-notes/release-notes-current#aem-beta-programs).

## Cos’è l’ottimizzazione in Edge?

Ottimizza in Edge è una funzionalità di distribuzione basata su edge in LLM Optimizer che fornisce modifiche di facile utilizzo dell’intelligenza artificiale agli agenti utente LLM. Nel contesto corrente, &quot;Edge&quot; significa che l’ottimizzazione viene applicata a livello CDN. Poiché offre ottimizzazioni a livello CDN, non sono necessarie modifiche di authoring in Content Management System (CMS) in modo che il CMS di origine rimanga invariato. Questa separazione consente di migliorare la visibilità LLM senza modificare i flussi di lavoro di pubblicazione esistenti. Il targeting riguarda solo il traffico agenziale e non influisce né sugli utenti umani né sui bot SEO (Search Engine Optimization). Quando LLM Optimizer rileva opportunità per ottimizzare una pagina, gli utenti possono distribuire correzioni direttamente al server Edge di CDN.

L’ottimizzazione in Edge è un’alternativa più veloce e più snella alle correzioni tradizionali che richiedono interventi di progettazione complessi. Come accennato, una volta completata la configurazione una tantum, non è necessario apportare modifiche alla piattaforma né eseguire lunghi cicli di sviluppo per applicare le modifiche. Puoi pubblicare miglioramenti in pochi minuti senza richiedere il coinvolgimento degli sviluppatori. È un modo senza codice per ottimizzare il sito web per gli agenti di intelligenza artificiale.

Ottimizza in Edge è progettato per gli utenti aziendali nei team di marketing, SEO, contenuti e strategie digitali. Consente agli utenti aziendali di completare l’intero percorso in LLM Optimizer: identificando le opportunità, comprendendo i suggerimenti e distribuendo facilmente le correzioni. Con Ottimizza in Edge, gli utenti possono visualizzare in anteprima le modifiche, distribuirle rapidamente all’edge della CDN e verificare che le ottimizzazioni siano attive. Le prestazioni possono essere tracciate nell’ecosistema LLM Optimizer.

### Vantaggi chiave

* **Distribuzione solo IA:** fornisce HTML ottimizzato solo agli agenti di IA senza impatto sui visitatori umani o sui bot SEO.
* **Cicli più veloci:** Pubblicare le modifiche in pochi minuti anziché settimane. Non sono necessari cambiamenti di piattaforma o lunghi cicli tecnici.
* **Reversibile:** supportato con funzionalità di rollback con un solo clic che consente di ripristinare la pagina in pochi minuti.
* **Nessun impatto sulle prestazioni:** le ottimizzazioni basate su Edge e la memorizzazione nella cache non influiscono sulla latenza del sito.
* **CDN e CMS-agnostic:** funziona con qualsiasi configurazione CDN e configurazione front-end indipendentemente dal sistema di gestione dei contenuti.

### Quali opportunità sono supportate con Ottimizza in Edge?

Le opportunità che possono migliorare l’esperienza agentica sul web sono supportate con l’ottimizzazione in Edge. Ulteriori informazioni su ogni opportunità sono disponibili sia nella pagina [Dashboard opportunità](/help/dashboards/opportunities.md) che nella sezione opportunità della pagina corrente.

## Onboarding

Per avviare il processo di onboarding, contatta il team del tuo account Adobe o il team FDE. Il team IT o CDN deve inoltre completare i prerequisiti e il processo di configurazione. Inoltre, puoi contattare `llmo-at-edge@adobe.com` per ulteriore assistenza sull&#39;onboarding.

Prerequisiti per l’onboarding per l’ottimizzazione in Edge:

* Completa il processo di onboarding in LLM Optimizer.
* Completa il processo di inoltro dei registri per i registri CDN.

Requisiti per il team IT/CDN:

* Genera una chiave API.
* Aggiungi le regole di instradamento Ottimizza in Edge nella rete CDN.
* Inserire nell&#39;elenco Consentiti percorsi definiti dall&#39;utente o l&#39;intero dominio.
* Aggiungere un elenco definito dall&#39;utente di agenti utente LLM per la destinazione.
* Assicurarsi che `robots.txt` non blocchi gli agenti utente destinati alla destinazione.
* Conferma il routing di ottimizzazione in Edge nell’interfaccia di LLM Optimizer.

Di seguito sono riportate alcune configurazioni esemplificative per diverse configurazioni CDN. Tieni presente che questi esempi devono essere adattati alla tua configurazione live effettiva. È consigliabile applicare prima le modifiche negli ambienti inferiori.

>[!BEGINTABS]

>[!TAB CDN gestito da Adobe]

**CDN gestito da Adobe**

Questa configurazione ha lo scopo di configurare le richieste con agenti utente che verranno instradati al servizio Optimizer (`live.edgeoptimize.net` backend). Per verificare la configurazione, al termine dell&#39;installazione cercare l&#39;intestazione `x-edgeoptimize-request-id` nella risposta.

```
curl -svo page.html https://frescopa.coffee/about-us --header "user-agent: chatgpt-user"
< HTTP/2 200
< x-edgeoptimize-request-id: 50fce12d-0519-4fc6-af78-d928785c1b85
```

La configurazione del routing viene eseguita utilizzando una regola CDN [originSelector](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/content-delivery/cdn-configuring-traffic#origin-selectors). I prerequisiti sono i seguenti:

* decidere il dominio da instradare
* decidere i percorsi da instradare
* decidere gli agenti utente da instradare (consigliato regex)

Per distribuire la regola, è necessario:

* crea una [pipeline di configurazione](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/operations/config-pipeline)
* eseguire il commit del file di configurazione `cdn.yaml` nel repository
* eseguire la pipeline di configurazione


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

Per testare l’installazione, esegui una curl e osserva quanto segue:

```
curl -svo page.html https://www.example.com/page.html --header "user-agent: chatgpt-user"
< HTTP/2 200
< x-edgeoptimize-request-id: 50fce12d-0519-4fc6-af78-d928785c1b85
```

<!-- >>[!TAB Akamai (BYOCDN)]

**Tokowaka BYOCDN - Akamai**

```
{
    "name": "Project Tokowaka CDN Rule",
    "children": [
        {
            "name": "Connection settings",
            "children": [],
            "behaviors": [
                {
                    "name": "advanced",
                    "options": {
                        "description": "",
                        "xml": "<forward:availability.health-detect.status>off</forward:availability.health-detect.status>\n<forward:availability>\n<max-reforwards>1</max-reforwards>\n<max-reconnects>1</max-reconnects>\n</forward:availability>\n<match:forward.server-type value=\"CUSTOMER_ORIGIN\">\n<network:http.read>%(PMUSER_HTTP_READ)</network:http.read>\n<network:http.first-byte-timeout>%(PMUSER_FIRST_BYTE_TIMEOUT)</network:http.first-byte-timeout>\n<network:http.connect-timeout>%(PMUSER_HTTP_CONNECT_TIMEOUT)</network:http.connect-timeout> \n</match:forward.server-type>"
                    },
                    "uuid": "4a8c027b-1b23-44a7-8e12-f8d07e453679",
                    "templateUuid": "41c77091-419f-43f2-9a84-0b406b050cc8"
                }
            ],
            "uuid": "4759571b-8036-4c16-9b60-d3aeb84958f1",
            "criteria": [],
            "criteriaMustSatisfy": "all"
        },
        {
            "name": "Site Failover Behavior",
            "children": [],
            "behaviors": [
                {
                    "name": "failAction",
                    "options": {
                        "actionType": "RECREATED_CO",
                        "contentCustomPath": false,
                        "contentHostname": "www.adobe.com",
                        "enabled": true
                    }
                },
                {
                    "name": "advanced",
                    "options": {
                        "description": "",
                        "xml": "<forward:availability.fail-action2>\n<add-header>\n<status>on</status>\n<name>x-tokowaka-request</name>\n<value>fo</value>\n</add-header>\n</forward:availability.fail-action2>"
                    }
                }
            ],
            "uuid": "b3000c12-1ab8-49b1-a5d0-75e58bb18c9c",
            "criteria": [
                {
                    "name": "matchResponseCode",
                    "options": {
                        "lowerBound": 400,
                        "matchOperator": "IS_BETWEEN",
                        "upperBound": 599
                    }
                },
                {
                    "name": "originTimeout",
                    "options": {
                        "matchOperator": "ORIGIN_TIMED_OUT"
                    }
                }
            ],
            "criteriaMustSatisfy": "any",
            "comments": "If Tokowaka origin returns a 4xx or 5xx error (or times out), failover condition is to send the request back to Akamai and set the x-tokowaka-request header so we don't re-send the request to Tokowaka"
        }
    ],
    "behaviors": [
        {
            "name": "origin",
            "options": {
                "cacheKeyHostname": "ORIGIN_HOSTNAME",
                "compress": true,
                "customValidCnValues": [
                    "{{Origin Hostname}}",
                    "{{Forward Host Header}}",
                    "*.tokowaka.now"
                ],
                "enableTrueClientIp": true,
                "forwardHostHeader": "ORIGIN_HOSTNAME",
                "hostname": "edge.tokowaka.now",
                "httpPort": 80,
                "httpsPort": 443,
                "ipVersion": "IPV4",
                "minTlsVersion": "DYNAMIC",
                "originCertificate": "",
                "originCertsToHonor": "STANDARD_CERTIFICATE_AUTHORITIES",
                "originSni": true,
                "originType": "CUSTOMER",
                "ports": "",
                "standardCertificateAuthorities": [
                    "akamai-permissive",
                    "THIRD_PARTY_AMAZON"
                ],
                "tlsVersionTitle": "",
                "trueClientIpClientSetting": true,
                "trueClientIpHeader": "True-Client-IP",
                "verificationMode": "CUSTOM"
            }
        },
        {
            "name": "setVariable",
            "options": {
                "transform": "NONE",
                "valueSource": "EXPRESSION",
                "variableName": "PMUSER_LLMCLIENT",
                "variableValue": "TRUE"
            }
        },
        {
            "name": "setVariable",
            "options": {
                "caseSensitive": false,
                "extractLocation": "CLIENT_REQUEST_HEADER",
                "globalSubstitution": false,
                "headerName": "Accept-Language ",
                "regex": "^([a-zA-Z]{2}).*",
                "replacement": "$1",
                "transform": "SUBSTITUTE",
                "valueSource": "EXTRACT",
                "variableName": "PMUSER_LANG"
            }
        },
        {
            "name": "setVariable",
            "options": {
                "transform": "NONE",
                "valueSource": "EXPRESSION",
                "variableName": "PMUSER_X_FORWARDED_HOST",
                "variableValue": "{{builtin.AK_HOST}}"
            }
        },
        {
            "name": "setVariable",
            "options": {
                "transform": "NONE",
                "valueSource": "EXPRESSION",
                "variableName": "PMUSER_TOKOWAKA_CACHE_KEY",
                "variableValue": "LLMCLIENT={{user.PMUSER_LLMCLIENT}};LANG={{user.PMUSER_LANG}};X_FORWARDED_HOST={{user.PMUSER_X_FORWARDED_HOST}}"
            }
        },
        {
            "name": "caching",
            "options": {
                "behavior": "CACHE_CONTROL_AND_EXPIRES",
                "cacheControlDirectives": "",
                "defaultTtl": "1d",
                "enhancedRfcSupport": false,
                "honorMustRevalidate": false,
                "honorPrivate": false,
                "mustRevalidate": false
            }
        },
        {
            "name": "modifyIncomingRequestHeader",
            "options": {
                "action": "MODIFY",
                "avoidDuplicateHeaders": true,
                "customHeaderName": "X-tokowaka-api-key",
                "newHeaderValue": "<your api-key here>",
                "standardModifyHeaderName": "OTHER"
            }
        },
        {
            "name": "modifyIncomingRequestHeader",
            "options": {
                "action": "MODIFY",
                "avoidDuplicateHeaders": true,
                "customHeaderName": "x-tokowaka-config",
                "newHeaderValue": "LLMCLIENT={{user.PMUSER_LLMCLIENT}};LANG={{user.PMUSER_LANG}}",
                "standardModifyHeaderName": "OTHER"
            }
        },
        {
            "name": "modifyIncomingRequestHeader",
            "options": {
                "action": "MODIFY",
                "avoidDuplicateHeaders": true,
                "customHeaderName": "x-tokowaka-url",
                "newHeaderValue": "{{builtin.AK_URL}}",
                "standardModifyHeaderName": "OTHER"
            }
        },
        {
            "name": "cacheId",
            "options": {
                "rule": "INCLUDE_VARIABLE",
                "variableName": "PMUSER_TOKOWAKA_CACHE_KEY"
            }
        },
        {
            "name": "modifyIncomingResponseHeader",
            "options": {
                "action": "DELETE",
                "customHeaderName": "Age",
                "standardDeleteHeaderName": "OTHER"
            }
        },
        {
            "name": "prefreshCache",
            "options": {
                "enabled": true,
                "prefreshval": 90
            }
        },
        {
            "name": "modifyOutgoingRequestHeader",
            "options": {
                "action": "MODIFY",
                "avoidDuplicateHeaders": true,
                "customHeaderName": "X-Forwarded-Host",
                "newHeaderValue": "{{builtin.AK_HOST}}",
                "standardModifyHeaderName": "OTHER"
            }
        }
    ],
    "criteria": [
        {
            "name": "userAgent",
            "options": {
                "matchCaseSensitive": false,
                "matchOperator": "IS_ONE_OF",
                "matchWildcard": true,
                "values": [
                    "*Tokowaka-AI*",
                    "*ChatGPT-User*",
                    "*GPTBot*",
                    "*OAI-SearchBot*"
                ]
            }
        },
        {
            "name": "path",
            "options": {
                "matchCaseSensitive": false,
                "matchOperator": "MATCHES_ONE_OF",
                "normalize": false,
                "values": [
                ]
            }
        },
        {
            "name": "requestHeader",
            "options": {
                "headerName": "x-tokowaka-request",
                "matchOperator": "DOES_NOT_EXIST",
                "matchWildcardName": false
            }
        },
        {
            "name": "matchVariable",
            "options": {
                "matchCaseSensitive": true,
                "matchOperator": "IS",
                "matchWildcard": false,
                "variableExpression": "FALSE",
                "variableName": "PMUSER_TOKOWAKA_DISABLE"
            }
        }
    ],
    "criteriaMustSatisfy": "all"
}
```

Important considerations:

* Tokowaka Rule will be ON based on User-Agent + Path + x-tokowaka-request (if not present) + TOKOWAKA_DISABLE variable (to allow switch off using a single variable toggle)
* Set up rules to **Modify Incoming Request Headers** rule to set custom headers
* Set cache-key in Akamai using user defined variable through Cache-ID modification mechanism. Only a single user defined variable is allowed, so create a separate variable for cache_key and set it accordingly.
* Lang: extracted from Accept-Language header using "regex": "^([a-zA-Z]{2}).*"
* With Cache ID Modification within a match on User Agent, the content can't be purged by URL (just FYI)
* Site failover mechanism: With the match on User-Agent rule, Akamai does not allows to failover based on health check, but only only basis of origin response/connectivity per request. Set **x-tokowaka-fo:true**  resp header in case of failover response.
* SWR is not supported by Akamai. So, only TTL based caching is there. So, configure a rule in Akamai to strip Age header from origin response else TTL based caching would not work.
* Ensure that the Tokowaka rule is the bottom most rule in the rule hierarchy (so that it overrides all other rules).-->

>[!TAB Fastly (BYOCDN)]

**Ottimizzazione BYOCDN Edge - Fastly - VCL**

![VCL Fastly](/help/assets/optimize-at-edge/fastly-vcl.png)

![Aggiungi snippet VCL](/help/assets/optimize-at-edge/add-vcl-snippets.png)

**snippet vcl_recv**

```
unset req.http.x-edgeoptimize-url;
unset req.http.x-edgeoptimize-config;
unset req.http.x-edgeoptimize-api-key;

if (!req.http.x-edgeoptimize-request
    && req.http.user-agent ~ "(?i)(AdobeEdgeOptimize-AI|ChatGPT-User|GPTBot|OAI-SearchBot|PerplexityBot|Perplexity-User)") {
  set req.http.x-fowarded-host = req.http.host; # required for identifying the original host
  set req.http.x-edgeoptimize-url = req.url; # required for identifying the original url
  set req.http.x-edgeoptimize-config = "LLMCLIENT=true"; # required for cache key
  set req.http.x-edgeoptimize-api-key = "<YOUR API KEY>"; # required for identifying the client
  set req.backend = F_EDGE_OPTIMIZE;
}
```

**frammento vcl_hash**

```
if (req.http.x-edgeoptimize-config) {
  set req.hash += "edge-optimize";
  set req.hash += req.http.x-edgeoptimize-config;
}
```

**vcl_deliver snippet**

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

>[!ENDTABS]

>[!NOTE]
>Per gli altri provider CDN, contatta `llmo-at-edge@adobe.com` per assistere i team IT/CDN nell&#39;onboarding. Una volta completate le configurazioni di configurazione, puoi implementare i suggerimenti per Ottimizzare alle opportunità Edge in LLM Optimizer.

## Opportunità

Nella tabella seguente sono presentate le opportunità che possono migliorare l’esperienza web dell’agente e sono supportate da Ottimizza in Edge.

| Opportunità | Tipo | Identificazione automatica | Suggerimento automatico | Ottimizzazione automatica |
|---------|----------|----------|----------|----------|
| Recupera visibilità contenuto | GEO tecnico | Rileva le pagine in cui il contenuto critico è nascosto dagli agenti di intelligenza artificiale. Mostra gli URL interessati e il contenuto previsto che può essere recuperato. | Evidenzia i contenuti che possono essere resi disponibili per gli agenti di intelligenza artificiale e consiglia di abilitare il pre-rendering per tali pagine. | Distribuisce un’istantanea di HTML completamente renderizzata e compatibile con l’intelligenza artificiale al traffico agente che recupera il contenuto precedentemente nascosto. |
| Ottimizzare le intestazioni per i moduli LLM | Ottimizzazione dei contenuti | Esegue la scansione delle intestazioni per rilevare intestazioni vuote, duplicate, mancanti o ambigue che possono ridurre la leggibilità del computer. | Propone una gerarchia di titoli più pulita e etichette migliorate e mostra un’anteprima della struttura aggiornata per ogni pagina. | Inserisce la struttura di intestazione migliorata per gli agenti di intelligenza artificiale, preservando la progettazione visiva e rendendo la pagina più leggibile per i moduli LLM. |
| Aggiungi riepiloghi descrittivi LLM | Ottimizzazione dei contenuti | Identifica pagine lunghe o complesse prive di riepiloghi concisi a livello di pagina o di sezione, rendendo più difficile l’analisi e la comprensione da parte dell’intelligenza artificiale. | Consiglia brevi riepiloghi generati dall’intelligenza artificiale a livello di pagina e di sezione, per l’acquisizione di contenuti chiave. | Inserisce i riepiloghi nelle sezioni pertinenti di HTML, migliorando il modo in cui i modelli interpretano e descrivono il contenuto della pagina. |
| Aggiungi domande frequenti pertinenti | Ottimizzazione dei contenuti | Rileva le lacune nelle finalità del contenuto della pagina esistente che potrebbero trarre vantaggio dalle domande frequenti. | Suggerisce contenuti FAQ generati dall’intelligenza artificiale in linea con le intenzioni dell’utente e gli argomenti esistenti. | Inserisce i contenuti delle domande frequenti in HTML, rendendo le pagine più individuabili e rilevanti nelle risposte basate sull’intelligenza artificiale. |
| Semplificare contenuti complessi | Ottimizzazione dei contenuti | Contrassegna le pagine con testo complesso che può ostacolare la comprensione dell’intelligenza artificiale. | Fornisce versioni semplificate generate dall&#39;intelligenza artificiale di testo complesso mantenendo il significato originale. | Riscrive sezioni complesse nella pagina, migliorando la leggibilità dell’intelligenza artificiale. |

### Strumenti aggiuntivi

[Adobe LLM Optimizer: la tua pagina Web è consultabile?L&#39;estensione Chrome &#x200B;](https://chromewebstore.google.com/detail/adobe-llm-optimizer-is-yo/jbjngahjjdgonbeinjlepfamjdmdcbcc) mostra la quantità di contenuto della pagina Web a cui i moduli LLM possono accedere e ciò che rimane nascosto. Progettato come strumento diagnostico indipendente e gratuito, non richiede alcuna licenza o configurazione del prodotto.

Con un solo clic, puoi valutare la leggibilità automatica di qualsiasi sito. Puoi visualizzare un confronto affiancato tra ciò che gli agenti di intelligenza artificiale vedono e ciò che gli utenti umani vedono, e stimare quanto contenuto potrebbe essere recuperato utilizzando LLM Optimizer. Consulta [Può AI leggere il tuo sito Web?](https://business.adobe.com/blog/introducing-the-llm-optimizer-chrome-extension) pagina per ulteriori informazioni.

## Opportunità dettagliate

Nelle sezioni seguenti, puoi visualizzare ulteriori dettagli per ogni opportunità supportata con Ottimizza in Edge.

### Recupera visibilità contenuto

Questa opportunità contrassegna le pagine in cui il contenuto chiave è nascosto per gli agenti AI a causa del rendering lato client. Per ogni pagina identificata, mostra esattamente quale contenuto manca dalla vista dell’agente di intelligenza artificiale, evidenzia le lacune di visibilità e consente di applicare direttamente le modifiche per recuperare il contenuto nascosto. Quando distribuisci questa opportunità con Optimize at Edge, agli agenti utente LLM viene distribuita una versione della pagina pre-renderizzata e ottimizzata per l’intelligenza artificiale, in modo che possano accedere al contesto completo senza eseguire Javascript.
In questo modo la pagina sarà prima completamente visibile agli agenti di intelligenza artificiale. Ulteriori miglioramenti vengono applicati al HTML pre-renderizzato.

>[!IMPORTANT]
>Questa funzionalità di pre-rendering si applica automaticamente a tutte le opportunità presentate di seguito quando viene implementato con Ottimizza in Edge per garantire che la pagina sia completamente visibile agli agenti AI.

### Ottimizzare le intestazioni per i moduli LLM

Questa opportunità rileva le pagine in cui la struttura dell’intestazione rende difficile per gli agenti AI comprendere la pagina a causa di intestazioni vuote, duplicate, mancanti o ambigue. Per ogni pagina interessata, l’opportunità fa emergere i titoli non ottimali e consiglia una gerarchia più chiara. Quando vengono implementati con Ottimizza in Edge, i titoli migliorati vengono applicati nel HTML utilizzato per il traffico agente. In questo modo è possibile migliorare la leggibilità della macchina lasciando invariato il layout rivolto agli utenti.

### Aggiungi riepiloghi descrittivi LLM

Questa opportunità identifica le pagine che possono trarre vantaggio da riepiloghi concisi per aiutare i moduli LLM a comprendere rapidamente di cosa si tratta il contenuto della pagina. Per ogni pagina, l’opportunità rileva dove è più necessario un riepilogo e crea riepiloghi generati dall’intelligenza artificiale a livello di pagina o di sezione. Quando distribuisci con Ottimizza in Edge, questi riepiloghi vengono inseriti nel HTML che gli agenti di intelligenza artificiale recuperano, migliorando le possibilità di descrizione più accurata del contenuto.

### Aggiungi domande frequenti pertinenti

Questa opportunità segnala le pagine in cui i contenuti aggiuntivi di domande e risposte potrebbero corrispondere meglio alle intenzioni dell’utente e alle richieste nell’individuazione basata sull’intelligenza artificiale. Per ogni pagina, propone blocchi di domande frequenti generati dall’intelligenza artificiale associati alle intenzioni dell’utente e al contenuto della pagina. Con Optimize at Edge, queste domande frequenti vengono inserite in HTML, rendendo la pagina più intuitiva e aumentando la probabilità che le risposte di IA riflettano direttamente la tua guida.

### Semplificare contenuti complessi

Questa opportunità trova pagine con paragrafi lunghi e complessi che possono ridurre la comprensione dell’intelligenza artificiale. Per ogni pagina che supera le soglie di leggibilità, crea contenuti generati dall’intelligenza artificiale più semplici e facili da scansionare, mantenendo il significato originale. Quando viene distribuito ai server perimetrali, il contenuto semplificato distribuito al traffico agente consente ai moduli LLM di interpretare e riepilogare i contenuti in modo più fedele.

## Ottimizzazione automatica in Edge

Per ogni opportunità, puoi visualizzare in anteprima, modificare, distribuire, visualizzare in tempo reale e eseguire il rollback delle ottimizzazioni al limite.

>[!VIDEO](https://video.tv.adobe.com/v/3477983/?learn=on&enablevpops)

### Anteprima

**Anteprima** consente di visualizzare l&#39;impatto di un suggerimento prima che venga pubblicato. Mette in evidenza una differenza affiancata tra la pagina corrente e la versione ottimizzata per l’intelligenza artificiale prevista dopo l’applicazione del suggerimento. Questa vista utilizza la stessa logica di Ottimizzazione in Edge che alimenta il traffico in tempo reale, ma in modalità di anteprima isolata. Questo non influisce sul traffico in tempo reale, in quanto si tratta di una simulazione di sola lettura per la revisione.

![Anteprima](/help/assets/optimize-at-edge/preview.png)

### Modifica

**Modifica** ti consente di perfezionare o riscrivere completamente il suggerimento generato automaticamente prima di distribuirlo. Invece di accettare il suggerimento, puoi mantenere il controllo completo tramite il flusso di lavoro di modifica. La vista mostra le modifiche proposte in un editor strutturato, dove puoi modificare il testo per soddisfare meglio l’intento originale. La versione modificata verrà quindi trasmessa agli agenti di intelligenza artificiale una volta distribuita.

![Modifica](/help/assets/optimize-at-edge/edit.png)

### Distribuzione

**Distribuisci** pubblica i suggerimenti selezionati in modo che le esperienze ottimizzate possano essere distribuite dal server Edge agli agenti di intelligenza artificiale. Se la rete CDN è completamente instradata, in genere tutte le pagine del dominio vengono pubblicate con le nuove modifiche in pochi minuti. Se il routing è stato configurato solo per alcuni percorsi, solo le pagine inserite nell&#39;elenco Consentiti vengono pubblicate con le ottimizzazioni.

![Distribuisci](/help/assets/optimize-at-edge/deploy.png)

### Visualizza in diretta

**Visualizza Live** consente di verificare che l&#39;ottimizzazione sia attiva e che si comporti come previsto per il traffico agente, una visualizzazione a cui altrimenti sarebbe difficile accedere. Puoi visualizzare la pagina live in Suggerimenti fissi, che esegue il rendering della pagina come mostrato agli agenti di intelligenza artificiale.

![Visualizza Live](/help/assets/optimize-at-edge/view-live.png)

### Rollback

Il rollback ripristina in modo sicuro un’ottimizzazione distribuita in precedenza. In genere, lo stato della versione solo IA della pagina viene ripristinato allo stato precedente in pochi minuti, rendendo sicure le possibilità di sperimentazione con le ottimizzazioni quando necessario.

![Rollback](/help/assets/optimize-at-edge/rollback.png)

## Domande frequenti

D. Di quali tipi di moduli LLM si esegue il targeting con Optimize at Edge?

L’elenco degli agenti utente di destinazione viene definito dall’utente durante il processo di onboarding.

<!--Q. What does "Edge" in Optimize at Edge mean?

In our context, "Edge" means that the optimization is applied at the CDN layer and not inside your CMS.

Q. Why does this optimization require a CDN?

The CDN is where the optimized version of the page is assembled and delivered to AI agents. We leverage the CDN to ensure your origin CMS remains unchanged. This separation lets you improve LLM visibility without altering your existing publishing workflows.-->

D. Cosa succede se non ho ancora effettuato l’onboarding per ottimizzare in Edge?

Se fai clic su **Distribuisci ottimizzazioni** prima di completare la configurazione richiesta, non verrà applicato nulla al tuo sito. Viene invece visualizzata una finestra di dialogo a comparsa in cui viene richiesto di contattare il team all&#39;indirizzo `llmo-at-edge@adobe.com` per assistenza sull&#39;onboarding. Fino a quando l’onboarding non è completo, puoi ancora esplorare le opportunità e i suggerimenti rilevati, ma il flusso di lavoro di distribuzione con un solo clic rimarrà inattivo.

D: Cosa succede quando il contenuto viene aggiornato alla sorgente?

Distribuiamo la versione ottimizzata della pagina dalla cache, purché la pagina sorgente sottostante non sia cambiata. Tuttavia, quando l’origine cambia, il sistema si aggiorna automaticamente in modo che gli agenti AI ricevano sempre il contenuto più aggiornato. Questo perché utilizziamo impostazioni TTL (time-to-live) della cache ridotte (in ordine di minuti) in modo che qualsiasi aggiornamento del contenuto sul sito attivi una nuova ottimizzazione all’interno di tale finestra. <!--As there is no universal TTL that fits every site, we can configure this TTL based on your cache invalidation rules to ensure both systems stay in sync.-->

D. L’ottimizzazione in Edge è valida solo per i siti che utilizzano Adobe Edge Delivery Service (EDS)?

No. L’ottimizzazione in Edge è indipendente dalla CDN e funziona con qualsiasi architettura front-end, non solo quelle distribuite sullo stack EDS di Adobe.

D. In che modo l’ottimizzazione a livello di pre-rendering di Edge è diversa dal rendering lato server tradizionale?

Entrambi risolvono problemi diversi e possono lavorare insieme. La SSR tradizionale esegue il rendering del contenuto lato server, ma non include il contenuto caricato successivamente nel browser. Il pre-rendering Ottimizza in Edge acquisisce la pagina dopo il caricamento di JavaScript e dei dati lato client, producendo la versione completamente assemblata al limite della CDN. SSR si concentra sul miglioramento dell’esperienza umana e Optimize at Edge migliora l’esperienza web per i moduli LLM.
