---
title: Inoltro registro - Cloudflare
description: Scopri come inoltrare i registri CDN da Cloudflare al bucket S3 di Adobe per la raccolta di dati sul traffico agente in LLM Optimizer.
feature: Agentic Traffic
source-git-commit: b590cd14ba7d64e56a6c972fd6090e2df9de58f6
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---


# Inoltro registro: Cloudflare {#log-forwarding-cloudflare}

Questa pagina illustra come inoltrare i registri CDN da Cloudflare al bucket S3 di Adobe per la raccolta di dati sul traffico agente. Per effettuare l’onboarding in LLM Optimizer, utilizza la pagina Configurazione CDN di LLM Optimizer. Al termine del processo di onboarding, segui i passaggi descritti in questa pagina per configurare l’inoltro dei registri nella console della dashboard di Cloudflare.

## Passaggio 1: onboarding in LLM Optimizer {#step-1}

Nella pagina LLM Optimizer [https://llmo.now/](https://llmo.now/):

1. Vai a **Dashboard configurazione cliente**.

   ![Pulsante Configurazione](/help/overview/assets/log-forwarding/common/config-button.png)

1. Fare clic sulla scheda **Configurazione CDN**.

   ![Scheda Configurazione CDN](/help/overview/assets/log-forwarding/common/cdn-config-tab.png)

1. Fai clic su **Inizia**.

   <!-- ![Onboard CDN button](/help/overview/assets/log-forwarding/common/onboard-cdn-button.png) -->

1. Accanto a **Attiva analisi traffico IA**, fai clic su **Configura**.

   ![Configura](/help/overview/assets/log-forwarding/common/configure.png)

1. Selezionare **Cloudflare (BYOCDN)**.

   ![Seleziona Cloud Flare](/help/overview/assets/log-forwarding/cloudflare/cloudflare-select.png)

1. Fare clic su **Onboard**.

   <!-- ![Onboard button](/help/overview/assets/log-forwarding/common/onboard-button.png)-->

## Passaggio 2: creare un processo Logpush in Cloudflare {#step-2}

Nel [dashboard Cloudflare](https://dash.cloudflare.com/login), eseguire la procedura seguente:

1. Vai alla pagina **Logpush** al livello **Dominio (zona)**.
1. Selezionare **Crea un processo Logpush**.
1. In **Seleziona una destinazione**, scegli **Amazon S3**.
1. Immettere le seguenti informazioni sulla destinazione:

   - **Bucket**: nome del bucket S3. Copia il valore dalla pagina Configurazione CDN di LLM Optimizer.

     ![Nome bucket](/help/overview/assets/log-forwarding/common/bucket-name.png)

   - **Percorso**: la posizione del bucket all&#39;interno del contenitore di archiviazione. Copia il valore dalla pagina Configurazione CDN di LLM Optimizer.

     ![Percorso Cloudflare](/help/overview/assets/log-forwarding/cloudflare/cloudflare-path.png)

   - **Organizzare gli accessi nelle sottocartelle giornaliere** (scelta consigliata).

     ![Sottocartelle giornaliere](/help/overview/assets/log-forwarding/cloudflare/cloudflare-daily-subfolders.png)

   - **Area bucket**: copiare il valore dalla pagina Configurazione CDN di LLM Optimizer.

     <!-- ![Region](/help/overview/assets/log-forwarding/cloudflare/cloudflare-region.png)-->

   - Se la crittografia lato server non è necessaria, lasciare deselezionata questa opzione.

   Dopo aver completato i passaggi precedenti, seleziona **Continua**.

1. Per provare la proprietà, Cloudflare invierà un file alla destinazione designata. Per trovare il token, fare clic sul pulsante **Apri** nella scheda **Panoramica** del file di verifica della proprietà. Copia il token di proprietà dalla pagina di configurazione CDN di LLM Optimizer, quindi incollalo nel dashboard di Cloudflare per verificare l’accesso al bucket. Immettere il token di proprietà e selezionare **Continua**.

   <!--![Ownership token](/help/overview/assets/log-forwarding/cloudflare/cloudflare-ownership-token.png)-->

1. Seleziona il set di dati **Richieste HTTP** da inviare al servizio di archiviazione.

1. Configurare il processo Logpush:

   - Immetti il **nome processo**.

   - In **Invia i campi seguenti**, vedi i valori nella pagina di configurazione di LLM Optimizer.

     ![Campi Logpush](/help/overview/assets/log-forwarding/cloudflare/cloudflare-logpush-fields.png)

   - **Formato registro**: JSON.

     <!--![JSON format](/help/overview/assets/log-forwarding/cloudflare/cloudflare-json-format.png)-->

1. In **Opzioni avanzate**:

   - Scegliere il formato dei campi timestamp nei registri: `RFC3339`.

     ![Formato timestamp](/help/overview/assets/log-forwarding/cloudflare/cloudflare-timestamp-format.png)

   - Per le percentuali di campionamento, selezionare **Tutti i registri**.

     ![Frequenza di campionamento](/help/overview/assets/log-forwarding/cloudflare/cloudflare-sampling-rate.png)

1. Seleziona **Invia** una volta completata la configurazione del processo Logpush.
