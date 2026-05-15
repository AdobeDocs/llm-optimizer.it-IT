---
title: Inoltro log - Imperva
description: Scopri come inoltrare i registri CDN da Imperva al bucket S3 di Adobe per la raccolta di dati sul traffico agente in LLM Optimizer.
feature: Agentic Traffic
autotag-review: '2026-05-15T17:52:22.260Z'
TQID: 'https://experienceleague.adobe.com/y2ticpRCNZjPYJ6wHg-V3QWxBnGF--mQfqGBYjVjKXY'
product_v2:
  - id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2:
  - id: d1956731-2adb-4bb7-8301-2b239254ac72
subfeature_v2:
  - id: d23587d6-14d6-4e3f-9ee1-cc18623832e1
topic_v2:
  - id: d3cdead0-685a-4489-9250-4bb709942f66
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
source-git-commit: 564171851fdccee43afd233da143d66182464889
workflow-type: tm+mt
source-wordcount: 352
ht-degree: 4%

---


# Inoltro log: Imperva {#log-forwarding-imperva}

Questa guida spiega come inoltrare i registri CDN da Imperva al bucket S3 di Adobe per la raccolta di dati sul traffico agente. Per effettuare l’onboarding in LLM Optimizer, utilizza la pagina Configurazione CDN di LLM Optimizer. Al termine del processo di onboarding, segui i passaggi descritti in questa pagina per configurare l’inoltro dei registri dalla console web Imperva.

## Passaggio 1: onboarding in LLM Optimizer {#step-1}

Nella pagina LLM Optimizer [https://llmo.now/](https://llmo.now/):

1. Vai a **Configurazione**.

   ![Pulsante Configurazione](/help/overview/assets/log-forwarding/common/config-button.png)

1. Fare clic sulla scheda **Configurazione CDN**.

   ![Scheda Configurazione CDN](/help/overview/assets/log-forwarding/common/cdn-config-tab.png)
1. Fai clic su **Inizia**.
1. Accanto a **Attiva analisi traffico IA**, fai clic su **Configura**.

   ![Configura](/help/overview/assets/log-forwarding/common/configure.png)
1. Selezionare **Imperva (BYOCDN)**.

   ![Seleziona Imperva](/help/overview/assets/log-forwarding/imperva/imperva-select.png)
1. Fare clic su **Onboard**.

## Passaggio 2: configurare l’inoltro dei registri a Imperva {#step-2}

Nella [console Imperva](https://my.imperva.com):

>[!NOTE]
>
>I registri devono essere inviati ogni giorno.

1. Accedi al tuo account Imperva all&#39;indirizzo [https://my.imperva.com](https://my.imperva.com).

2. Nella barra laterale, vai a **Registri** > **Configurazione registro** (o **Integrazione registro**).

3. Selezionare **Amazon S3 ARN** come tipo di connessione (destinazione log).

4. Immetti le seguenti informazioni:

   | Campo | Descrizione | Nota |
   |---|---|---|
   | **Nome connessione** | Un nome descrittivo per la connessione (ad esempio, registri di produzione S3). È possibile rinominare l&#39;impostazione predefinita. | |
   | **Percorso** | Percorso della cartella in cui verranno archiviati i file di registro. Utilizza il formato `<Amazon S3 bucket name>/<log folder>`. Ad esempio: `MyBucket/MyImpervaLogFolder`. | `Amazon S3 bucket name` è il **nome bucket** dalla pagina di configurazione di LLM Optimizer. ![Nome bucket](/help/overview/assets/log-forwarding/imperva/imperva-bucket-name.png) La cartella di registro è **Percorso** dalla pagina di configurazione di LLM Optimizer. ![Percorso](/help/overview/assets/log-forwarding/imperva/imperva-path.png) |

5. Fare clic su **Verifica connessione**. Imperva esegue un test completo in cui un file di test (nessun dato reale) viene inviato alla cartella designata e quindi rimosso al termine del trasferimento.

   - **Disponibile** — i dettagli di archiviazione sono validi. È possibile configurare i registri per utilizzare questa connessione.
   - **Non definito** — mancano i dettagli richiesti o il test non è riuscito.

6. Fai clic su **Salva** per memorizzare la configurazione.

7. Configura le opzioni di registro (tipi di registro, livello di registro, formato, compressione) e **Livelli di registro**. Puoi ottenere i valori dalla pagina di configurazione di LLM Optimizer.

   | Campo | Nota |
   |---|---|
   | Modalità di integrazione del registro | ![Modalità di integrazione registro](/help/overview/assets/log-forwarding/imperva/imperva-log-integration-mode.png) |
   | Metodo di consegna | ![Metodo di consegna](/help/overview/assets/log-forwarding/imperva/imperva-delivery-method.png) |
   | Tipi di registro | ![Tipi di registro](/help/overview/assets/log-forwarding/imperva/imperva-log-types.png) |
   | Livello di registro | ![Livello di registro](/help/overview/assets/log-forwarding/imperva/imperva-log-level.png) |
   | Formato | ![Formato](/help/overview/assets/log-forwarding/imperva/imperva-format.png) |
   | Comprimi registri | ![Comprimi registri](/help/overview/assets/log-forwarding/imperva/imperva-compress-logs.png) |
