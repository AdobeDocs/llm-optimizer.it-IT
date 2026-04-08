---
source-git-commit: da789100d814004687de2f46e18a295671dec4b8
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---
# Snippet

## Passaggi per il recupero della chiave API {#retrieve-byocdn-api-key}

**Passaggi per recuperare la chiave API di produzione Edge Optimize:**

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

Inoltre, se hai bisogno di assistenza per i passaggi precedenti, contatta il team del tuo account Adobe o `llmo-at-edge@adobe.com`.

## Chiave API del dominio di staging (opzionale) {#retrieve-staging-edge-optimize-api-key}

Utilizza un nome host di staging quando desideri testare l’ottimizzazione in Edge in un ambiente inferiore prima che il traffico di produzione utilizzi le regole di routing.

**Prerequisiti**

* Il nome host per la gestione temporanea deve appartenere allo **stesso dominio registrabile** del sito di produzione (ad esempio, `https://staging.example.com` quando la produzione è `https://www.example.com`).
* È possibile configurare solo **un** dominio di gestione temporanea per il sito. Una volta salvato, non è possibile modificarlo senza assistenza.

**Passaggi**

1. In LLM Optimizer, apri **Configurazione cliente** e seleziona la scheda **Configurazione CDN**.

2. Nella sezione **Distribuire le ottimizzazioni agli agenti di IA**, selezionare **Aggiungi dominio stage** (o **Dominio stage** se è già configurato un dominio di staging).

3. Nella finestra di dialogo **Dominio stage**, immetti l&#39;URL completo dell&#39;area di gestione temporanea, incluso `https://`, e seleziona **Imposta dominio**.

   ![Finestra di dialogo per l&#39;input del dominio di staging](/help/assets/optimize-at-edge/byocdn-staging-domain-input.png)

4. Conferma il dominio al prompt successivo. Al termine del flusso di lavoro, la finestra di dialogo **Domini fase** mostra il dominio configurato e la relativa **chiave API**. Seleziona **Copia** per copiare la chiave API dell&#39;area di gestione temporanea.

   ![Chiave API del dominio di gestione temporanea](/help/assets/optimize-at-edge/byocdn-staging-domain-api-key.png)

Se hai bisogno di aiuto, contatta `llmo-at-edge@adobe.com`.

## Verifica dello stato di indirizzamento in LLM Optimizer {#verify-routing-status-in-ui}

Lo stato del routing del traffico può essere controllato anche nell’interfaccia utente di LLM Optimizer. Passa a **Configurazione cliente** e seleziona la scheda **Configurazione CDN**.

![Distribuzione delle ottimizzazioni agli agenti di IA - completata](/help/assets/optimize-at-edge/byocdn-CDN-traffic-routed-tick.png)

## Torna alla panoramica {#return-to-overview}

Per ulteriori informazioni su Ottimizza in Edge, tra cui le opportunità disponibili, i flussi di lavoro di ottimizzazione automatica e le domande frequenti, torna alla [Panoramica sull&#39;ottimizzazione in Edge](/help/dashboards/optimize-at-edge/overview.md).
