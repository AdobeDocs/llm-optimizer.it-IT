---
title: Avvio rapido
description: Scopri come effettuare l’onboarding di dominio e nome del tuo brand, attivare la versione di prova da Experience Hub o Experience Cloud e completare la configurazione di Adobe LLM Optimizer.
feature: Quickstart, Onboarding
autotag-review: '2026-05-15T17:56:15.005Z'
TQID: 'https://experienceleague.adobe.com/ShjpvskyOoHqz88gorfhqbIdP5SWT9FJ9SfmjBgEm8E'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: c0713b97-4af8-4c41-b742-5afcc6ced468
subfeature_v2: id: b70f186a-2ef9-43ce-b452-25fa1d91bcda
source-git-commit: 564171851fdccee43afd233da143d66182464889
workflow-type: tm+mt
source-wordcount: 1472
ht-degree: 96%

---


# Avvio rapido

Per iniziare a utilizzare LLM Optimizer, completa il processo di onboarding. Quindi personalizza categorie, argomenti e prompt, configura l’inoltro del registro CDN e apri le [dashboard](/help/dashboards/dashboards-overview.md) per ottenere insight più completi.

<!--Where steps differ by layout, use **Customer Configuration (classic experience)** or **Brands Management** / **Prompts Management**, whichever matches your current interface.-->

## Esperienza incentrata sul brand {#brand-centric-experience}

Per impostazione predefinita, i nuovi clienti iniziano con un’interfaccia incentrata sul brand e una configurazione basata sull’onboarding. In questa nuova interfaccia, ogni organizzazione inizia con un brand attivo e altri brand suggeriti tra cui scegliere. I clienti LLM Optimizer esistenti passeranno gradualmente all’Esperienza incentrata sul brand.

## Panoramica sull’onboarding

Il processo di onboarding inizia con l’onboarding del dominio e del nome del tuo brand. Di seguito sono riportate tutte le fasi del percorso di onboarding, insieme a suggerimenti utili su come iniziare a utilizzare LLM Optimizer il prima possibile.

### Consentire ad Adobe LLM Optimizer di accedere alle pagine pubbliche

Per fornire contenuti accurati e consigli tecnici, Adobe LLM Optimizer richiede l’accesso alle tue pagine pubbliche. Puoi consentirne l’accesso tramite un crawler interno sicuro, l’agente utente Spacecat/1.0.

Requisiti di configurazione:

* Aggiungi l’agente utente Spacecat/1.0 all’elenco Consentiti del file robots.txt del tuo sito o nelle regole di gestione del traffico da bot.
* Assicurati che le pagine non siano bloccate a livello di dominio o CDN. Le pagine bloccate non possono essere indicizzate, pertanto non è possibile generare attività di ottimizzazione e insight per esse.

Se la visibilità dei contenuti ha un punteggio basso nella dashboard, verifica che il crawler abbia accesso ai tuoi domini. L’accesso limitato è infatti una delle cause più comuni per un’indicizzazione incompleta.

## Passaggio 1: onboarding di dominio e nome del brand {#step-1-onboard-your-domain}

Per iniziare a utilizzare LLM Optimizer, attiva innanzitutto la versione di prova (se idonea) ed esegui l’onboarding di dominio e nome del brand.

### Attivare la versione di prova

Il flusso di attivazione varia a seconda del prodotto Adobe.

#### Clienti AEM Cloud

Per attivare la versione di prova, in qualità di cliente di AEM Cloud, puoi effettuare le seguenti operazioni:

