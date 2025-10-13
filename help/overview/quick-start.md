---
title: Avvio rapido
description: 'Inizia a usare Adobe LLM Optimizer: integra il tuo marchio, sfrutta le informazioni sulla visibilità AI ed esplora le dashboard per migliorare le prestazioni di ricerca.'
source-git-commit: a699f8f3c50f77d07f29cd354fd1ef8e6eed8ff9
workflow-type: tm+mt
source-wordcount: '933'
ht-degree: 0%

---


# Avvio rapido

Per iniziare a utilizzare l’ottimizzatore LLM, devi completare il processo di onboarding come descritto nei passaggi descritti di seguito. Dopo aver completato il processo, potrai accedere a [dashboard di LLM Optimizer](/help/dashboards/dashboards-overview.md) e ad altre funzionalità.

## Panoramica sull’onboarding

Il processo di onboarding inizia con l’onboarding del dominio. Il processo varia a seconda che tu sia o meno un cliente di AEM Cloud. Dopo aver completato il processo, è necessario fornire informazioni sull’inoltro del registro CDN e infine personalizzare categorie, argomenti e prompt. Di seguito sono riportate tutte le fasi del processo, insieme a suggerimenti utili su come iniziare a utilizzare LLM Optimizer il prima possibile.

## Passaggio 1: integrare il dominio

### Prova prima di acquistare

I clienti di AEM Cloud (Cloud Service, Managed Services, Edge Delivery Service) possono utilizzare l&#39;offerta **Prova prima di acquistare**. Si tratta di una versione di prova gratuita di LLM Optimizer con un massimo di 200 richieste gratuite. L&#39;utilizzo di più di 200 prompt richiede un contratto di licenza separato. L’accesso viene fornito &quot;così com’è&quot; e &quot;così come è disponibile&quot; e può essere modificato, limitato o rimosso da Adobe in qualsiasi momento.

Nella versione gratuita di sono disponibili alcune funzionalità dei prodotti:

* La versione di prova è limitata a un dominio. Dopo aver completato l’installazione, non potrai modificare il dominio fornito.
* Il supporto per la distribuzione delle ottimizzazioni non sarà disponibile.

Consulta la sezione seguente per informazioni su come attivare la versione di prova gratuita e integrare il dominio.

### Clienti AEM Cloud

