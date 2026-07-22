---
title: Ottimizzazione nella rete edge - CloudFront (BYOCDN)
description: Scopri come configurare CloudFront BYOCDN per l’ottimizzazione nella rete edge in LLM Optimizer.
feature: Opportunities
autotag-review: '2026-07-15T17:46:25.674Z'
TQID: 'https://experienceleague.adobe.com/yIEUTzlnvOX-WBf276KQcAN8sGYDpZNVibJt024VMWU'
product_v2:
  - id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2:
  - id: d1956731-2adb-4bb7-8301-2b239254ac72
  - id: e1b649f0-0a61-46e4-9082-64d5cb2576c6
  - id: ef4e63f5-cb4d-462d-bf9a-1f617edf2a3a
  - id: e0828736-236a-487b-a478-5a635455eadc
subfeature_v2:
  - id: d23587d6-14d6-4e3f-9ee1-cc18623832e1
  - id: e06fae5f-830b-4222-a469-b5e148d36465
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: e36ee407933e2d3d56cadf1c9517f23f24d41d91
workflow-type: tm+mt
source-wordcount: 2343
ht-degree: 85%

---


# CloudFront (BYOCDN)

Questa configurazione indirizza il traffico da IA agentica (richieste da bot IA e da agenti utente LLM) al servizio back-end Edge Optimize (`live.edgeoptimize.net`). Le persone e i bot SEO continuano a ricevere come al solito i contenuti trasmessi dalla tua origine. Per testare la configurazione, al termine cerca nella risposta l’intestazione `x-edgeoptimize-request-id`.

**Prerequisiti**

Prima di configurare CloudFront, assicurati di:

