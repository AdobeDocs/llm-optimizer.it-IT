---
title: Inoltro dei registri - Cloudflare
description: Scopri come inoltrare i registri CDN da Cloudflare al bucket S3 di Adobe per la raccolta di dati sul traffico da IA agentica in LLM Optimizer.
feature: Agentic Traffic
autotag-review: '2026-07-15T17:45:52.167Z'
TQID: 'https://experienceleague.adobe.com/6D7Xe-ysQOSsNMONyart2HaTfdyQR64l0r3AeFNsOpI'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: d1956731-2adb-4bb7-8301-2b239254ac72id: e0828736-236a-487b-a478-5a635455eadc
subfeature_v2: id: d23587d6-14d6-4e3f-9ee1-cc18623832e1id: e06fae5f-830b-4222-a469-b5e148d36465
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: d3cdead0-685a-4489-9250-4bb709942f66id: e1e0219c-f879-479f-8427-888ed2a6e9c2id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 2705cf26faea9c09817bbdcec4b4c531552df7ba
workflow-type: tm+mt
source-wordcount: 381
ht-degree: 100%

---


# Inoltro dei registri: Cloudflare {#log-forwarding-cloudflare}

Questa pagina spiega come inoltrare i registri CDN da Cloudflare al bucket S3 di Adobe per la raccolta dati relativa al traffico da IA agentica. Per effettuare l’onboarding in LLM Optimizer, utilizza la pagina Configurazione CDN di LLM Optimizer. Al termine del processo di onboarding, segui i passaggi descritti in questa pagina per configurare l’inoltro dei registri nella console della dashboard di Cloudflare.

## Passaggio 1: eseguire l’onboarding in LLM Optimizer {#step-1}

Nella pagina LLM Optimizer [https://llmo.now/](https://llmo.now/):

1. Vai alla **Dashboard Configurazione cliente**.

   ![Pulsante Configurazione](/help/overview/assets/log-forwarding/common/config-button.png)

1. Fai clic sulla scheda **Configurazione CDN**.

   ![Scheda Configurazione CDN](/help/overview/assets/log-forwarding/common/cdn-config-tab.png)

1. Fai clic su **Inizia**.

   <!-- ![Onboard CDN button](/help/overview/assets/log-forwarding/common/onboard-cdn-button.png) -->

1. Accanto ad **Attiva analisi traffico IA**, fai clic su **Configura**.

   ![Configura](/help/overview/assets/log-forwarding/common/configure.png)

1. Seleziona **Cloudflare (BYOCDN)**.

   ![Seleziona Cloudflare](/help/overview/assets/log-forwarding/cloudflare/cloudflare-select.png)

1. Fai clic su **Esegui onboarding**.

   <!-- ![Onboard button](/help/overview/assets/log-forwarding/common/onboard-button.png)-->

## Passaggio 2: creare un processo Logpush in Cloudflare {#step-2}

Nella [dashboard Cloudflare](https://dash.cloudflare.com/login), segui questi passaggi:

1. Vai alla pagina **Logpush** al livello del **Dominio (zona)**.
1. Seleziona **Crea un processo Logpush**.
1. In **Seleziona una destinazione**, scegli **Amazon S3**.
1. Immetti le seguenti informazioni di destinazione:

   - **Bucket**: il nome del bucket S3. Copia il valore dalla pagina Configurazione CDN di LLM Optimizer.

     ![Nome del bucket](/help/overview/assets/log-forwarding/common/bucket-name.png)

   - **Percorso**: la posizione del bucket all’interno del contenitore di archiviazione. Copia il valore dalla pagina Configurazione CDN di LLM Optimizer.

     ![Percorso Cloudflare](/help/overview/assets/log-forwarding/cloudflare/cloudflare-path.png)

   - **Organizzazione degli accessi nelle sottocartelle giornaliere** (scelta consigliata).

     ![Sottocartelle giornaliere](/help/overview/assets/log-forwarding/cloudflare/cloudflare-daily-subfolders.png)

   - **Area bucket**: copia il valore dalla pagina Configurazione CDN di LLM Optimizer.

     <!-- ![Region](/help/overview/assets/log-forwarding/cloudflare/cloudflare-region.png)-->

   - Se la crittografia lato server non è necessaria, lasciare deselezionata questa opzione.

   Dopo aver completato i passaggi precedenti, seleziona **Continua**.

1. Per provare la proprietà, Cloudflare invierà un file alla destinazione designata. Per trovare il token, fai clic sul pulsante **Apri** nella scheda **Panoramica** del file di verifica della proprietà. Copia il token di proprietà dalla pagina di configurazione CDN di LLM Optimizer, quindi incollalo nella dashboard di Cloudflare per verificare l’accesso al bucket. Immetti il token di proprietà e seleziona **Continua**.

   <!--![Ownership token](/help/overview/assets/log-forwarding/cloudflare/cloudflare-ownership-token.png)-->

1. Seleziona il set di dati **Richieste HTTP** da inviare al servizio di archiviazione.

1. Configura il tuo processo Logpush:

   - Inserisci il **nome del processo**.

   - In **Invia i seguenti campi**, visualizza i valori nella pagina di configurazione di LLM Optimizer.

     ![Campi Logpush](/help/overview/assets/log-forwarding/cloudflare/cloudflare-logpush-fields.png)

   - **Formato registro**: JSON.

     <!--![JSON format](/help/overview/assets/log-forwarding/cloudflare/cloudflare-json-format.png)-->

1. In **Opzioni avanzate**:

   - Scegli il formato dei campi marca temporale nei registri: `RFC3339`.

     ![Formato marca temporale](/help/overview/assets/log-forwarding/cloudflare/cloudflare-timestamp-format.png)

   - Per le frequenze di campionamento, seleziona **Tutti i registri**.

     ![Frequenza di campionamento](/help/overview/assets/log-forwarding/cloudflare/cloudflare-sampling-rate.png)

1. Seleziona **Invia** dopo aver completato la configurazione del processo Logpush.