* Passa a [Experience Hub](https://experienceleague.adobe.com/it/docs/experience-manager-cloud-service/content/experience-hub/experience-hub) e utilizza la scheda Annuncio prodotto per attivare LLM Optimizer. Dopo aver selezionato **Prova LLM Optimizer**, avviene il reindirizzamento a [https://llmo.now](https://llmo.now). Accedi tramite IMS, quindi immetti un dominio e il nome di un brand per avviare il processo di onboarding.
* Oppure passa direttamente a [https://llmo.now](https://llmo.now) e accedi.

![Versione di prova di LLM Optimizer](/help/overview/assets/llm-trial.png)

#### ADOBE ANALYTICS e ADOBE CUSTOMER JOURNEY ANALYTICS

Per i clienti Adobe Analytics e Adobe Customer Journey Analytics, visualizzerai un banner nella pagina Home di Experience Cloud.

![Pagina Home di Experience Cloud con banner Inizia la versione di prova di Adobe LLM Optimizer](/help/overview/assets/experience-cloud-llmo-trial-banner.png)

Puoi attivare la versione di prova in uno dei seguenti modi:

* Seleziona **Inizia la prova di Adobe LLM Optimizer** nel banner.
* Passa direttamente a [https://llmo.now](https://llmo.now) e accedi.

Una volta che la versione di prova è attiva, procedi con l’onboarding del nome del brand e del dominio.

>[!NOTE]
>
> * **Versione di prova gratuita:** i clienti di AEM Cloud e Adobe Analytics/Customer Journey Analytics possono utilizzare la versione di prova gratuita di LLM Optimizer.
> * **I clienti che attivano la versione di prova a partire dal 1° aprile 2026** possono utilizzare fino a 100 prompt, un dominio e implementare ottimizzazioni in un massimo di 10 URL per un singolo tipo di opportunità.
> * **I clienti che hanno attivato la versione di prova prima del 1° aprile 2026** continuano ad avere accesso a un massimo di 200 prompt in base ai termini esistenti.
>
>Se si supera questa soglia di utilizzo, è necessario sottoscrivere un contratto di licenza separato. L’accesso viene fornito “così com’è” e “secondo disponibilità” e può essere modificato, limitato o rimosso in qualsiasi momento. Per ulteriori informazioni, contatta il rappresentante del tuo account.

#### Eseguire l’onboarding di dominio e nome del tuo brand

Per iniziare a utilizzare LLM Optimizer, effettua l’onboarding di dominio e nome del tuo brand.

1. Immetti il nome del brand e il dominio associato.

   * Questo dovrebbe essere il dominio principale in cui analizzare e ottimizzare il contenuto.

1. Completa l’onboarding.

   * Dopo l’invio, LLM Optimizer inizia ad analizzare il dominio e a generare insight.

![Dominio LLM Optimizer](/help/overview/assets/domain.png)

>[!NOTE]
>I nuovi prompt aggiunti saranno disponibili nella [dashboard Presenza del brand](/help/dashboards/brand-presence.md) solo al termine dell’elaborazione.

>[!NOTE]
>Il dominio scelto verrà utilizzato da tutti gli utenti dell’organizzazione e non può essere cambiato.

Durante la fase di onboarding verrà generato un piccolo set di categorie, argomenti e prompt. L’analisi della presenza del brand su tali prompt sarà disponibile subito dopo l’onboarding del sito.

È inoltre disponibile la possibilità di implementare ottimizzazioni nella rete Edge. Per ulteriori informazioni, consulta le [domande frequenti su Ottimizza su rete Edge](https://experienceleague.adobe.com/it/docs/llm-optimizer/using/resources/optimize-at-edge/overview#frequently-asked-questions).

In aggiunta, configura l’[inoltro registro CDN](#step-4) per l’analisi del traffico. LLM Optimizer richiede dati e insight sulla Presenza del brand dal traffico da IA agentica e da referral per identificare opportunità e fornire consigli prescrittivi che possano aumentare la visibilità nei sistemi di IA.

### Clienti non AEM Cloud

Dopo che l’organizzazione avrà finalizzato il contratto di business, potrai iniziare a utilizzare LLM Optimizer con il dominio selezionato dalla tua organizzazione. Al termine dell’onboarding, accedi a [https://llmo.now](https://llmo.now).

## Passaggio 2: personalizzare categorie, argomenti e prompt {#step-2-customize-categories-topics-and-prompts}

Una volta effettuato l’onboarding del sito, puoi visualizzare l’analisi della Presenza del brand in base a un piccolo set di prompt generati automaticamente durante la fase di onboarding. In futuro, potrai personalizzare le categorie, gli argomenti e i prompt per il tuo brand.

### Configurazione cliente (navigazione classica)

Se utilizzi la navigazione classica (non l’esperienza incentrata sul brand), puoi personalizzare categorie, argomenti e prompt per il tuo brand dalla [dashboard di configurazione del cliente](/help/dashboards/customer-configuration.md).

![Dashboard Configurazione cliente](/help/overview/assets/prompt-creation.png)

Dalla dashboard Configurazione cliente puoi effettuare le seguenti operazioni:

* Aggiungere **nuove categorie** in linea con le tue priorità di business. Le categorie possono essere ampie aree di contenuto rilevanti per il dominio.
* Inserisci **argomenti personalizzati** o argomenti secondari da tracciare. Gli argomenti possono essere temi specifici associati a volumi elevati di parole chiave senza brand associate al dominio.
* Crea **i tuoi prompt** per monitorare la visibilità in query specifiche. I prompt sono query, con e senza brand, che forniscono una visibilità di base. In base alle categorie e agli argomenti specificati, verrà generato automaticamente solo un numero limitato di prompt.
* Definisci gli **alias** di menzione per garantire che tutte le menzioni di un brand vengano acquisite e prese in considerazione.
* Definisci gli **alias di altri brand** per tenere traccia con precisione degli altri brand.

>[!NOTE]
>I prompt esatti chiesti agli LLM non sono disponibili al pubblico perché non sono resi pubblici dagli LLM.

>[!NOTE]
>
> Per ulteriori dettagli sulla configurazione delle categorie, degli argomenti e dei prompt, consulta la pagina [Best practice per la configurazione di categorie, argomenti e prompt](/help/overview/best-practices-topics-prompts.md).

### Categorie di esperienza, argomenti e prompt incentrati sul brand

Per chi utilizza l’Esperienza incentrata sul brand, è possibile aggiungere categorie, argomenti e prompt come segue:

* **Categorie** - Passa a **Gestione dei brand** e fai clic su **Categorie**. Le categorie sono definite a livello globale e si applicano a tutti i brand in Gestione dei brand.

  ![Gestione dei brand con Categorie nella navigazione](/help/assets/brand-centric-experience/llmo-app-shell.png)

* **Argomenti e prompt** - Passa a **Gestione dei prompt** per creare argomenti e prompt, inclusi i prompt per un brand specifico.

  ![Gestione dei prompt](/help/assets/brand-centric-experience/prompts-management.png)

## Passaggio 3: insight sulla presenza del brand

Una volta effettuato l’onboarding del dominio, puoi visualizzare gli insight iniziali nella vista Presenza del brand in base ai prompt generati automaticamente durante l’onboarding. Dopo aver personalizzato le categorie, gli argomenti e i prompt, LLM Optimizer attiva automaticamente l’analisi della Presenza del brand sui prompt specificati e i risultati saranno disponibili in 24 ore.

>[!NOTE]
>
> Per chi utilizza l’Esperienza incentrata sul brand, passa a **Presenza del brand** e seleziona il brand di cui desideri visualizzare la presenza utilizzando il menu a discesa del brand. Con questa esperienza, puoi anche visualizzare la visibilità del brand a livello di **Tutti i brand**.

## Passaggio 4: fornire informazioni per l’inoltro del registro CDN {#step-4}

Per sbloccare gli insight su traffico da IA agentica e traffico da referral, registra l’inoltro dei registri CDN in modo che LLM Optimizer possa leggere i registri di accesso.

### Configurazione cliente (navigazione classica)

Se utilizzi la navigazione classica, puoi aggiungere le informazioni di inoltro del registro CDN dalla [dashboard di configurazione del cliente](/help/dashboards/customer-configuration.md#cdn-configuration). Apri la scheda **Configurazione CDN** e seleziona **Onboarding della CDN**.

![Configurazione CDN cliente](/help/overview/assets/cc-cdn.png)

In alternativa, se non hai già aggiunto un provider CDN, come descritto in precedenza, ti verrà richiesto di aggiungere l’inoltro del registro CDN quando accedi alle dashboard Traffico da IA agentica e Traffico da referral per la prima volta. Per ulteriori dettagli, consulta:

* [Traffico da IA agentica](/help/dashboards/agentic-traffic.md#cdn-setup)
* [Traffico da referral](/help/dashboards/referral-traffic.md#setup)

>[!NOTE]
>Per informazioni dettagliate sull’inoltro dei registri quando si utilizza una rete CDN gestita dal cliente (BYOCDN), consulta [Panoramica sull’inoltro del registro BYOCDN](/help/overview/log-forwarding/log-forwarding-overview.md)

### Inoltro registro CDN dell’Esperienza incentrata sul brand

Per chi utilizza l’Esperienza incentrata sul brand, è possibile aggiungere le informazioni di inoltro del registro CDN da **Gestione dei brand** come segue: apri **Gestione dei brand** e fai clic sull’etichetta **CDN**.

![Gestione dei brand: inoltro registro CDN](/help/assets/brand-centric-experience/brands-management-cdn.png)

## Passaggio 5: esplorare le dashboard e intervenire

Una volta fornite le informazioni per l’inoltro del registro CDN, puoi:

* Visualizzare la dashboard di [Presenza del brand](/help/dashboards/brand-presence.md), visualizzare il punteggio di visibilità e tenere traccia delle prestazioni relative ad altri brand.
* Esplora le dashboard [Traffico da IA agentica](/help/dashboards/agentic-traffic.md) e [Traffico da referral](/help/dashboards/referral-traffic.md), se hai configurato l’inoltro dei registri CDN.
* Utilizzare [Opportunità](/help/dashboards/opportunities-overview.md) per identificare contenuti e miglioramenti tecnici.
* Esportare dati e collaborare con il team o invitare un collega a utilizzare il prodotto.

>[!NOTE]
> Nell’Esperienza incentrata sul brand, accedi alla vista desiderata dalla sezione di navigazione sulla sinistra.

Infine, per comprendere appieno le funzionalità di LLM Optimizer, puoi esplorare tutte le [dashboard](/help/dashboards/dashboards-overview.md) disponibili.
