---
title: Inoltro registro - Akamai
description: Scopri come inoltrare i registri CDN da Akamai al bucket S3 di Adobe per la raccolta di dati sul traffico agente in LLM Optimizer.
feature: Agentic Traffic
source-git-commit: b590cd14ba7d64e56a6c972fd6090e2df9de58f6
workflow-type: tm+mt
source-wordcount: '595'
ht-degree: 0%

---


# Inoltro registro: Akamai {#log-forwarding-akamai}

Questa pagina spiega come inoltrare i registri CDN da Akamai al bucket S3 di Adobe per la raccolta di dati sul traffico agente. Per effettuare l’onboarding in LLM Optimizer, utilizza la pagina Configurazione CDN di LLM Optimizer. Al termine del processo di onboarding, segui i passaggi descritti in questa pagina per configurare l’inoltro dei registri nel Pannello di controllo Campaign Akamai.

## Passaggio 1: onboarding in LLM Optimizer {#step-1}

Nella pagina LLM Optimizer [https://llmo.now/](https://llmo.now/):

1. Vai a **Dashboard configurazione cliente**.

   ![Pulsante Configurazione](/help/overview/assets/log-forwarding/common/config-button.png)

1. Fare clic sulla scheda **Configurazione CDN**.

   ![Scheda Configurazione CDN](/help/overview/assets/log-forwarding/common/cdn-config-tab.png)

1. Fai clic su **Inizia**.

   <!--![Onboard CDN button](/help/overview/assets/log-forwarding/common/onboard-cdn-button.png)-->

1. Accanto a **Attiva analisi traffico IA**, fai clic su **Configura**.

   ![Configura](/help/overview/assets/log-forwarding/common/configure.png)

1. Selezionare **Akamai (BYOCDN)**.

   ![Seleziona Akamai](/help/overview/assets/log-forwarding/akamai/akamai-select.png)

1. Fare clic su **Onboard**.

   <!--![Onboard button](/help/overview/assets/log-forwarding/common/onboard-button.png)-->

## Passaggio 2: creare un flusso in Akamai {#step-2}

Nel Pannello di controllo di Akamai [https://control.akamai.com/](https://control.akamai.com/) seguire i passaggi della documentazione ufficiale di Akamai per [creare un flusso](https://techdocs.akamai.com/datastream2/docs/create-stream).

## Passaggio 3: scegliere i parametri dei dati {#step-3}

Dopo aver creato il flusso, nel Pannello di controllo di Akamai fare clic su Avanti per passare alla scheda **Set di dati**. Segui i passaggi della documentazione ufficiale di Akamai per scegliere i [parametri dati](https://techdocs.akamai.com/datastream2/docs/choose-data-parameters). Saranno necessari i seguenti campi dalla configurazione LLM Optimizer:

![Campi di configurazione LLMO](/help/overview/assets/log-forwarding/akamai/akamai-llmo-config-fields.png)

La mappatura deve essere la seguente:

* **Informazioni registro**
reqTimeSec -> Tempo richiesta
* **Dati geografici**
paese -> Paese
* **Dati di scambio messaggi**
reqHost -> Richiedi host
reqPath -> Percorso richiesta
queryStr -> Stringa di query
reqMethod -> Metodo di richiesta
ua -> Agente utente
statusCode -> codice di stato HTTP
rspContentType -> Response Content-Type
* **Dati intestazione richiesta**
referer -> Referer
* **Dati prestazioni di rete**
timeToFirstByte -> Tempo al primo byte

I campi del set di dati Akamai (inclusi gli ID) sono i seguenti:

1100, # reqTimeSec -> Tempo richiesta
2012, # paese -> Paese
1011, # reqHost -> Richiedi host
1013, # reqPath -> Percorso richiesta
2009, # queryStr -> Stringa di query
1012, # reqMethod -> Metodo di richiesta
1017, # ua -> Agente utente
1008, # statusCode -> Codice di stato HTTP
1032, # referer -> Referer
1016, # rspContentType -> Tipo di contenuto risposta
2025 # timeToFirstByte -> Tempo al primo byte

## Passaggio 4: configurare la destinazione {#step-4}

Dopo aver creato i flussi di dati e scelto i parametri necessari per configurare la destinazione. Per configurare la destinazione, effettua le seguenti operazioni:

1. In **Destination**, selezionare **S3**.
2. In **Name** immettere una descrizione leggibile per la destinazione.
3. In **Bucket**, copia il **Nome bucket** dalla pagina di configurazione di LLM Optimizer.

   ![Nome bucket](/help/overview/assets/log-forwarding/common/bucket-name.png)

4. In **Percorso cartella**, copia il **Percorso** dalla pagina di configurazione di LLM Optimizer.

   ![Configurazione del percorso](/help/overview/assets/log-forwarding/akamai/akamai-path-config.png)

5. In **Regione**, copia **Regione** dalla pagina di configurazione di LLM Optimizer.

   <!--![Region](/help/overview/assets/log-forwarding/common/region.png)-->

6. In **ID chiave di accesso** e **Chiave di accesso segreta**, copiare entrambi i valori dalla pagina di configurazione di LLM Optimizer.

   ![Chiavi di accesso](/help/overview/assets/log-forwarding/common/access-keys.png)

7. Fai clic su **Convalida e salva** per convalidare la connessione alla destinazione e salvare i dettagli forniti. Come parte di questo processo di convalida, il sistema utilizza l&#39;identificatore della chiave di accesso e la chiave di accesso segreta forniti per creare un file di verifica nella cartella S3, con una marca temporale nel nome del file nel formato `Akamai_access_verification_[TimeStamp].txt`. Puoi visualizzare questo file solo se il processo di convalida ha esito positivo e hai accesso al bucket Amazon S3 e alla cartella a cui stai tentando di inviare i registri.

8. Nel menu **Opzioni di consegna**, modificare il campo **Nome file** come segue:

   a. Modifica il **prefisso**. Copia il valore dalla pagina di configurazione di LLM Optimizer in **Prefisso file di registro**:

   ```
   {%Y}-{%m}-{%d}T{%H}:{%M}:{%S}.000
   ```

   b. Modifica il **suffisso**. Copiare il valore dalla pagina di configurazione di LLM Optimizer in **Suffisso file di registro**.

9. Modifica la **frequenza push**. Copia il valore dalla pagina di configurazione di LLM Optimizer in **Intervallo di registro**.

   ![Intervallo registro](/help/overview/assets/log-forwarding/akamai/akamai-log-interval.png)

10. Fai clic su **Avanti** per completare il processo.

Prima della convalida finale, la configurazione deve essere simile a questa:

![Convalida configurazione](/help/overview/assets/log-forwarding/akamai/akamai-validation.png)
