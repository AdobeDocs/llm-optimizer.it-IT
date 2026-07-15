---
title: Inoltro dei registri - Akamai
description: Scopri come inoltrare i registri CDN da Akamai al bucket S3 di Adobe per la raccolta di dati sul traffico da IA agentica in LLM Optimizer.
feature: Agentic Traffic
autotag-review: '2026-07-15T17:40:31.728Z'
TQID: 'https://experienceleague.adobe.com/I-FHVzjiUvTwncGnfR2aAV2lOgtyltvac8aRN5LEQoE'
product_v2:
  - id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2:
  - id: d1956731-2adb-4bb7-8301-2b239254ac72
  - id: e0828736-236a-487b-a478-5a635455eadc
subfeature_v2:
  - id: d23587d6-14d6-4e3f-9ee1-cc18623832e1
  - id: e06fae5f-830b-4222-a469-b5e148d36465
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: d3cdead0-685a-4489-9250-4bb709942f66
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 2705cf26faea9c09817bbdcec4b4c531552df7ba
workflow-type: tm+mt
source-wordcount: 612
ht-degree: 93%

---


# Inoltro dei registri: Akamai {#log-forwarding-akamai}

Questa pagina spiega come inoltrare i registri CDN da Akamai al bucket S3 di Adobe per la raccolta dati relativa al traffico da IA agentica. Per effettuare l’onboarding in LLM Optimizer, utilizza la pagina Configurazione CDN di LLM Optimizer. Al termine del processo di onboarding, segui i passaggi descritti in questa pagina per configurare l’inoltro dei registri nel Pannello di controllo di Akamai.

## Passaggio 1: eseguire l’onboarding in LLM Optimizer {#step-1}