Se sei un cliente di AEM Cloud, puoi provare LLM Optimizer utilizzando la scheda Annuncio prodotto in [Experience Hub](https://experienceleague.adobe.com/it/docs/experience-manager-cloud-service/content/experience-hub/experience-hub).

>[!NOTE]
>Le nuove richieste aggiunte non verranno visualizzate nel [dashboard della presenza del marchio](/help/dashboards/brand-presence.md) fino al completamento dell&#39;elaborazione. I clienti di AEM Cloud possono utilizzare la versione di prova gratuita di LLM Optimizer. L&#39;utilizzo di più di 200 prompt richiede un contratto di licenza separato. L’accesso viene fornito &quot;così com’è&quot; e &quot;così come è disponibile&quot; e può essere modificato, limitato o rimosso da Adobe in qualsiasi momento. Per ulteriori informazioni, contatta il rappresentante del tuo account.

![Versione di valutazione di LLM Optimizer](/help/overview/assets/llm-trial.png)

Dopo aver fatto clic sul pulsante **Prova LLM Optimizer**, verrai reindirizzato a [https://llmo.now](https://llmo.now). Ti verrà quindi richiesto di effettuare l’accesso tramite IMS. Dopo aver effettuato l’accesso, inizierai il processo di onboarding fornendo un dominio e il nome del brand.

![Dominio LLM Optimizer](/help/overview/assets/domain.png)

>[!NOTE]
>Il dominio fornito verrà utilizzato da tutti gli utenti dell’organizzazione e non può essere modificato.

Per attivare l’analisi della presenza del brand, devi fornire categorie, argomenti e prompt.

![Analisi della presenza del marchio](/help/overview/assets/bp-analysis.png)

Inoltre, devi anche configurare [Inoltro registro CDN](#step-4) per l&#39;analisi del traffico. LLM Optimizer richiede dati e informazioni sulla presenza del marchio dal traffico di riferimento e agente per identificare opportunità e fornire raccomandazioni prescrittive al fine di aumentare la visibilità dell’intelligenza artificiale.

### Clienti non AEM Cloud

Una volta finalizzato il contratto di business, potrai iniziare a utilizzarlo tramite il comando slackbot con il dominio che desideri integrare in LLM Optimizer. Una volta completato l&#39;onboarding, potrai accedere a LLM Optimizer tramite [https://llmo.now](https://llmo.now).

### Passaggio 2: personalizzare categorie, argomenti e prompt

Per attivare l’analisi della presenza del brand e popolare la dashboard con informazioni sulla visibilità del brand, è necessario personalizzare categorie, argomenti e prompt. Questa configurazione viene creata nel [dashboard di configurazione del cliente](/help/dashboards/customer-configuration.md).

![Dashboard configurazione cliente](/help/overview/assets/prompt-creation.png)

Da questa dashboard è possibile:

* Aggiungi **nuove categorie** in linea con le tue priorità aziendali. Le categorie possono essere ampie aree di contenuto rilevanti per il dominio.
* Immetti **argomenti personalizzati** o argomenti secondari da monitorare. Gli argomenti possono essere temi specifici associati a parole chiave senza marchio associate al dominio.
* Crea **le tue richieste** per monitorare la visibilità in query specifiche. I prompt sono query (con e senza marchio) che forniscono una visibilità di base. In base alle categorie e agli argomenti specificati, verrà generato automaticamente solo un numero limitato di prompt.
* Definisci gli **alias** di menzione per garantire che tutte le menzioni di un brand vengano acquisite e contabilizzate.
* Definisci **alias concorrenti** per tenere traccia dei concorrenti in modo accurato.

>[!NOTE]
>I prompt esatti richiesti non sono disponibili al pubblico perché non sono resi pubblici dai moduli LLM.

>[!NOTE]
>
> Per ulteriori dettagli su come impostare categorie, argomenti, prompt e concorrenti, vedere la pagina [Best practice per la configurazione di categorie, argomenti, prompt e concorrenti](/help/overview/best-practices-topics-prompts.md).

### Passaggio 3: precompilazione automatica di approfondimenti

Una volta effettuato l’onboarding del dominio e dopo aver fornito categorie e argomenti, LLM Optimizer attiva automaticamente l’analisi della presenza del brand.

### Passaggio 4: fornire informazioni per l’inoltro del registro CDN {#step-4}

Per sbloccare le informazioni sul traffico agente e sul traffico di riferimento, devi fornire informazioni per l’inoltro del registro CDN. Può essere aggiunto dal [dashboard di configurazione del cliente](/help/dashboards/customer-configuration.md) passando alla scheda **Configurazione CDN** e facendo clic su **CDN integrato**.

![CDN configurazione cliente](/help/overview/assets/cc-cdn.png)

In alternativa, se in precedenza non è stato aggiunto alcun provider CDN simile all’esempio precedente, ti verrà richiesto di aggiungere l’inoltro del registro CDN quando accedi per la prima volta alle dashboard Traffico agente e traffico di riferimento. Per ulteriori dettagli, consulta:

* [Traffico agente](/help/dashboards/agentic-traffic.md#cdn-setup)
* [Traffico di riferimento](/help/dashboards/referral-traffic.md#setup#setup)

### Passaggio 5: esplorare le dashboard e intervenire

Dopo aver fornito le informazioni per l’inoltro del registro CDN, puoi:

* Visualizza la dashboard [Presenza marchio](/help/dashboards/brand-presence.md), visualizza il tuo punteggio di visibilità e tieni traccia delle prestazioni relative ai tuoi concorrenti.
* Esplora i dashboard [Agentic](/help/dashboards/agentic-traffic.md) e [Referral Traffic](/help/dashboards/referral-traffic.md), se è stato configurato l&#39;inoltro del registro CDN.
* Utilizza [Opportunità](/help/dashboards/opportunities.md) per identificare contenuti e miglioramenti tecnici.
* Esportare dati e collaborare con il team o invitare il collega a utilizzare il prodotto.

Infine, per comprendere appieno le funzionalità di LLM Optimizer, è necessario esplorare tutte le [dashboard](/help/dashboards/dashboards-overview.md) disponibili.
