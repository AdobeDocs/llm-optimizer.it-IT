---
title: Recupero delle chiavi API
description: Come recuperare da LLM Optimizer le chiavi API del servizio Edge Optimize per produzione e staging.
feature: Opportunities
autotag-review: '2026-05-15T17:58:10.897Z'
TQID: 'https://experienceleague.adobe.com/4R-cx6wv75Oowj9ZvEPGCzQbQBSoppgDuI5Ut1IbObA'
product_v2:
  - id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2:
  - id: d1956731-2adb-4bb7-8301-2b239254ac72
subfeature_v2:
  - id: d23587d6-14d6-4e3f-9ee1-cc18623832e1
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
source-git-commit: 564171851fdccee43afd233da143d66182464889
workflow-type: tm+mt
source-wordcount: 337
ht-degree: 100%

---


# Recupero delle chiavi API

Prima di configurare la rete CDN, recupera le chiavi API del servizio Edge Optimize dall’interfaccia di LLM Optimizer. È necessaria una chiave API di **produzione** per il traffico live. Facoltativamente, puoi anche recuperare una chiave API di **staging** per testare prima l’indirizzamento su un nome host di staging.

## Chiave API di produzione

1. In LLM Optimizer, apri **Configurazione cliente** e seleziona la scheda **Configurazione CDN**.

   ![Passa a Configurazione cliente](/help/assets/optimize-at-edge/prereq-customer-config-nav.png)

2. Individua la sezione **Implementare le ottimizzazioni negli agenti IA**. Seleziona la casella di controllo **Abilitare motore di ottimizzazione**.

   ![Implementare le ottimizzazioni negli agenti IA](/help/assets/optimize-at-edge/byocdn-deploy-optimizations-pending.png)

3. Nella finestra di dialogo di conferma, seleziona **Abilita**.

   ![Abilitare la finestra di dialogo di conferma del motore di ottimizzazione](/help/assets/optimize-at-edge/byocdn-enable-optimization-engine-dialog.png)

4. Seleziona **Visualizza dettagli**. Nella finestra di dialogo **Dettagli delle ottimizzazioni dell’implementazione**, copia la **chiave API di produzione** (utilizza **Copia** accanto al campo).

   ![Chiave API di produzione nei Dettagli delle ottimizzazioni dell’implementazione](/help/assets/optimize-at-edge/byocdn-production-api-key-details.png)

   >[!NOTE]
   >La finestra di dialogo potrebbe indicare che la configurazione non è completa. Questo è previsto fino alla verifica dell’indirizzamento: è comunque possibile copiare la chiave API in modo che il team IT o CDN possa completare la configurazione.

Se hai bisogno di assistenza per i passaggi precedenti, contatta il team Adobe Account o `llmo-at-edge@adobe.com`.

## Chiave API di staging (facoltativa)

Per convalidare l’indirizzamento in un ambiente inferiore prima di abilitare l’indirizzamento per la produzione, puoi configurare un nome host di staging.

**Requisiti**

* Il nome host di staging deve trovarsi nello **stesso dominio registrabile** della produzione (ad esempio, `https://staging.example.com` quando la produzione è `https://www.example.com`).
* Deve esserci solo **un** dominio di staging per sito. Una volta salvato, non è possibile modificarlo senza contattare Adobe.

**Passaggi**

1. In LLM Optimizer, apri **Configurazione cliente** e seleziona la scheda **Configurazione CDN**.
2. In **Implementare le ottimizzazioni negli agenti IA**, seleziona **Aggiungi dominio di staging** (o **Dominio staging** se è già configurato un dominio di staging).
3. Immetti l’URL di staging completo, includendo `https://`, e seleziona **Imposta dominio**.
4. Copia la chiave API di **staging** dalla finestra di dialogo di conferma.

   ![Chiave API del dominio di staging](/help/assets/optimize-at-edge/byocdn-staging-domain-api-key.png)

Implementa le stesse regole di indirizzamento nell’ambiente di staging utilizzando la chiave API di staging.

Se hai bisogno di aiuto, contatta `llmo-at-edge@adobe.com`.

## Passaggi successivi

Dopo aver recuperato le chiavi API, torna alla [Guida per la configurazione della rete CDN](/help/dashboards/optimize-at-edge/overview.md#cdn-configuration-guides) per configurare l’indirizzamento.
