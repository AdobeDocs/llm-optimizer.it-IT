---
title: Avvio rapido
description: Questo è l’articolo di avvio rapido.
source-git-commit: 5dbf794b87df92583daec83ab02063821ee7a412
workflow-type: tm+mt
source-wordcount: '618'
ht-degree: 0%

---


# Avvio rapido

Per iniziare a utilizzare l’ottimizzatore LLM, devi seguire il processo di onboarding. Dopodiché avrai accesso a tutte le dashboard e le funzionalità di LLM Optimizer.

## Panoramica sull’onboarding

Il processo di onboarding inizia con l’onboarding del dominio. Il processo varia a seconda che tu sia o meno un cliente di AEM Cloud. Dopo aver completato il processo, è necessario fornire informazioni sull’inoltro del registro CDN e infine personalizzare categorie, argomenti e prompt.

### Passaggio 1: integrare il dominio

### Clienti AEM Cloud

I clienti di AEM Cloud (Cloud Service/Managed Services/ Edge Delivery Service) vedranno l&#39;opzione per provare LLM Optimizer tramite la scheda Annuncio prodotto in [Experience Hub](https://experienceleague.adobe.com/it/docs/experience-manager-cloud-service/content/experience-hub/experience-hub).

>[!NOTE]
>Le nuove richieste aggiunte non verranno visualizzate in Presenza marchio fino al completamento dell’elaborazione. I clienti di AEM Cloud (Cloud Service, Managed Services/Edge Delivery Service) possono utilizzare la versione di prova gratuita di LLM Optimizer. L&#39;utilizzo di più di 200 prompt richiede un contratto di licenza separato. L’accesso viene fornito &quot;così com’è&quot; e &quot;così come è disponibile&quot; e può essere modificato, limitato o rimosso da Adobe in qualsiasi momento. Per ulteriori informazioni, contattare il [rappresentante dell&#39;account].

![Versione di valutazione di LLM Optimizer](/help/overview/assets/llm-trial.png)

Dopo aver fatto clic sul pulsante **Prova LLM Optimizer**, verrai reindirizzato a [https://llmo.now](https://llmo.now) . Ti verrà quindi richiesto di effettuare l’accesso tramite IMS. Dopo aver effettuato l’accesso, inizierai il processo di onboarding fornendo un dominio e il nome del brand.

![Dominio LLM Optimizer](/help/overview/assets/domain.png)

>[!NOTE]
>Il dominio fornito verrà utilizzato da tutte le persone dell’organizzazione e non può essere modificato.

Per attivare l’analisi della presenza del brand, devi fornire categorie, argomenti e prompt.

![Analisi della presenza del marchio](/help/overview/assets/bp-analysis.png)

Inoltre, devi anche configurare l’inoltro del registro CDN per l’analisi del traffico. LLM Optimizer richiede dati e informazioni sulla presenza del marchio dal traffico di riferimento e agente per identificare opportunità e fornire consigli prescrittivi per aiutare i clienti a migliorare la visibilità AI.

### Clienti non AEM Cloud

Dopo aver firmato il contratto, potrai iniziare a utilizzarlo tramite il comando slackbot con il dominio che desideri aggiungere a LLM Optimizer. Una volta completato l&#39;onboarding, potrai accedere a LLM Optimizer tramite [https://llmo.now](https://llmo.now) .

### Passaggio 2: precompilazione automatica di approfondimenti

Una volta effettuato l’onboarding del dominio, LLM Optimizer popolerà automaticamente quanto segue:

* **Categorie** - Aree di contenuto estese relative al dominio.
* **Argomenti** - Temi specifici associati a parole chiave non di branding di grandi volumi associate al dominio.
* **Richieste** - Query (con e senza marchio) per fornire visibilità linea di base.

Questo assicura che anche prima di aggiungere configurazioni e input personalizzati, vedrai le informazioni iniziali sulla visibilità del tuo marchio.

### Passaggio 3: personalizzare categorie, argomenti e prompt

Fai clic sul [dashboard di configurazione del cliente](/help/dashboards/customer-configuration.md) per iniziare a personalizzare categorie, argomenti e prompt.

![Dashboard configurazione cliente](/help/dashboards/assets/customer-config.png)

Da questa dashboard è possibile:

* Aggiungi nuove categorie in linea con le priorità aziendali.
* Immetti argomenti o sottoargomenti personalizzati da tracciare.
* Crea le richieste per monitorare la visibilità in query specifiche.
* Definisci gli alias di menzione in modo che tutte le menzioni vengano acquisite.
* Definisci gli alias dei concorrenti per tenere traccia dei concorrenti in modo accurato.

### Passaggio 4: fornire informazioni per l’inoltro del registro CDN

Per sbloccare le informazioni sul traffico agente e sul traffico di riferimento, devi fornire informazioni per l’inoltro del registro CDN. Consulta ogni pagina specifica per ulteriori dettagli su come configurare l’inoltro dei registri:

* [Traffico agente](/help/dashboards/agentic-traffic.md)
* [Traffico di riferimento](/help/dashboards/referral-traffic.md#setup#cdn-setup)

### Passaggio 5: esplorare le dashboard e intervenire

Dopo aver fornito le informazioni per l’inoltro del registro CDN, puoi:

* Visualizza la dashboard [Presenza marchio](/help/dashboards/brand-presence.md), visualizza il tuo punteggio di visibilità e tieni traccia delle prestazioni relative ai tuoi concorrenti.
* Esplora i dashboard [Agentic](/help/dashboards/agentic-traffic.md) e [Referral Traffic](/help/dashboards/referral-traffic.md).
* Utilizza [Opportunità](/help/dashboards/opportunities.md) per identificare contenuti e miglioramenti tecnici.
* Esportare dati e collaborare con il team o invitare il collega a utilizzare il prodotto.

Per comprendere appieno le funzionalità dell&#39;ottimizzatore LLM, esplorare tutte le [dashboard](/help/dashboards/dashboards-overview.md) disponibili.
