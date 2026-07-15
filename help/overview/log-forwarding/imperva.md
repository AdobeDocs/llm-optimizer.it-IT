---
title: Inoltro dei registri - Imperva
description: Scopri come inoltrare i registri CDN da Imperva al bucket S3 di Adobe per la raccolta automatica dei dati sul traffico da IA agentica in LLM Optimizer.
feature: Agentic Traffic
autotag-review: '2026-07-15T17:57:30.264Z'
TQID: 'https://experienceleague.adobe.com/l-DYz7pXzFDqZn1rnZWUOG9PpRqosq00LmGrlsOMqNk'
product_v2:
  - id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2:
  - id: d1956731-2adb-4bb7-8301-2b239254ac72
  - id: ef4e63f5-cb4d-462d-bf9a-1f617edf2a3a
  - id: e0828736-236a-487b-a478-5a635455eadc
subfeature_v2:
  - id: d23587d6-14d6-4e3f-9ee1-cc18623832e1
  - id: dd952468-5202-43af-a365-6e0d2e67a703
  - id: e06fae5f-830b-4222-a469-b5e148d36465
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: d3cdead0-685a-4489-9250-4bb709942f66
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 2705cf26faea9c09817bbdcec4b4c531552df7ba
workflow-type: tm+mt
source-wordcount: 352
ht-degree: 100%

---


# Inoltro registri: Imperva {#log-forwarding-imperva}

Questa guida spiega come inoltrare i registri della CDN da Imperva al bucket S3 di Adobe per la raccolta dei dati sul traffico da IA agentica. Per effettuare l’onboarding in LLM Optimizer, utilizza la pagina Configurazione CDN di LLM Optimizer. Una volta completata la procedura di onboarding, segui i passaggi descritti in questa pagina per configurare l’inoltro dei registri dalla console web di Imperva.

## Passaggio 1: eseguire l’onboarding in LLM Optimizer {#step-1}

Nella pagina LLM Optimizer [https://llmo.now/](https://llmo.now/):

1. Passa a **Configurazione**.

   ![Pulsante Configurazione](/help/overview/assets/log-forwarding/common/config-button.png)

1. Fai clic sulla scheda **Configurazione CDN**.

   ![Scheda Configurazione CDN](/help/overview/assets/log-forwarding/common/cdn-config-tab.png)
1. Fai clic su **Inizia**.
1. Accanto ad **Attiva analisi traffico IA**, fai clic su **Configura**.

   ![Configura](/help/overview/assets/log-forwarding/common/configure.png)
1. Seleziona **Imperva (BYOCDN)**.

   ![Seleziona Imperva](/help/overview/assets/log-forwarding/imperva/imperva-select.png)
1. Fai clic su **Esegui onboarding**.

## Passaggio 2: configurare l’inoltro dei registri in Imperva {#step-2}

Nella [console Imperva](https://my.imperva.com):

>[!NOTE]
>
>I registri devono essere inviati quotidianamente.

1. Accedi al tuo account Imperva all’indirizzo [https://my.imperva.com](https://my.imperva.com).

2. Nella barra laterale, passa a **Logs** (Registri) >**Log Setup** (Configurazione registro, oppure **Log Integration** (Integrazione registro).

3. Seleziona **Amazon S3 ARN** come tipo di connessione (destinazione del registro).

4. Immetti le seguenti informazioni:

   | Campo | Descrizione | Nota |
   |---|---|---|
   | **Nome connessione** | Un nome descrittivo per la connessione (ad esempio, registri S3 di Produzione). È possibile rinominare quello predefinito. | |
   | **Percorso** | Il percorso della cartella in cui verranno memorizzati i file di registro. Utilizza il formato `<Amazon S3 bucket name>/<log folder>`. Ad esempio: `MyBucket/MyImpervaLogFolder`. | `Amazon S3 bucket name` è il **nome bucket** dalla pagina di configurazione di LLM Optimizer. ![Nome bucket](/help/overview/assets/log-forwarding/imperva/imperva-bucket-name.png) La cartella di registro è **Percorso** dalla pagina di configurazione di LLM Optimizer. ![Percorso](/help/overview/assets/log-forwarding/imperva/imperva-path.png) |

5. Fai clic su **Verifica connessione**. Imperva esegue un test completo in cui un file di prova (nessun dato reale) viene inviato alla cartella designata e quindi rimosso al termine del trasferimento.

   - **Disponibile** - i dettagli di archiviazione sono validi. È possibile configurare i registri per utilizzare questa connessione.
   - **Non definito** - Mancano i dettagli richiesti o il test non è riuscito.

6. Fai clic su **Salva** per memorizzare la configurazione.

7. Configura le opzioni di registro (tipi di registro, livello di registro, formato, compressione) e **Livelli di registro**. Puoi ottenere i valori dalla pagina di configurazione di LLM Optimizer.

   | Campo | Nota |
   |---|---|
   | Modalità di integrazione del registro | ![Modalità di integrazione del registro](/help/overview/assets/log-forwarding/imperva/imperva-log-integration-mode.png) |
   | Metodo di consegna | ![Metodo di consegna](/help/overview/assets/log-forwarding/imperva/imperva-delivery-method.png) |
   | Tipi di registro | ![Tipi di registro](/help/overview/assets/log-forwarding/imperva/imperva-log-types.png) |
   | Livello di registro | ![Livello di registro](/help/overview/assets/log-forwarding/imperva/imperva-log-level.png) |
   | Formato | ![Formato](/help/overview/assets/log-forwarding/imperva/imperva-format.png) |
   | Comprimi registri | ![Comprimi registri](/help/overview/assets/log-forwarding/imperva/imperva-compress-logs.png) |
