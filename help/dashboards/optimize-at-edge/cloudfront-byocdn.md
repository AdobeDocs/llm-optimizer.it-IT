---
title: Ottimizza in Edge - CloudFront (BYOCDN)
description: Scopri come configurare CloudFront BYOCDN per ottimizzare in Edge in LLM Optimizer.
feature: Opportunities
source-git-commit: 1253d0f0a58f6523699c52fbfab23028dc469c82
workflow-type: tm+mt
source-wordcount: '2228'
ht-degree: 1%

---


# CloudFront (BYOCDN)

Questa configurazione indirizza il traffico agente (richieste da bot di IA e agenti utente LLM) al servizio back-end Edge Optimize (`live.edgeoptimize.net`). I visitatori umani e i bot SEO continuano a essere serviti dalla tua origine come al solito. Per verificare la configurazione, al termine dell&#39;installazione, cercare l&#39;intestazione `x-edgeoptimize-request-id` nella risposta.

**Prerequisiti**

Prima di configurare la configurazione CloudFront, assicurati di disporre di:

* Una distribuzione CloudFront esistente che serve il sito web.
* Le autorizzazioni IAM di AWS per creare funzioni Lambda, ruoli IAM, distribuzioni CloudFront e criteri di cache.
* Processo di onboarding in LLM Optimizer completato.
* Inoltro del registro CDN a LLM Optimizer completato.
* Chiave API di ottimizzazione Edge recuperata dall’interfaccia utente di LLM Optimizer.

{{retrieve-byocdn-api-key}}

**Passaggio 1: creare l&#39;origine di Edge Optimize**

**Navigazione:** Console AWS > CloudFront > Distribuzioni > [Distribuzione] > Scheda Origini

1. Fare clic su **Crea origine**.

2. Configura l’origine:
   * **Dominio di origine:** `live.edgeoptimize.net`
   * **Nome:** `EdgeOptimize_Origin`

3. Lascia tutti gli altri campi con i loro valori predefiniti.

4. Aggiungi intestazioni personalizzate:

   | Intestazione | Valore |
   |--------|-------|
   | `x-edgeoptimize-api-key` | Chiave API |
   | `x-forwarded-host` | `www.example.com` |

   Sostituisci `www.example.com` con il tuo dominio sito Web effettivo e `Your API key` con la chiave API Edge Optimize fornita dal tuo rappresentante Adobe.

5. Fare clic su **Crea origine**.

![Creazione origine Cloudfront](/help/assets/optimize-at-edge/cloudfront-origin-creation.png)

**Passaggio 2: crea funzione di richiesta visualizzatore**

**Navigazione:** Console AWS > CloudFront > Funzioni

1. Fare clic su **Crea funzione**.

2. Configurare:
   * **Nome:** `edgeoptimize-routing`
   * **Runtime:** `cloudfront-js-2.0`