Nella pagina LLM Optimizer [https://llmo.now/](https://llmo.now/):

1. Vai alla **Dashboard Configurazione cliente**.

   ![Pulsante Configurazione](/help/overview/assets/log-forwarding/common/config-button.png)

1. Fai clic sulla scheda **Configurazione CDN**.

   ![Scheda Configurazione CDN](/help/overview/assets/log-forwarding/common/cdn-config-tab.png)

1. Fai clic su **Inizia**.

   <!--![Onboard CDN button](/help/overview/assets/log-forwarding/common/onboard-cdn-button.png)-->

1. Accanto ad **Attiva analisi traffico IA**, fai clic su **Configura**.

   ![Configura](/help/overview/assets/log-forwarding/common/configure.png)

1. Seleziona **Akamai (BYOCDN)**.

   ![Seleziona Akamai](/help/overview/assets/log-forwarding/akamai/akamai-select.png)

1. Fai clic su **Esegui onboarding**.

   <!--![Onboard button](/help/overview/assets/log-forwarding/common/onboard-button.png)-->

## Passaggio 2: creare un flusso in Akamai {#step-2}

Nel pannello di controllo di Akamai [https://control.akamai.com/](https://control.akamai.com/), segui i passaggi della documentazione ufficiale di Akamai per [creare un flusso](https://techdocs.akamai.com/datastream2/docs/create-stream).

## Passaggio 3: scegliere i parametri dei dati {#step-3}

Dopo aver creato il flusso, nel Pannello di controllo di Akamai fare clic su **Avanti** per passare alla scheda **Set di dati**. Segui i passaggi della documentazione ufficiale di Akamai per scegliere i [parametri dei dati](https://techdocs.akamai.com/datastream2/docs/choose-data-parameters). Saranno necessari i seguenti campi dalla configurazione di LLM Optimizer:

![Campi di configurazione di LLMO](/help/overview/assets/log-forwarding/akamai/akamai-llmo-config-fields.png)

La mappatura deve essere la seguente:

* **Informazioni di registro**
reqTimeSec -> Orario della richiesta
* **Dati geografici**
country -> Paese/Area geografica
* **Dati di scambio messaggi**
reqHost -> Host della richiesta
reqPath -> Percorso della richiesta
queryStr -> Stringa di query (facoltativo)
reqMethod -> Metodo di richiesta
ua -> User-Agent
statusCode -> Codice di stato HTTP
rspContentType -> Risposta Content-Type
* **Dati intestazione richiesta**
referer -> Referer
* **Dati prestazioni di rete**
timeToFirstByte -> Time to first byte

>[!NOTE]
>
>Il parametro `queryStr` è facoltativo. È possibile ometterlo se la stringa di query include informazioni PII.

I campi del set di dati Akamai (inclusi gli ID) sono i seguenti:

1100, # reqTimeSec -> Orario della richiesta
2012, # country -> Paese
1011, # reqHost -> Host della richiesta
1013, # reqPath -> Percorso della richiesta
2009, # queryStr -> Stringa di query (facoltativo)
1012, # reqMethod -> Metodo di richiesta
1017, # ua -> User-Agent
1008, # statusCode -> Codice di stato HTTP
1032, # referer -> Referer
1016, # rspContentType -> Risposta Content-Type
2025  # timeToFirstByte -> Time to first byte

## Passaggio 4: configurare la destinazione {#step-4}

Dopo aver creato i flussi di dati e scelto i parametri, devi configurare la destinazione. Per configurare la destinazione, segui questi passaggi:

1. In **Destinazione**, seleziona **S3**.
2. In **Nome**, immetti una descrizione leggibile per la destinazione.
3. In **Bucket**, copia il **Nome del bucket** dalla pagina di configurazione di LLM Optimizer.

   ![Nome del bucket](/help/overview/assets/log-forwarding/common/bucket-name.png)

4. In **Percorso della cartella**, copia il **Percorso** dalla pagina di configurazione di LLM Optimizer.

   ![Configurazione del percorso](/help/overview/assets/log-forwarding/akamai/akamai-path-config.png)

5. In **Area geografica**, copia l’**area geografica** dalla pagina di configurazione di LLM Optimizer.

   <!--![Region](/help/overview/assets/log-forwarding/common/region.png)-->

6. In **ID chiave di accesso** e **Chiave di accesso segreta**, copia entrambi i valori dalla pagina di configurazione di LLM Optimizer.

   ![Chiavi di accesso](/help/overview/assets/log-forwarding/common/access-keys.png)

7. Fai clic su **Convalida e salva** per convalidare la connessione alla destinazione e salvare i dettagli forniti. Come parte di questo processo di convalida, il sistema utilizza l’identificatore della chiave di accesso e la chiave di accesso segreta forniti per creare un file di verifica nella tua cartella S3, con una marca temporale nel nome del file nel formato `Akamai_access_verification_[TimeStamp].txt`. Puoi visualizzare questo file solo se il processo di convalida è riuscito e disponi dell’accesso al bucket Amazon S3 e alla cartella a cui stai tentando di inviare i registri.

8. Nel menu **Opzioni di consegna**, modifica il campo **Nome file** come segue:

   a. Cambia il **prefisso**. Copia il valore dalla pagina di configurazione di LLM Optimizer in **Prefisso file di registro**:

   ```
   {%Y}-{%m}-{%d}T{%H}:{%M}:{%S}.000
   ```

   b. Cambia il **suffisso**. Copia il valore dalla pagina di configurazione di LLM Optimizer in **Suffisso file di registro**.

9. Cambia la **frequenza di push**. Copia il valore dalla pagina di configurazione di LLM Optimizer in **Intervallo di registro**.

   ![Intervallodi registro](/help/overview/assets/log-forwarding/akamai/akamai-log-interval.png)

10. Fai clic su **Avanti** per completare il processo.

Prima della convalida finale, la configurazione dovrebbe essere simile a questo esempio:

![Convalida configurazione](/help/overview/assets/log-forwarding/akamai/akamai-validation.png)
