---
title: Avvio rapido
description: 'Inizia a usare Adobe LLM Optimizer: effettua l’onboarding del tuo brand, sfrutta gli insight sulla visibilità IA ed esplora le dashboard per migliorare le prestazioni di ricerca.'
feature: Quickstart, Onboarding
source-git-commit: ae37ef578f279eae6ea51fd8aed5c6b91c8e1088
workflow-type: tm+mt
source-wordcount: '1151'
ht-degree: 93%

---


# Avvio rapido

Per iniziare a utilizzare LLM Optimizer, devi completare il processo di onboarding come descritto nei passaggi descritti di seguito. Dopo averlo completato, potrai accedere alle [dashboard di LLM Optimizer](/help/dashboards/dashboards-overview.md) e ad altre funzionalità.

## Panoramica sull’onboarding

Il processo di onboarding inizia con l’onboarding del dominio. Il processo varia a seconda che tu sia o meno un cliente di AEM Cloud. Dopo aver completato il processo, devi fornire informazioni sull’inoltro del registro CDN e infine personalizzare categorie, argomenti e prompt. Di seguito sono riportate tutte le fasi del processo, insieme a suggerimenti utili su come iniziare a utilizzare LLM Optimizer il prima possibile.

### Consentire ad Adobe LLM Optimizer di accedere alle pagine pubbliche

Per fornire contenuti accurati e consigli tecnici, Adobe LLM Optimizer richiede l’accesso alle tue pagine pubbliche. Puoi consentirne l’accesso tramite un crawler interno sicuro, l’agente utente Spacecat/1.0.

Requisiti di configurazione:

* Aggiungi l’agente utente Spacecat/1.0 all’elenco Consentiti del file robots.txt del tuo sito o nelle regole di gestione del traffico da bot
* Assicurati che le pagine non siano bloccate a livello di dominio o CDN. Le pagine bloccate non possono essere indicizzate, pertanto non è possibile generare attività di ottimizzazione e insight per esse.

Se la visibilità dei contenuti ha un punteggio basso nella dashboard, verifica che il crawler abbia accesso ai tuoi domini. L’accesso limitato è infatti una delle cause più comuni per un’indicizzazione incompleta.

## Passaggio 1: onboarding del dominio

### Prova prima di acquistare

I clienti di AEM Cloud (Cloud Service, Managed Services, Edge Delivery Service) possono utilizzare l&#39;offerta **Prova prima di acquistare**. Si tratta di una versione di prova gratuita di LLM Optimizer, con 200 prompt gratuiti. Per utilizzare più di 200 prompt, è necessario un contratto di licenza separato. L’accesso viene fornito “così com’è” e “secondo disponibilità” e può essere modificato, limitato o rimosso da Adobe in qualsiasi momento.

Nella versione gratuita, alcune funzionalità del prodotto non sono disponibili:

* La versione di prova è limitata a un solo dominio. Dopo aver completato la configurazione, non potrai cambiare il dominio specificato.
* La possibilità di distribuire ottimizzazioni è disponibile in Accesso anticipato. Per ulteriori informazioni, consulta [Ottimizzare alle domande frequenti su Edge](https://experienceleague.adobe.com/it/docs/llm-optimizer/using/resources/optimize-at-edge#frequently-asked-questions).

Consulta la sezione seguente per informazioni su come attivare la versione di prova gratuita e sull’onboarding del tuo dominio.

### Clienti di AEM Cloud

Se sei cliente di AEM Cloud, puoi provare LLM Optimizer utilizzando la scheda Annunci prodotto in [Experience Hub](https://experienceleague.adobe.com/it/docs/experience-manager-cloud-service/content/experience-hub/experience-hub).

>[!NOTE]
>I nuovi prompt aggiunti saranno disponibili nella [dashboard Presenza del brand](/help/dashboards/brand-presence.md) solo al termine dell’elaborazione. I clienti di AEM Cloud possono utilizzare la versione di prova gratuita di LLM Optimizer. Per utilizzare più di 200 prompt, è necessario un contratto di licenza separato. L’accesso viene fornito “così com’è” e “secondo disponibilità” e può essere modificato, limitato o rimosso da Adobe in qualsiasi momento. Per ulteriori informazioni, rivolgiti al rappresentante per il tuo account.

![Versione di prova di LLM Optimizer](/help/overview/assets/llm-trial.png)

Dopo aver fatto clic sul pulsante **Prova LLM Optimizer**, verrai reindirizzato su [https://llmo.now](https://llmo.now). Ti verrà quindi richiesto di effettuare l’accesso tramite IMS. Dopo aver effettuato l’accesso, inizierai il processo di onboarding fornendo un dominio e il nome del tuo brand.

![Dominio LLM Optimizer](/help/overview/assets/domain.png)

>[!NOTE]
>Il dominio scelto verrà utilizzato da tutti gli utenti dell’organizzazione e non può essere cambiato.

Durante la fase di onboarding verrà generato un piccolo set di categorie, argomenti e prompt. L’analisi della presenza del brand su tali prompt sarà disponibile subito dopo l’onboarding del sito.

<!--![Brand Presence Analysis](/help/overview/assets/bp-analysis.png)-->

Inoltre, configura l’[inoltro del registro CDN](#step-4) per l’analisi del traffico. LLM Optimizer richiede dati e insight sulla Presenza del brand dal traffico da IA agentica e da referral per identificare opportunità e fornire consigli prescrittivi al fine di aumentare la visibilità nei sistemi di IA.

### Clienti non AEM Cloud

Dopo aver finalizzato l’accordo di business, potrai iniziare a utilizzare il dominio di cui desideri effettuare l’onboarding in LLM Optimizer. Una volta completato l’onboarding, potrai accedere a LLM Optimizer tramite [https://llmo.now](https://llmo.now).

## Passaggio 2: personalizzare categorie, argomenti e prompt

Una volta effettuato l’onboarding del sito, puoi visualizzare l’analisi della Presenza del brand in base a un piccolo set di prompt generati automaticamente durante la fase di onboarding. In futuro, potrai personalizzare le categorie, gli argomenti e i prompt per il tuo brand. Questa configurazione viene creata nella [dashboard Configurazione cliente](/help/dashboards/customer-configuration.md).

![Dashboard Configurazione cliente](/help/overview/assets/prompt-creation.png)

Da questa dashboard puoi:

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

## Passaggio 3: insight sulla presenza del brand

Una volta effettuato l’onboarding del dominio, puoi visualizzare gli insight iniziali nella vista Presenza del brand in base ai prompt generati automaticamente durante l’onboarding. Dopo aver personalizzato le categorie, gli argomenti e i prompt, LLM Optimizer attiva automaticamente l’analisi della Presenza del brand sui prompt specificati e i risultati saranno disponibili in 24 ore.

## Passaggio 4: fornire informazioni per l’inoltro del registro CDN {#step-4}

Per sbloccare gli insight sul traffico da IA agentica e da referral, devi fornire informazioni per l’inoltro del registro CDN. Può essere aggiunto dalla [dashboard Configurazione cliente](/help/dashboards/customer-configuration.md#cdn-configuration) passando alla scheda **Configurazione CDN** e facendo clic su **Effettua onboarding CDN**.

![Configurazione CDN cliente](/help/overview/assets/cc-cdn.png)

In alternativa, se non hai già aggiunto un provider CDN, come descritto in precedenza, ti verrà richiesto di aggiungere l’inoltro del registro CDN quando accedi alle dashboard Traffico da IA agentica e Traffico da referral per la prima volta. Per ulteriori dettagli, consulta:

* [Traffico da IA agentica](/help/dashboards/agentic-traffic.md#cdn-setup)
* [Traffico da referral](/help/dashboards/referral-traffic.md#setup#setup)

## Passaggio 5: esplorare le dashboard e intervenire

Una volta fornite le informazioni per l’inoltro del registro CDN, puoi:

* Visualizzare la dashboard di [Presenza del brand](/help/dashboards/brand-presence.md), visualizzare il punteggio di visibilità e tenere traccia delle prestazioni relative ad altri brand.
* Esplorare le dashboard [Traffico da IA agentica](/help/dashboards/agentic-traffic.md) e [Traffico da referral](/help/dashboards/referral-traffic.md), se hai configurato l’inoltro del registro CDN.
* Utilizzare [Opportunità](/help/dashboards/opportunities.md) per identificare contenuti e miglioramenti tecnici.
* Esportare dati e collaborare con il team o invitare un collega a utilizzare il prodotto.

Infine, per comprendere appieno le funzionalità di LLM Optimizer, puoi esplorare tutte le [dashboard](/help/dashboards/dashboards-overview.md) disponibili.