* disporre di una distribuzione CloudFront esistente per il tuo sito web;
* disporre di autorizzazioni AWS IAM per creare funzioni Lambda, ruoli IAM, distribuzioni CloudFront e criteri della cache;
* aver recuperato dall’interfaccia di LLM Optimizer una chiave API del servizio Edge Optimize. Per la procedura, consulta [Recuperare le chiavi API](/help/dashboards/optimize-at-edge/retrieve-api-keys.md#production-api-key).
* (Facoltativo) Per verificare l’indirizzamento in fase di staging, consulta [Chiave API di staging](/help/dashboards/optimize-at-edge/retrieve-api-keys.md#staging-api-key-optional).

## Passaggio 1: creare l’origine di Edge Optimize

**Navigazione:** Console AWS > CloudFront > Distribuzioni > [La tua distribuzione] > scheda Origini

1. Fai clic su **Crea origine**.

2. Configura l’origine:
   * **Dominio dell’origine:** `live.edgeoptimize.net`
   * **Nome:** `EdgeOptimize_Origin`

3. Per tutti gli altri campi, lascia invariati i valori predefiniti.

4. Aggiungi intestazioni personalizzate:

   | Intestazione | Valore |
   |--------|-------|
   | `x-edgeoptimize-api-key` | La tua chiave API |
   | `x-forwarded-host` | `www.example.com` |
   | `x-edgeoptimize-fetcher-key` | Chiave fetcher (necessaria solo in caso di WAF di inserire nell&#39;elenco Consentiti) |

   Sostituisci `www.example.com` con il dominio effettivo del tuo sito web e `Your API key` con la chiave API di Edge Optimize fornita dal tuo rappresentante Adobe.

5. Fai clic su **Crea origine**.

![Creazione dell’origine di Cloudfront](/help/assets/optimize-at-edge/cloudfront-origin-creation.png)

## Passaggio 2: creare la funzione di richiesta del visualizzatore

**Navigazione:** Console AWS > CloudFront > Funzioni

1. Fai clic su **Crea funzione**.

2. Configurare:
   * **Nome:** `edgeoptimize-routing`
   * **Runtime:** `cloudfront-js-2.0`

3. Sostituisci il codice predefinito con il codice presente in [viewer-request.js](https://github.com/adobe/llmo-code-samples/blob/main/optimize-at-edge/cloudfront/cloudfront-function/viewer-request.js).

   Prima di pubblicare, personalizza i seguenti valori nel codice:

   * `YOUR_DEFAULT_ORIGIN`: sostituisci con il nome dell’origine predefinita esistente (disponibile in CloudFront > Distribuzioni > [Distribuzione] > scheda Origini).
   * `TARGETED_PATHS`: imposta su `null` per eseguire il targeting di tutte le pagine HTML oppure su un array di percorsi specifici, ad esempio `['/', '/products', '/about']`.

4. Fai clic su **Salva modifiche** > **Funzione di pubblicazione**.

![Creazione della funzione di Cloudfront](/help/assets/optimize-at-edge/cloudfront-function-creation.png)


## Passaggio 3: configurare i criteri della cache

**Navigazione:** Console AWS > CloudFront > Distribuzioni > [La tua distribuzione] > Comportamenti

Verifica il criterio di cache attualmente associato al comportamento. Fai clic su **Modifica** sul comportamento e controlla la sezione **Chiave della cache e richieste di origine** per identificare lo scenario:

* **Scenario A (precedente):** vedi un pulsante di scelta selezionato, con etichetta **Impostazioni cache precedenti**. Non esiste un elenco a discesa del nome dei criteri, ma vedi le impostazioni TTL e di intestazione in linea.
* **Scenario B (criterio personalizzato):** puoi vedere selezionato “**Criterio di cache**” con un nome di criterio creato da te o dal tuo team (non un criterio fornito da AWS).
* **Scenario C (criterio gestito):** puoi vedere selezionato “**Criterio di cache**”con un nome fornito da AWS, ad esempio `CachingOptimized`, `CachingDisabled` o `CachingOptimizedForUncompressedObjects`, che non possono essere modificati.

### Scenario A: impostazioni della cache legacy

Se il comportamento utilizza impostazioni cache precedenti:

1. In **Chiave della cache e richieste di origine**, vedrai selezionato **Impostazioni cache precedenti**.

2. Aggiungi `x-edgeoptimize-config` e `x-edgeoptimize-url` all’elenco delle **Intestazioni** consentite:

   * Seleziona **Includi le seguenti intestazioni** dal menu a discesa.
   * Aggiungi `x-edgeoptimize-config` e `x-edgeoptimize-url`.
     ![Cache Cloudfront precedente](/help/assets/optimize-at-edge/cloudfront-cache-policy-legacy.png)

   Se **Tutti** è già selezionato nel menu a discesa delle intestazioni, salta questo passaggio: tutte le intestazioni vengono inoltrate automaticamente all’origine.

3. Controlla l’impostazione **Caching degli oggetti**:

   * Se impostata su **Personalizza**, è consigliabile impostare **TTL minimo** su `0`. Tuttavia, se il TTL minimo corrente è già molto breve, potrebbe non essere necessario modificarlo.
   * Se impostata su **Usa intestazioni cache di origine**, non sono necessarie modifiche.

4. Fai clic su **Salva modifiche**.

### Scenario B: non legacy con criteri di cache personalizzati

Se il comportamento utilizza già un criterio di cache personalizzato (uno creato dall’utente, non un criterio gestito da AWS):

**Navigazione:** Console AWS > CloudFront > Criteri > Cache

1. Fai clic sul criterio esistente.

2. Fai clic su **Modifica**.

3. È consigliabile impostare **TTL minimo** su `0`. Tuttavia, se il TTL minimo corrente è già molto breve, potrebbe non essere necessario modificarlo.
   ![Impostazioni TTL del criterio di cache](/help/assets/optimize-at-edge/cloudfront-cache-policy-ttl.png)

4. In **Impostazioni chiave della cache** > **Intestazioni**, insieme alle inclusioni esistenti, aggiungi `x-edgeoptimize-config` e `x-edgeoptimize-url`.
   ![Intestazioni del criterio di cache](/help/assets/optimize-at-edge/cloudfront-cache-policy-headers.png)

5. Fai clic su **Salva modifiche**.

### Scenario C: non legacy con criteri di cache gestiti (AWS)

Se il comportamento utilizza un criterio di cache gestito da AWS (per esempio `CachingOptimized`), non puoi modificarlo. Devi creare un nuovo criterio di cache personalizzato che replichi le impostazioni del criterio gestito esistente e aggiunga le intestazioni Edge Optimize in alto.

**Parte 1: prendere nota delle impostazioni del criterio di cache gestito corrente**

**Navigazione:** Console AWS > CloudFront > Criteri > Cache

1. Trova e fai clic sul criterio di cache gestito attualmente associato al comportamento (ad esempio, `CachingOptimized`).

2. Prendi nota di tutte le impostazioni esistenti:
   * TTL minimo, TTL massimo, TTL predefinito
   * Intestazioni incluse nella chiave della cache
   * Cookie inclusi nella chiave della cache
   * Stringhe di query incluse nella chiave della cache
   * Supporto compressione (Gzip, Brotli)

**Parte 2: creare un nuovo criterio di cache personalizzato con le stesse impostazioni e configurare Edge Optimize**

**Navigazione:** Console AWS > CloudFront > Criteri > Cache

1. Fai clic su **Crea criterio di cache**.

2. **Nome:** `edgeoptimize-cache`

   ![Nome criterio di cache](/help/assets/optimize-at-edge/cloudfront-cache-policy-name.png)

3. Replica tutte le impostazioni della Parte 1, con le seguenti modifiche:

   * È consigliabile impostare **TTL minimo** su `0`. Tuttavia, se il TTL minimo corrente è già molto breve, potrebbe non essere necessario modificarlo.

   ![Impostazioni TTL del criterio di cache](/help/assets/optimize-at-edge/cloudfront-cache-policy-ttl.png)

   * In **Impostazioni della chiave della cache** > **Intestazioni**, includi tutto ciò che era presente nel criterio gestito, aggiungendo `x-edgeoptimize-config` e `x-edgeoptimize-url`.

   ![Intestazioni del criterio di cache](/help/assets/optimize-at-edge/cloudfront-cache-policy-headers.png)

4. Fai clic su **Crea**.

5. Torna al tuo comportamento e associa il criterio appena creato:

   **Navigazione:** Console AWS > CloudFront > Distribuzioni > [La tua distribuzione] > Comportamenti

   1. Modifica il comportamento.
   2. In **Chiave della cache e richieste di origine**, seleziona **Criterio di cache**.
   3. Scegli `edgeoptimize-cache` dal menu a discesa.
   4. Fai clic su **Salva modifiche**.

## Passaggio 4: creare la funzione Lambda@Edge (richiesta e risposta di origine)

>[!IMPORTANT]
>Le funzioni Lambda@Edge **devono essere create nell’`us-east-1`area geografica (N. Virginia)**. Si tratta di un requisito di AWS. Anche se la funzione viene creata in `us-east-1`, AWS la replica automaticamente in tutte le posizioni Edge di CloudFront in tutto il mondo, in modo che venga eseguita nella posizione edge più vicina al visualizzatore. Prima di procedere, assicurati di trovarti nell’area `us-east-1` della console AWS.

### Creare la funzione Lambda

**Navigazione:** Console AWS > Lambda

1. Fai clic su **Crea funzione**.

2. Seleziona **Crea da zero**.

3. Configurare:
   * **Nome funzione:** `edgeoptimize-origin`
   * Per tutti gli altri campi, lascia invariati i valori predefiniti.

4. Fai clic su **Crea funzione**.

5. Nell’editor di codice, sostituisci il codice predefinito con il codice presente in [origin-request-response.js](https://github.com/adobe/llmo-code-samples/blob/main/optimize-at-edge/cloudfront/lambda/origin-request-response.js).

6. Fai clic su **Implementa** per salvare il codice.

7. Prendi nota del **nome del ruolo di esecuzione** visualizzato in **Configurazione** > **Autorizzazioni** (ad esempio, `edgeoptimize-origin-role-xxxxx`). Ti servirà nei seguenti passaggi.

### Aggiorna il criterio di attendibilità del ruolo di esecuzione

Il ruolo creato automaticamente considera attendibile solo `lambda.amazonaws.com`. Per Lambda@Edge, devi aggiungere anche `edgelambda.amazonaws.com`.

**Navigazione:** Console AWS > IAM > Ruoli > [il tuo ruolo dal passaggio precedente] > scheda Relazioni di attendibilità

1. Fai clic su **Modifica criterio di attendibilità**.

2. Sostituisci il criterio con il contenuto di [trust-policy.json](https://github.com/adobe/llmo-code-samples/blob/main/optimize-at-edge/cloudfront/lambda/trust-policy.json).

3. Fai clic su **Aggiorna criterio**.

>[!WARNING]
>Per Lambda@Edge è **obbligatoria** l’entità principale di servizio `edgelambda.amazonaws.com`. In sua assenza, CloudFront non può invocare la funzione nelle posizioni Edge.

### Correzione dei criteri di autorizzazione per i registri di CloudWatch

Il ruolo creato automaticamente viene fornito con un criterio `AWSLambdaBasicExecutionRole` configurato per la normale funzione Lambda, in cui l’area geografica e il nome del gruppo di registri per Lambda@Edge sono errati. Devi aggiornarlo.

**Navigazione:** Console AWS > IAM > Ruoli > [il tuo ruolo] > scheda Autorizzazioni > fare clic sul nome del criterio associato (ad esempio, `AWSLambdaBasicExecutionRole-xxxx`)

1. Fai clic su **Modifica**.

2. Sostituisci il criterio con il contenuto di [cloudwatch-policy.json](https://github.com/adobe/llmo-code-samples/blob/main/optimize-at-edge/cloudfront/lambda/cloudwatch-policy.json).

   Nel JSON, sostituisci `ACCOUNT_ID` con il tuo ID account AWS reale (riportato nell’angolo in alto a destra della console AWS) e `FUNCTION_NAME` con il nome della tua funzione Lambda (ad esempio, `edgeoptimize-origin`).

3. Fai clic su **Salva modifiche**.

>[!WARNING]
>L’area geografica dell’ARN deve essere `*` — Lambda@Edge viene eseguito nella posizione edge più vicina al visualizzatore, pertanto i registri vengono scritti in CloudWatch nell’area geografica della posizione edge (ad esempio, `ap-south-1`, `eu-west-1`), non necessariamente `us-east-1`. Il gruppo di registri utilizza un nome con prefisso di area geografica: `/aws/lambda/us-east-1.FUNCTION_NAME`, dove `us-east-1` è sempre l’area geografica propria della funzione.

### Correggi il collegamento dei registri di CloudWatch

Per impostazione predefinita, il collegamento **Visualizza registri CloudWatch** nella console Lambda collega a `/aws/lambda/FUNCTION_NAME` in `us-east-1`, ovvero il gruppo di registro errato per Lambda@Edge. Configurare un gruppo di registro personalizzato in modo che il collegamento punti al percorso corretto.

**Navigazione:** Console AWS > Lambda > [funzione] > Configurazione > Strumenti di monitoraggio e operazioni

1. Fai clic su **Modifica**.

2. In **Gruppo di registro CloudWatch**, seleziona **Personalizzato**.

3. Impostare il nome del gruppo di log personalizzato su `/aws/lambda/us-east-1.edgeoptimize-origin`.

4. In **Autorizzazioni**, lascia la casella di controllo **Aggiungi autorizzazioni richieste** **deselezionata**.

   ![Configurazione gruppo di log personalizzato Lambda](/help/assets/optimize-at-edge/cloudfront-lambda-custom-log-group.png)

5. Fai clic su **Salva**.

>[!NOTE]
>Anche dopo questa correzione, il collegamento **Visualizza registri di CloudWatch** apre il nome corretto del gruppo di registri, ma potrebbe non mostrare dati se ti trovi nell&#39;area sbagliata. I registri Lambda@Edge vengono scritti nell&#39;area Edge che ha fornito la richiesta (ad esempio, `eu-west-1`, `ap-south-1`), non `us-east-1`. Per visualizzare i registri, è comunque necessario passare all’area corretta in CloudWatch.

### Pubblicare una versione

1. Nella pagina della funzione, fai clic su **Azioni** (in alto a destra) > **Pubblica nuova versione**.

2. Aggiungi una descrizione.

3. Fai clic su **Pubblica**.
   ![Pubblicazione lambda](/help/assets/optimize-at-edge/cloudfront-lambda-publish.png)

4. Copia o prendi nota dell’**ARN della funzione** (ti servirà nel passaggio successivo).
   ![ARN di Lambda](/help/assets/optimize-at-edge/cloudfront-lambda-arn.png)

## Passaggio 5: associare le funzioni e i criteri di cache al comportamento

**Navigazione:** Console AWS > CloudFront > Distribuzioni > [La tua distribuzione] > Comportamenti

1. Modifica il comportamento.

2. Se hai creato un nuovo criterio di cache nel passaggio 3 (Scenario C), imposta **Criterio di cache** su `edgeoptimize-cache`.
   ![Criterio di cache](/help/assets/optimize-at-edge/cloudfront-behaviour-cache.png)

3. In **Associazioni della funzione**, configura:

   * **La richiesta del visualizzatore:** `edgeoptimize-routing`
   * **La richiesta di origine:** ARN della funzione nella versione del passaggio 4 (in **Pubblica una versione**)
   * **La risposta di origine:** ARN della funzione nella versione del passaggio 4 (in **Pubblica una versione**)

   ![Configurazione associazioni della funzione](/help/assets/optimize-at-edge/cloudfront-function-association.png)

4. Fai clic su **Salva modifiche**.

## Consenti ottimizzazione in Edge tramite regole firewall (facoltativo)

{{waf-allowlist-setup}}

## Passaggio 6: verificare la configurazione

**1. Test del traffico da bot (deve risultare ottimizzato)**

Invia una richiesta con uno user agent bot agentico. Nella **prima richiesta**, Edge Optimize potrebbe restituire una risposta proxy (non ottimizzata) durante l’elaborazione della pagina e relativa memorizzazione nella cache. Puoi identificarla nell’intestazione `x-edgeoptimize-proxy: 1` della risposta.

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

**4. Verificare il flusso corretto dei registri**

Dopo aver eseguito le richieste di test sopra riportate, verifica che i registri siano scritti sia per la funzione CloudFront che per la funzione Lambda@Edge.

*Registri della funzione CloudFront (`edgeoptimize-routing`)*

**Navigazione:** Console AWS > CloudWatch > Gruppi di registri (in `us-east-1` o nell’area geografica in cui è configurata la distribuzione CloudFront)

1. Cerca un gruppo di registri denominato `/aws/cloudfront/function/edgeoptimize-routing`.
2. Apri il flusso di registro più recente.
3. Per le richieste agentiche, dovresti vedere voci quali:
   * `Adding origin group for userAgent: chatgpt-user`
   * `Routing to Edge Optimize origin for userAgent: chatgpt-user`
4. Per le richieste non agentiche, dovresti vedere:
   * `Routing to Default origin for userAgent: ...`

Puoi anche controllare la scheda **Metriche** in **Console AWS > CloudFront > Funzioni > edgeoptimize-routing** per visualizzare i conteggi delle chiamate e i tassi di errore.

*Registri Lambda@Edge (`edgeoptimize-origin`)*

>[!IMPORTANT]
>I registri Lambda@Edge sono scritti in CloudWatch nell’**area geografica della posizione edge** che ha visualizzato la richiesta, non in `us-east-1`. Controlla CloudWatch nell’area geografica di AWS più vicina alla posizione in cui hai eseguito il comando curl.

**Navigazione:** Console AWS > CloudWatch > Gruppi di registri (assicurati di trovarti nell’area geografica corretta)

1. Cerca un gruppo di registri denominato `/aws/lambda/us-east-1.edgeoptimize-origin`.
2. Apri il flusso di registro più recente.
3. Per le richieste agentiche, dovresti vedere voci quali:
   * `Calling Edge Optimize Origin for agentic requests`: percorso primario
   * `Calling Default Origin in case of failover for agentic requests`: percorso di failover
   * `Failover Triggered for agentic requests`: rilevamento failover risposta di origine

Se il gruppo di registri non è presente, verifica che le autorizzazioni IAM siano state aggiornate correttamente nel passaggio 4. Controlla anche altre aree geografiche vicine di AWS: la posizione Edge che ha visualizzato la richiesta potrebbe essere diversa da quella prevista.

## Risoluzione dei problemi

| Problema | Causa possibile | Soluzione |
|-------|----------------|----------|
| Nessun `x-edgeoptimize-request-id` nella risposta per le richieste agentiche | Il gruppo di origine non viene indirizzato a Edge Optimize | Verifica che `YOUR_DEFAULT_ORIGIN` sia stato sostituito correttamente nel codice della funzione CloudFront (passaggio 2). |
| Errori 403 nelle richieste agentiche | Chiave API non valida o mancante | Controlla il valore dell’intestazione `x-edgeoptimize-api-key` nelle intestazioni personalizzate di origine di Edge Optimize (passaggio 1). |
| Impossibile trovare i registri CloudWatch per Lambda@Edge | Autorizzazioni IAM errate | Verifica che il criterio di autorizzazione dei registri di CloudWatch sia stato aggiornato (passaggio 4). Nota: i registri Lambda@Edge vengono visualizzati nell’area geografica di edge che ha visualizzato la richiesta, non necessariamente `us-east-1`. |
| La cache non rispetta `cache-control: no-store` | Il TTL minimo potrebbe essere troppo elevato | Imposta il TTL minimo su `0` nel tuo criterio di cache (passaggio 3). Se il TTL minimo è già molto breve, questo potrebbe non essere il problema. |
| Traffico regolare (non agentico) interrotto dopo la configurazione | Configurazione errata del criterio di cache | Se hai creato un nuovo criterio di cache (Scenario C), assicurati di aver replicato tutte le impostazioni del criterio gestito originale. |

## Disabilitazione e riabilitazione di Ottimizza in Edge

La funzione Lambda@Edge (`edgeoptimize-origin`) è associata alla richiesta di origine e agli eventi di risposta di origine del comportamento CloudFront. Siccome viene eseguito in linea su ogni richiesta che passa attraverso tale comportamento, sia umana che agentica, un’interruzione di Lambda@Edge influirà su tutto il traffico live, non solo sulle richieste agentiche. Se rilevi un’interruzione Lambda@Edge, rimuovi immediatamente le associazioni della funzione per ripristinare il normale flusso di traffico all’origine predefinita.

### Come rilevare un’interruzione Lambda@Edge

* **Dashboard AWS Service Health**: visita la [Dashboard AWS Service Health](https://health.aws.amazon.com/health/status) per eventuali incidenti attivi che interessano **Amazon CloudFront** o **AWS Lambda**. Un’interruzione globale o regionale riportata qui è il modo più rapido per confermare che il problema riguarda il lato dell’infrastruttura AWS anziché la tua configurazione.
* **Errori Lambda@Edge**: passa a **Console AWS > CloudFront > Monitoraggio > [La tua distribuzione]**. Apri la scheda **Errori Lambda@Edge** per verificare nel grafico degli **Errori di esecuzione** l’eventuale presenza di errori di esecuzione. Se il numero è elevato, Lambda@Edge potrebbe essere inattivo.

### Scollegamento della funzione Lambda@Edge

**Navigazione:** Console AWS > CloudFront > Distribuzioni > [La tua distribuzione] > Comportamenti

1. Fai clic su **Modifica** sul tuo comportamento.

2. Scorri verso il basso fino alla sezione **Associazioni della funzione**.

3. Imposta le seguenti associazioni su **Nessuna associazione**:

   | Evento | Cambiare in |
   |---|---|
   | Richiesta del visualizzatore | Nessuna associazione |
   | Richiesta di origine | Nessuna associazione |
   | Risposta di origine | Nessuna associazione |

   ![Configurazione associazioni della funzione](/help/assets/optimize-at-edge/cloudfront-no-function-association.png)

4. Fai clic su **Salva modifiche**.

5. Attendi il completamento della distribuzione di CloudFront. Lo stato cambia da **Implementazione** alla data dell’ultima modifica, in genere entro pochi minuti.

Al termine dell’implentazione, tutti gli indirizzamenti del traffico arrivano direttamente all’origine predefinita. Nessuna configurazione viene eliminata: la funzione Lambda e le relative associazioni possono essere ripristinate in qualsiasi momento.

### Riassociazione della funzione Lambda@Edge

**Navigazione:** Console AWS > CloudFront > Distribuzioni > [La tua distribuzione] > Comportamenti

1. Fai clic su **Modifica** sul tuo comportamento.

2. Scorri verso il basso fino alla sezione **Associazioni della funzione**.

3. Ripristina le associazioni:

   | Evento | Impostare su |
   |---|---|
   | Richiesta del visualizzatore | `edgeoptimize-routing` (funzione CloudFront) |
   | Richiesta di origine | ARN Lambda nella versione del passaggio 4 |
   | Risposta di origine | ARN Lambda nella versione del passaggio 4 |

   Utilizza l’**ARN della funzione** nella versione annotata nel passaggio 4 (in **Pubblica una versione**).

   ![Configurazione associazioni della funzione](/help/assets/optimize-at-edge/cloudfront-function-association.png)

4. Fai clic su **Salva modifiche**.

5. Attendi il completamento della distribuzione, quindi verifica che le richieste agentiche restituiscano l’intestazione `x-edgeoptimize-request-id` come descritto nel passaggio 6.

{{return-to-overview}}
