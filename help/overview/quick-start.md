---
title: Avvio rapido
description: Scopri come integrare il nome commerciale e il dominio, attivare la versione di prova da Experience Hub o Experience Cloud e completare la configurazione per Adobe LLM Optimizer.
feature: Quickstart, Onboarding
source-git-commit: d38cf066ca1e3785032b7beca1c257e3a42f532b
workflow-type: tm+mt
source-wordcount: '1454'
ht-degree: 37%

---


# Avvio rapido

Per iniziare a utilizzare LLM Optimizer, completa l’onboarding. Quindi personalizza categorie, argomenti e prompt, configura l&#39;inoltro del registro CDN e apri le [dashboard](/help/dashboards/dashboards-overview.md) per ottenere informazioni più complete.

**Esperienza incentrata sul marchio:** Per impostazione predefinita, i nuovi clienti iniziano con un&#39;interfaccia incentrata sul marchio con una configurazione basata sull&#39;onboarding. In questa nuova interfaccia, ogni organizzazione inizia con un marchio attivo e altri marchi suggeriti tra cui scegliere. I clienti LLM Optimizer esistenti passeranno gradualmente a questa esperienza incentrata sul marchio.

<!--Where steps differ by layout, use **Customer Configuration (classic experience)** or **Brands Management** / **Prompts Management**, whichever matches your current interface.-->

## Panoramica sull’onboarding

Il processo di onboarding inizia con l’onboarding del dominio e del nome del brand. Di seguito sono riportate tutte le parti del percorso di onboarding e sono riportati alcuni suggerimenti utili per iniziare a utilizzare LLM Optimizer il prima possibile.

### Consentire ad Adobe LLM Optimizer di accedere alle pagine pubbliche

Per fornire contenuti accurati e consigli tecnici, Adobe LLM Optimizer richiede l’accesso alle tue pagine pubbliche. Puoi consentirne l’accesso tramite un crawler interno sicuro, l’agente utente Spacecat/1.0.

Requisiti di configurazione:

* Aggiungi l’agente utente di Spacecat/1.0 al Inserisco nell&#39;elenco Consentiti di gestione del traffico da bot nel file robots.txt del tuo sito o nelle regole di gestione del traffico da bot.
* Assicurati che le pagine non siano bloccate a livello di dominio o CDN. Le pagine bloccate non possono essere indicizzate, pertanto non è possibile generare attività di ottimizzazione e insight per esse.

Se la visibilità dei contenuti ha un punteggio basso nella dashboard, verifica che il crawler abbia accesso ai tuoi domini. L’accesso limitato è infatti una delle cause più comuni per un’indicizzazione incompleta.

## Passaggio 1: integrare nome commerciale e dominio {#step-1-onboard-your-domain}

Per iniziare a utilizzare LLM Optimizer, attiva innanzitutto la versione di prova (se idonea) e incorpora il nome del brand e il dominio.

### Attiva la versione di prova

Il flusso di attivazione varia a seconda del prodotto Adobe.

#### Clienti AEM Cloud

Per attivare la versione di prova, in qualità di cliente di AEM Cloud, puoi effettuare le seguenti operazioni:

* Passa a [Experience Hub](https://experienceleague.adobe.com/it/docs/experience-manager-cloud-service/content/experience-hub/experience-hub) e utilizza la scheda Annuncio prodotto per attivare LLM Optimizer. Dopo aver selezionato **Prova LLM Optimizer**, sei reindirizzato a [https://llmo.now](https://llmo.now). Accedi tramite IMS, quindi immetti un dominio e un nome del brand per avviare il processo di onboarding.
* Oppure vai direttamente a [https://llmo.now](https://llmo.now) e accedi.

![Versione di prova di LLM Optimizer](/help/overview/assets/llm-trial.png)

#### Clienti Adobe Analytics

I clienti di Adobe Analytics visualizzeranno un banner nella pagina Home di Experience Cloud.

![Home page di Experience Cloud con banner Avvia la prova di Adobe LLM Optimizer](/help/overview/assets/experience-cloud-llmo-trial-banner.png)

Puoi attivare la versione di prova in uno dei seguenti modi:

* Seleziona **Avvia la prova Adobe LLM Optimizer** nel banner.
* Vai direttamente a [https://llmo.now](https://llmo.now) e accedi.

Una volta che la versione di prova è attiva, procedi con l’onboarding del nome del brand e del dominio.

>[!NOTE]
>
> * **Versione di prova gratuita:** i clienti di AEM Cloud e Adobe Analytics possono utilizzare la versione di prova gratuita di LLM Optimizer.
> * **I clienti che attivano la versione di prova il 1° aprile 2026** o in data successiva possono utilizzare fino a 100 prompt, un dominio e distribuire ottimizzazioni in un massimo di 10 URL per un singolo tipo di opportunità.
> * **I clienti che hanno attivato la versione di prova prima del 1° aprile 2026** continuano ad avere accesso a un massimo di 200 richieste in base ai termini esistenti.
>
>L’utilizzo oltre i limiti inclusi richiede un contratto di licenza separato. L’accesso viene fornito &quot;così com’è&quot; e &quot;così come è disponibile&quot; e può essere modificato, limitato o rimosso in qualsiasi momento. Per ulteriori informazioni, contatta il rappresentante del tuo account.

#### Acquisisci il tuo nome commerciale e dominio

Per iniziare a utilizzare LLM Optimizer, effettua l’onboarding del nome commerciale e del dominio.

1. Immetti il nome del brand e il dominio associato.

   * Questo dovrebbe essere il dominio principale in cui analizzare e ottimizzare i contenuti.

1. Completa l’onboarding.

   * Dopo l’invio, LLM Optimizer inizia ad analizzare il dominio e a generare insights.

![Dominio LLM Optimizer](/help/overview/assets/domain.png)

>[!NOTE]
>I nuovi prompt aggiunti saranno disponibili nella [dashboard Presenza del brand](/help/dashboards/brand-presence.md) solo al termine dell’elaborazione.

>[!NOTE]
>Il dominio scelto verrà utilizzato da tutti gli utenti dell’organizzazione e non può essere cambiato.

Durante la fase di onboarding verrà generato un piccolo set di categorie, argomenti e prompt. L’analisi della presenza del brand su tali prompt sarà disponibile subito dopo l’onboarding del sito.

È inoltre disponibile la possibilità di distribuire ottimizzazioni in Edge. Ulteriori informazioni in [Ottimizza in Edge — Domande frequenti](https://experienceleague.adobe.com/en/docs/llm-optimizer/using/resources/optimize-at-edge/overview#frequently-asked-questions).

Inoltre, configura [l&#39;inoltro del registro CDN](#step-4) per l&#39;analisi del traffico. LLM Optimizer richiede dati e informazioni Presenza dei brand da agenti e traffichi da referral per identificare opportunità e fornire consigli prescrittivi che migliorano la visibilità dell’intelligenza artificiale.

### Clienti non AEM Cloud

Dopo che l’organizzazione avrà finalizzato il contratto di business, potrai iniziare a utilizzare LLM Optimizer con il dominio selezionato dalla tua organizzazione. Al termine dell&#39;onboarding, accedi a [https://llmo.now](https://llmo.now).

## Passaggio 2: personalizzare categorie, argomenti e prompt {#step-2-customize-categories-topics-and-prompts}

Una volta effettuato l’onboarding del sito, puoi visualizzare l’analisi della Presenza del brand in base a un piccolo set di prompt generati automaticamente durante la fase di onboarding. In futuro, potrai personalizzare categorie, argomenti e prompt per il tuo marchio.

### Configurazione cliente (navigazione classica)

Se utilizzi la navigazione classica (non l&#39;esperienza incentrata sul marchio), puoi personalizzare categorie, argomenti e prompt per il tuo marchio dal [dashboard di configurazione del cliente](/help/dashboards/customer-configuration.md).

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

### Esperienza incentrata sul brand

Per i clienti che si avvalgono dell’esperienza incentrata sul brand, puoi aggiungere categorie, argomenti e prompt come segue:

* **Categorie** — Passare a **Gestione marchi** e fare clic su **Categorie**. Le categorie sono definite a livello globale e si applicano a tutti i marchi in Gestione marchi.

  ![Gestione dei marchi con categorie nella navigazione](/help/assets/brand-centric-experience/llmo-app-shell.png)

* **Argomenti e prompt** — Passare a **Gestione prompt** per creare argomenti e prompt, inclusi i prompt per un marchio specifico.

  ![Gestione richieste](/help/assets/brand-centric-experience/prompts-management.png)

## Passaggio 3: insight sulla presenza del brand

Una volta effettuato l’onboarding del dominio, puoi visualizzare gli insight iniziali nella vista Presenza del brand in base ai prompt generati automaticamente durante l’onboarding. Dopo aver personalizzato le categorie, gli argomenti e i prompt, LLM Optimizer attiva automaticamente l’analisi della Presenza del brand sui prompt specificati e i risultati saranno disponibili in 24 ore.

>[!NOTE]
>
> Per i clienti che usano un&#39;esperienza incentrata sul brand, passa a **Presenza dei brand** e seleziona il brand di cui vuoi visualizzare la Presenza dei brand utilizzando il menu a discesa del brand. Puoi anche visualizzare la visibilità dei brand a un livello **Tutti i marchi** con questa esperienza.

## Passaggio 4: fornire informazioni per l’inoltro del registro CDN {#step-4}

Per sbloccare le informazioni sul traffico e sul Traffico da referral agenti, registra l’inoltro dei registri CDN in modo che LLM Optimizer possa leggere i registri di accesso.

### Configurazione cliente (navigazione classica)

Se utilizzi la navigazione classica, puoi aggiungere le informazioni di inoltro del registro CDN dal [dashboard di configurazione del cliente](/help/dashboards/customer-configuration.md#cdn-configuration). Apri la scheda **Configurazione rete CDN** e seleziona **Rete CDN integrata**.

![Configurazione CDN cliente](/help/overview/assets/cc-cdn.png)

In alternativa, se non hai già aggiunto un provider CDN, come descritto in precedenza, ti verrà richiesto di aggiungere l’inoltro del registro CDN quando accedi alle dashboard Traffico da IA agentica e Traffico da referral per la prima volta. Per ulteriori dettagli, consulta:

* [Traffico da IA agentica](/help/dashboards/agentic-traffic.md#cdn-setup)
* [Traffico da referral](/help/dashboards/referral-traffic.md#setup)

>[!NOTE]
>Per informazioni dettagliate sull&#39;inoltro di log quando si utilizza una rete CDN gestita dal cliente (BYOCDN), vedere [Panoramica sull&#39;inoltro di log BYOCDN](/help/overview/log-forwarding/log-forwarding-overview.md)

### Esperienza incentrata sul brand

Per i clienti che fanno parte dell&#39;esperienza incentrata sul brand, puoi aggiungere le informazioni di inoltro del registro CDN da **Gestione marchi** come segue: apri **Gestione marchi** e fai clic sull&#39;etichetta **CDN**.

![Gestione marchi - Inoltro registro CDN](/help/assets/brand-centric-experience/brands-management-cdn.png)

## Passaggio 5: esplorare le dashboard e intervenire

Una volta fornite le informazioni per l’inoltro del registro CDN, puoi:

* Visualizzare la dashboard di [Presenza del brand](/help/dashboards/brand-presence.md), visualizzare il punteggio di visibilità e tenere traccia delle prestazioni relative ad altri brand.
* Esplora le dashboard [Agentic](/help/dashboards/agentic-traffic.md) e [Traffico da referral](/help/dashboards/referral-traffic.md), se è stato configurato l&#39;inoltro del registro CDN.
* Utilizzare [Opportunità](/help/dashboards/opportunities.md) per identificare contenuti e miglioramenti tecnici.
* Esportare dati e collaborare con il team o invitare un collega a utilizzare il prodotto.

>[!NOTE]
> Nell’esperienza incentrata sul marchio, accedi alla vista desiderata dalla sezione navigazione a sinistra.

Infine, per comprendere appieno le funzionalità di LLM Optimizer, puoi esplorare tutte le [dashboard](/help/dashboards/dashboards-overview.md) disponibili.