3. Sostituisci il codice predefinito con il codice di [viewer-request.js](https://github.com/adobe-rnd/llmo-edge-optimize-samples/blob/main/cloudfront/cloudfront-function/viewer-request.js).

   Prima di pubblicare, personalizza i seguenti valori nel codice:

   * `YOUR_DEFAULT_ORIGIN` — Sostituisci con il nome dell&#39;origine predefinita esistente (disponibile in CloudFront > Distribuzioni > [Distribuzione] > scheda Origini).
   * `TARGETED_PATHS` — Imposta su `null` per eseguire il targeting di tutte le pagine HTML o su un array di percorsi specifici, ad esempio `['/', '/products', '/about']`.

4. Fai clic su **Salva modifiche** > **Funzione di pubblicazione**.

![Creazione funzione Cloudfront](/help/assets/optimize-at-edge/cloudfront-function-creation.png)


**Passaggio 3: configurare i criteri della cache**

**Navigazione:** Console AWS > CloudFront > Distribuzioni > [Distribuzione] > Comportamenti

Controlla i criteri della cache attualmente associati al tuo comportamento. Fai clic su **Modifica** sul comportamento e controlla la sezione **Chiave cache e richieste origine** per identificare lo scenario:

* **Scenario A (legacy):** è selezionato un pulsante di opzione con l&#39;etichetta **Impostazioni cache legacy**. Non esiste un elenco a discesa del nome del criterio, ma vengono visualizzate le impostazioni TTL e di intestazione in linea.
* **Scenario B (criterio personalizzato):** è selezionato **Criterio cache** con un nome di criterio creato da te o dal tuo team (non un criterio fornito da AWS).
* **Scenario C (criteri gestiti):** sono selezionati **Criteri cache** con un nome fornito da AWS, ad esempio `CachingOptimized`, `CachingDisabled` o `CachingOptimizedForUncompressedObjects`. Impossibile modificarli.

**Scenario A: impostazioni cache legacy**

Se il comportamento utilizza le impostazioni della cache legacy:

1. In **Richieste chiave cache e origine**, verranno selezionate **Impostazioni cache legacy**.

2. Aggiungi `x-edgeoptimize-config` e `x-edgeoptimize-url` all&#39;elenco consentiti **Intestazioni**:

   * Selezionare **Includi le intestazioni seguenti** dal menu a discesa.
   * Aggiungi `x-edgeoptimize-config` e `x-edgeoptimize-url`.
     ![Cache Cloudfront Legacy](/help/assets/optimize-at-edge/cloudfront-cache-policy-legacy.png)

   Se hai già selezionato **Tutti** nel menu a discesa Intestazioni, salta questo passaggio: tutte le intestazioni vengono inoltrate automaticamente all&#39;origine.

3. Controlla l&#39;impostazione **Object caching**:

   * Se è impostato su **Personalizza**, è consigliabile impostare **TTL minimo** su `0`. Tuttavia, se il TTL minimo corrente è già molto breve, potrebbe non essere necessario modificarlo.
   * Se è impostato su **Usa intestazioni cache di origine**, non è necessaria alcuna modifica.

4. Fai clic su **Salva modifiche**.

**Scenario B: non legacy con criteri di cache personalizzati**

Se il tuo comportamento utilizza già un criterio di cache personalizzato (uno creato dall’utente e non un criterio gestito da AWS):

**Navigazione:** Console AWS > CloudFront > Criteri > Cache

1. Fai clic sul criterio esistente.

2. Fai clic su **Modifica**.

3. È consigliabile impostare **TTL minimo** su `0`. Tuttavia, se il TTL minimo corrente è già molto breve, potrebbe non essere necessario modificarlo.
   ![Impostazioni TTL criteri cache](/help/assets/optimize-at-edge/cloudfront-cache-policy-ttl.png)

4. In **Impostazioni chiave cache** > **Intestazioni**, insieme alle inclusioni esistenti, aggiungi `x-edgeoptimize-config` e `x-edgeoptimize-url`.
   ![Intestazioni criteri cache](/help/assets/optimize-at-edge/cloudfront-cache-policy-headers.png)

5. Fai clic su **Salva modifiche**.

**Scenario C: non legacy con criteri di cache gestiti (AWS)**

Se il tuo comportamento utilizza un criterio di cache gestita di AWS (ad esempio, `CachingOptimized`), non puoi modificarlo. Devi creare un nuovo criterio di cache personalizzato che replichi le impostazioni esistenti dei criteri gestiti e aggiunga le intestazioni Edge Optimize in alto.

**Parte 1: annota le impostazioni correnti dei criteri della cache gestita**

**Navigazione:** Console AWS > CloudFront > Criteri > Cache

1. Trovare e fare clic sul criterio della cache gestita attualmente associato al comportamento (ad esempio, `CachingOptimized`).

2. Prendi nota di tutte le impostazioni esistenti:
   * TTL minimo, TTL massimo, TTL predefinito
   * Intestazioni incluse nella chiave della cache
   * Cookie inclusi nella chiave della cache
   * Stringhe di query incluse nella chiave della cache
   * Supporto per compressione (Gzip, Brotli)

**Parte 2: crea un nuovo criterio di cache personalizzato con le stesse impostazioni + Configurazione ottimizzazione Edge**

**Navigazione:** Console AWS > CloudFront > Criteri > Cache

1. Fare clic su **Crea criterio cache**.

2. **Nome:** `edgeoptimize-cache`

   ![Nome criteri cache](/help/assets/optimize-at-edge/cloudfront-cache-policy-name.png)

3. Replicare tutte le impostazioni indicate nella parte 1, con le seguenti modifiche:

   * È consigliabile impostare **TTL minimo** su `0`. Tuttavia, se il TTL minimo corrente è già molto breve, potrebbe non essere necessario modificarlo.

   ![Impostazioni TTL criteri cache](/help/assets/optimize-at-edge/cloudfront-cache-policy-ttl.png)

   * In **Impostazioni chiave cache** > **Intestazioni**, includi tutto ciò che aveva il criterio gestito, quindi aggiungi `x-edgeoptimize-config` e `x-edgeoptimize-url`.

   ![Intestazioni criteri cache](/help/assets/optimize-at-edge/cloudfront-cache-policy-headers.png)

4. Fai clic su **Crea**.

5. Torna al tuo comportamento e associa il criterio appena creato:

   **Navigazione:** Console AWS > CloudFront > Distribuzioni > [Distribuzione] > Comportamenti

   1. Modifica il tuo comportamento.
   2. In **Chiave cache e richieste origine**, selezionare **Criteri cache**.
   3. Scegli `edgeoptimize-cache` dal menu a discesa.
   4. Fai clic su **Salva modifiche**.

**Passaggio 4: creare la funzione Lambda@Edge (richiesta e risposta di origine)**

>[!IMPORTANT]
>Le funzioni Lambda@Edge **devono essere create nell&#39;area `us-east-1` (N. Virginia)**. Questo è un requisito di AWS. Anche se la funzione viene creata in `us-east-1`, AWS la replica automaticamente in tutte le posizioni edge di CloudFront in tutto il mondo, in modo che venga eseguita nella posizione edge più vicina al visualizzatore. Prima di procedere, assicurati di trovarti nell&#39;area `us-east-1` nella console AWS.

**Creare la funzione Lambda**

**Navigazione:** Console AWS > Lambda

1. Fare clic su **Crea funzione**.

2. Seleziona **Autore da zero**.

3. Configurare:
   * **Nome funzione:** `edgeoptimize-origin`
   * Lascia tutti gli altri campi con i loro valori predefiniti.

4. Fare clic su **Crea funzione**.

5. Nell&#39;editor di codice, sostituisci il codice predefinito con il codice di [origin-request-response.js](https://github.com/adobe-rnd/llmo-edge-optimize-samples/blob/main/cloudfront/lambda/origin-request-response.js).

6. Fare clic su **Distribuisci** per salvare il codice.

7. Nota il nome del ruolo di esecuzione **&#x200B;**&#x200B;visualizzato in **Configurazione** > **Autorizzazioni** (ad esempio, `edgeoptimize-origin-role-xxxxx`). È necessario eseguire questa operazione nei passaggi seguenti.

**Aggiorna i criteri di attendibilità del ruolo di esecuzione**

Il ruolo creato automaticamente considera attendibile solo `lambda.amazonaws.com`. Per Lambda@Edge, è necessario aggiungere anche `edgelambda.amazonaws.com`.

**Navigazione:** Console AWS > IAM > Ruoli > [il tuo ruolo del passaggio precedente] > scheda Relazioni di attendibilità

1. Fare clic su **Modifica criterio di attendibilità**.

2. Sostituisci il criterio con il contenuto di [trust-policy.json](https://github.com/adobe-rnd/llmo-edge-optimize-samples/blob/main/cloudfront/lambda/trust-policy.json).

3. Fare clic su **Aggiorna criterio**.

>[!WARNING]
>L&#39;entità servizio `edgelambda.amazonaws.com` è **required** per Lambda@Edge. Senza di esso, CloudFront non può richiamare la funzione nelle posizioni edge.

**Correggi i criteri di autorizzazione per i registri di CloudWatch**

Il ruolo creato automaticamente viene fornito con un criterio `AWSLambdaBasicExecutionRole` configurato per Lambda regolare, che presenta l&#39;area e il nome del gruppo di log errati per Lambda@Edge. Devi aggiornarla.

**Navigazione:** Console AWS > IAM > Ruoli > [ruolo] > scheda Autorizzazioni > fare clic sul nome del criterio associato (ad esempio, `AWSLambdaBasicExecutionRole-xxxx`)

1. Fai clic su **Modifica**.

2. Sostituisci il criterio con il contenuto di [cloudwatch-policy.json](https://github.com/adobe-rnd/llmo-edge-optimize-samples/blob/main/cloudfront/lambda/cloudwatch-policy.json).

   Nel JSON, sostituisci `ACCOUNT_ID` con l&#39;ID account AWS effettivo (riportato nell&#39;angolo in alto a destra della console AWS) e `FUNCTION_NAME` con il nome della funzione Lambda (ad esempio, `edgeoptimize-origin`).

3. Fai clic su **Salva modifiche**.

>[!WARNING]
>L&#39;area nell&#39;ARN deve essere `*`. Lambda@Edge viene eseguito nella posizione perimetrale più vicina al visualizzatore, pertanto i registri vengono scritti in CloudWatch nell&#39;area della posizione perimetrale (ad esempio, `ap-south-1`, `eu-west-1`), non necessariamente `us-east-1`. Il gruppo di log utilizza un nome con prefisso di regione: `/aws/lambda/us-east-1.FUNCTION_NAME`, dove `us-east-1` è sempre l&#39;area principale della funzione.

**Pubblica una versione**

1. Nella pagina della funzione, fai clic su **Azioni** (in alto a destra) > **Pubblica nuova versione**.

2. Aggiungi una descrizione.

3. Fai clic su **Pubblica**.
   ![Pubblicazione lambda](/help/assets/optimize-at-edge/cloudfront-lambda-publish.png)

4. Copiare o annotare la **ARN** della funzione. Ciò sarà necessario nel passaggio successivo.
   ![ARN lambda](/help/assets/optimize-at-edge/cloudfront-lambda-arn.png)

**Passaggio 5: associare le funzioni e i criteri della cache al comportamento**

**Navigazione:** Console AWS > CloudFront > Distribuzioni > [Distribuzione] > Comportamenti

1. Modifica il tuo comportamento.

2. Se hai creato un nuovo criterio cache nel passaggio 3 (Scenario C), imposta **Criterio cache** su `edgeoptimize-cache`.
   ![Criteri cache](/help/assets/optimize-at-edge/cloudfront-behaviour-cache.png)

3. In **Associazioni di funzioni**, configura:

   * **Richiesta visualizzatore:** `edgeoptimize-routing`
   * **Richiesta origine:** ARN funzione con versione dal passaggio 4 (in **Pubblica una versione**)
   * **Risposta origine:** ARN funzione con versione dal passaggio 4 (in **Pubblicare una versione**)

   ![Configurazione associazioni funzioni](/help/assets/optimize-at-edge/cloudfront-function-association.png)

4. Fai clic su **Salva modifiche**.

**Passaggio 6: verifica la configurazione**

**1. Verifica traffico da bot (deve essere ottimizzato)**

Invia una richiesta con un agente utente bot agente. Nella **prima richiesta**, Edge Optimize potrebbe restituire una risposta proxy (non ottimizzata) durante l&#39;elaborazione e la memorizzazione nella cache della pagina. È possibile identificarlo dall&#39;intestazione `x-edgeoptimize-proxy: 1` nella risposta.

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

![Stato routing traffico IA con routing abilitato](/help/assets/optimize-at-edge/byocdn-CDN-traffic-routed-tick.png)

**4. Verifica del corretto flusso dei registri**

Dopo aver eseguito le richieste di test di cui sopra, verifica che i registri vengano scritti sia per la funzione CloudFront che per la funzione Lambda@Edge.

*Registri funzioni CloudFront (`edgeoptimize-routing`)*

**Navigazione:** Console AWS > CloudWatch > Gruppi di registro (in `us-east-1` o nell&#39;area in cui è configurata la distribuzione CloudFront)

1. Cercare un gruppo di log denominato `/aws/cloudfront/function/edgeoptimize-routing`.
2. Apri il flusso di registro più recente.
3. Per le richieste di agenti, dovresti trovare voci quali:
   * `Adding origin group for userAgent: chatgpt-user`
   * `Routing to Edge Optimize origin for userAgent: chatgpt-user`
4. Per le richieste non basate su agenti, consulta:
   * `Routing to Default origin for userAgent: ...`

Puoi anche controllare la scheda **Metriche** in **Console AWS > CloudFront > Funzioni > edgeoptimize-routing** per visualizzare i conteggi delle chiamate e le percentuali di errore.

*Lambda@Edge registri (`edgeoptimize-origin`)*

>[!IMPORTANT]
>I registri Lambda@Edge vengono scritti in CloudWatch nell&#39;**area del percorso Edge** che ha fornito la richiesta, non in `us-east-1`. Controlla CloudWatch nell’area di AWS più vicina a dove hai eseguito il comando curl.

**Navigazione:** Console AWS > CloudWatch > Gruppi di registro (verifica di trovarti nell&#39;area corretta)

1. Cercare un gruppo di log denominato `/aws/lambda/us-east-1.edgeoptimize-origin`.
2. Apri il flusso di registro più recente.
3. Per le richieste di agenti, dovresti trovare voci quali:
   * `Calling Edge Optimize Origin for agentic requests` — percorso primario
   * `Calling Default Origin in case of failover for agentic requests` — percorso di failover
   * `Failover Triggered for agentic requests` - rilevamento failover origine-risposta

Se il gruppo di registro non è presente, verifica che le autorizzazioni IAM siano state aggiornate correttamente nel passaggio 4. Controlla anche le altre aree geografiche vicine di AWS: la posizione Edge in cui è stata inviata la richiesta potrebbe essere diversa da quella prevista.

**Risoluzione dei problemi**

| Problema | Causa possibile | Soluzione |
|-------|----------------|----------|
| Nessun `x-edgeoptimize-request-id` in risposta per le richieste dell&#39;agente | Il gruppo di origine non viene indirizzato ad Edge Optimize | Verificare che `YOUR_DEFAULT_ORIGIN` sia stato sostituito correttamente nel codice della funzione CloudFront (passaggio 2). |
| Errori 403 nelle richieste di agenti | Chiave API non valida o mancante | Controlla il valore dell&#39;intestazione `x-edgeoptimize-api-key` nelle intestazioni personalizzate dell&#39;origine di Edge Optimize (passaggio 1). |
| Impossibile trovare i registri CloudWatch per Lambda@Edge | Autorizzazioni IAM errate | Verifica che i criteri di autorizzazione per i registri di CloudWatch siano stati aggiornati (passaggio 4). Nota: i registri Lambda@Edge vengono visualizzati nell&#39;area Edge che ha fornito la richiesta, non necessariamente `us-east-1`. |
| La cache non rispetta `cache-control: no-store` | Il TTL minimo potrebbe essere troppo alto | Imposta TTL minimo su `0` nei criteri della cache (passaggio 3). Se il TTL minimo è già molto breve, questo potrebbe non essere il problema. |
| Traffico regolare (non agente) interrotto dopo la configurazione | Configurazione errata dei criteri della cache | Se hai creato un nuovo criterio di cache (Scenario C), assicurati di aver replicato tutte le impostazioni dal criterio gestito originale. |

**Disabilitazione e riabilitazione dell&#39;ottimizzazione in Edge**

La funzione Lambda@Edge (`edgeoptimize-origin`) è associata alla richiesta di origine e agli eventi di risposta di origine del comportamento CloudFront. Poiché viene eseguito in linea su ogni richiesta che passa attraverso tale comportamento, sia umana che agentica, un’interruzione di Lambda@Edge influirà su tutto il traffico in tempo reale, non solo sulle richieste agentiche. Se rilevi un’interruzione Lambda@Edge, rimuovi immediatamente le associazioni di funzioni per ripristinare il normale flusso di traffico all’origine predefinita.

**Come rilevare un&#39;interruzione Lambda@Edge**

* **AWS Service Health Dashboard** — Controlla il [AWS Service Health Dashboard](https://health.aws.amazon.com/health/status) per eventuali problemi attivi che interessano **Amazon CloudFront** o **AWS Lambda**. Un’interruzione globale o regionale riportata qui è il modo più veloce per confermare che il problema si trova sul lato dell’infrastruttura AWS anziché nella configurazione.
* **Lambda@Edge errori** — Passa a **Console AWS > CloudFront > Monitoraggio > [Distribuzione]**. Apri la scheda **Lambda@Edge errori** e controlla il grafico **Errori di esecuzione** per verificare la presenza di errori di esecuzione. Se questi valori sono elevati, Lambda@Edge potrebbe essere inattivo.

**Scollegamento della funzione Lambda@Edge**

**Navigazione:** Console AWS > CloudFront > Distribuzioni > [Distribuzione] > Comportamenti

1. Fai clic su **Modifica** sul tuo comportamento.

2. Scorri verso il basso fino alla sezione **Associazioni funzioni**.

3. Imposta le seguenti associazioni su **Nessuna associazione**:

   | Evento | Cambia in |
   |---|---|
   | Richiesta visualizzatore | Nessuna associazione |
   | Richiesta origine | Nessuna associazione |
   | Risposta di origine | Nessuna associazione |

   ![Configurazione associazioni funzioni](/help/assets/optimize-at-edge/cloudfront-no-function-association.png)

4. Fai clic su **Salva modifiche**.

5. Attendi il completamento della distribuzione di CloudFront. Lo stato cambia da **Distribuzione** alla data dell&#39;ultima modifica, in genere entro pochi minuti.

Una volta implementati, tutti i percorsi del traffico arrivano direttamente all’origine predefinita. Non viene eliminata alcuna configurazione; la funzione Lambda e le relative associazioni possono essere ripristinate in qualsiasi momento.

**Nuovo collegamento della funzione Lambda@Edge**

**Navigazione:** Console AWS > CloudFront > Distribuzioni > [Distribuzione] > Comportamenti

1. Fai clic su **Modifica** sul tuo comportamento.

2. Scorri verso il basso fino alla sezione **Associazioni funzioni**.

3. Ripristina le associazioni:

   | Evento | Imposta su |
   |---|---|
   | Richiesta visualizzatore | `edgeoptimize-routing` (funzione CloudFront) |
   | Richiesta origine | ARN Lambda con versione dal passaggio 4 |
   | Risposta di origine | ARN Lambda con versione dal passaggio 4 |

   Utilizza la **funzione ARN** con versione annotata nel passaggio 4 (in **Pubblica una versione**).

   ![Configurazione associazioni funzioni](/help/assets/optimize-at-edge/cloudfront-function-association.png)

4. Fai clic su **Salva modifiche**.

5. Attendi che la distribuzione finisca, quindi verifica che le richieste dell&#39;agente restituiscano l&#39;intestazione `x-edgeoptimize-request-id` come descritto nel passaggio 6.

{{return-to-overview}}
