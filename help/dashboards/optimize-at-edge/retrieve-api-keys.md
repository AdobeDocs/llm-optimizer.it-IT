---
title: Recuperare le chiavi API
description: Come recuperare da LLM Optimizer le chiavi API di ottimizzazione di Edge per produzione e staging.
feature: Opportunities
autotag-review: '2026-05-15T17:58:10.897Z'
TQID: 'https://experienceleague.adobe.com/4R-cx6wv75Oowj9ZvEPGCzQbQBSoppgDuI5Ut1IbObA'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: d1956731-2adb-4bb7-8301-2b239254ac72
subfeature_v2: id: d23587d6-14d6-4e3f-9ee1-cc18623832e1
topic_v2: id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
source-git-commit: 564171851fdccee43afd233da143d66182464889
workflow-type: tm+mt
source-wordcount: 337
ht-degree: 1%

---


# Recuperare le chiavi API

Prima di configurare la rete CDN, recupera le chiavi API di Edge Optimize dall’interfaccia utente di LLM Optimizer. È necessaria una chiave API **production** per il traffico live. Facoltativamente, puoi anche recuperare una chiave API **staging** per testare prima il routing su un nome host di staging.

## Chiave API di produzione

1. In LLM Optimizer, apri **Configurazione cliente** e seleziona la scheda **Configurazione CDN**.

   ![Passa a Configurazione cliente](/help/assets/optimize-at-edge/prereq-customer-config-nav.png)

2. Individua la sezione **Distribuire le ottimizzazioni agli agenti di IA**. Selezionare la casella di controllo **Abilita motore di ottimizzazione**.

   ![Distribuzione ottimizzazioni agli agenti di IA - in sospeso](/help/assets/optimize-at-edge/byocdn-deploy-optimizations-pending.png)

3. Nella finestra di dialogo di conferma, seleziona **Abilita**.

   ![Abilita la finestra di dialogo di conferma del motore di ottimizzazione](/help/assets/optimize-at-edge/byocdn-enable-optimization-engine-dialog.png)

4. Selezionare **Visualizza dettagli**. Nella finestra di dialogo **Dettagli ottimizzazione distribuzione**, copia la **chiave API di produzione** (utilizza **Copia** accanto al campo).

   ![Chiave API di produzione nei dettagli delle ottimizzazioni della distribuzione](/help/assets/optimize-at-edge/byocdn-production-api-key-details.png)

   >[!NOTE]
   >La finestra di dialogo potrebbe indicare che la configurazione non è completa. Questo è previsto fino alla verifica del routing: è comunque possibile copiare la chiave API in modo che il team IT o CDN possa completare la configurazione.

Per assistenza sui passaggi precedenti, contatta il team del tuo account Adobe o `llmo-at-edge@adobe.com`.

## Chiave API di staging (opzionale)

Per convalidare il ciclo di produzione in un ambiente inferiore prima di abilitare il ciclo di produzione, puoi configurare un nome host di staging.

**Requisiti**

* Il nome host dell&#39;area di gestione temporanea deve trovarsi nello **stesso dominio registrabile** della produzione (ad esempio, `https://staging.example.com` quando la produzione è `https://www.example.com`).
* Solo **un** dominio di gestione temporanea per sito. Una volta salvato, non è possibile modificarlo senza contattare Adobe.

**Passaggi**

1. In LLM Optimizer, apri **Configurazione cliente** e seleziona la scheda **Configurazione CDN**.
2. In **Distribuisci ottimizzazioni agli agenti di IA**, selezionare **Aggiungi dominio stage** (o **Dominio stage** se è già configurato un dominio di gestione temporanea).
3. Immetti l&#39;URL di gestione temporanea completo, incluso `https://`, e seleziona **Imposta dominio**.
4. Copia la chiave API **staging** dalla finestra di dialogo di conferma.

   ![Chiave API del dominio di gestione temporanea](/help/assets/optimize-at-edge/byocdn-staging-domain-api-key.png)

Distribuisci le stesse regole di routing nell’ambiente di staging utilizzando la chiave API di staging.

Se hai bisogno di aiuto, contatta `llmo-at-edge@adobe.com`.

## Passaggi successivi

Dopo aver recuperato le chiavi API, torna alla [guida all&#39;installazione della rete CDN](/help/dashboards/optimize-at-edge/overview.md#cdn-configuration-guides) per configurare il routing.
