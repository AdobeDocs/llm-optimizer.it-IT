---
title: Configurazione cliente
description: Utilizza la configurazione del cliente per definire in che modo il tuo marchio verrà monitorato e analizzato all’interno della piattaforma di ottimizzazione LLM.
feature: Customer Configuration
source-git-commit: 5d8b59ea4281c88bb42dc48096c07a3faaeb2e88
workflow-type: tm+mt
source-wordcount: '832'
ht-degree: 3%

---


# Configurazione cliente {#customer-configuration}

La dashboard di configurazione del cliente è uno strumento potente che fornisce informazioni approfondite sulla visibilità del brand in LLM. Impostando correttamente categorie, argomenti e prompt, puoi garantire che il brand sia ben posizionato per essere visualizzato nelle risposte generate da LLM. Questa configurazione garantisce che la piattaforma personalizzi le informazioni sul contesto aziendale, consentendo un’analisi accurata del traffico, delle opportunità e della visibilità.

![Dashboard configurazione cliente](/help/dashboards/assets/customer-config.png)

Per configurare il modo in cui LLM Optimizer monitora e analizza la presenza dei brand in diversi mercati e scenari competitivi, è possibile accedere alle seguenti schede:

* [Prompt](#prompts-brand)
* [Categorie](#categories)
* [Altri marchi](#other-brands)
* [Alias del brand](#brand-aliases)
* [Configurazione CDN](#agentic-cdn)

>[!IMPORTANT]
>
> Per ulteriori dettagli sulla configurazione delle categorie, degli argomenti e delle richieste, vedere la pagina [Best practice per la configurazione di categorie, argomenti e richieste](/help/overview/best-practices-topics-prompts.md).

## Prompt {#prompts-brand}

Da questa scheda è possibile rivedere, gestire e personalizzare i prompt. È possibile caricare un file con estensione csv di [analisi Presenza dei brand](/help/dashboards/brand-presence.md) e l&#39;elenco verrà compilato con i prompt e gli argomenti di tale analisi o [Scaricare una raccolta di prompt](/help/overview/best-practices-topics-prompts.md) creata da Adobe. Se necessario, è inoltre possibile eliminare, modificare e aggiungere argomenti e relative richieste.

Per importare un file .csv di approfondimenti dati, devi innanzitutto esportare un file dal dashboard delle Presenze dei brand. Per informazioni su come eseguire questa operazione, consulta la sezione [approfondimenti sui dati](/help/dashboards/brand-presence.md#data-insights). Una volta ottenuto il file:

1. Nel dashboard, fai clic su **Carica CSV**.
2. Nella finestra Importa approfondimenti dati, trascina e rilascia o scegli manualmente il file.
3. Fare clic su **Carica dati**.

Puoi anche creare un nuovo file CSV scaricando il modello dalla finestra **Importa dati**. Una volta ottenuto il modello, aprilo e inserisci gli argomenti con i prompt, le categorie e le aree a essi associati in una nuova riga.

Per informazioni su come scaricare e utilizzare la libreria dei prompt di settore creata da Adobe, consulta la sezione Libreria dei prompt di settore in [questa pagina](/help/overview/best-practices-topics-prompts.md)

È inoltre possibile aggiungere argomenti/prompt all&#39;elenco indipendentemente da un file CSV o da una raccolta di prompt. A questo scopo, nel dashboard devi:

1. Fare clic sul pulsante **Aggiungi argomento**.
2. Nella nuova finestra di configurazione, seleziona la **Categoria**. Le categorie create in precedenza verranno visualizzate qui.
3. Immettere il nome dell&#39;argomento.
4. Aggiungete il testo del prompt.
5. Seleziona la regione.
6. Fare clic su **Aggiungi prompt** per visualizzare l&#39;argomento con il prompt nell&#39;elenco.

>[!NOTE]
>I nuovi prompt aggiunti non appariranno nella presenza del brand fino al completamento dell’elaborazione.

Nell&#39;elenco è possibile fare clic su ogni argomento e verranno visualizzati i prompt associati. Per eliminare l&#39;argomento e i prompt associati, fare clic sull&#39;icona Elimina dall&#39;elenco.

## Categorie {#categories}

Dalla scheda Categorie è possibile definire le categorie commerciali o le linee di prodotti di cui si desidera tenere traccia e associarle ad aree specifiche. Nel complesso, la scheda Categorie fa riferimento a quasi tutte le altre personalizzazioni in questa pagina, perché le categorie verranno visualizzate nel campo categoria per le altre personalizzazioni (tracciamento di altri utenti, alias e così via). Per aggiungere una nuova categoria:

1. Fai clic sul pulsante **Aggiungi**.
2. Nella nuova finestra di configurazione, aggiungi **Nome categoria**.
3. Personalizza la **Area associata** in cui verrà monitorata la categoria.
4. Fai clic su **Salva** per visualizzare la nuova categoria nell&#39;elenco delle categorie.

L&#39;aggiunta di nuove categorie non genererà automaticamente argomenti e prompt, che dovranno essere aggiunti manualmente dalla scheda [Data Insights](#data-insights).

Per eliminare una categoria, fare clic sull&#39;icona Elimina nell&#39;elenco delle categorie. Fai attenzione, perché **l&#39;eliminazione di una categoria comporta anche l&#39;eliminazione degli elementi associati**, come gli alias del brand collegati a quella categoria specifica.

## Altri marchi {#others-tracking}

Utilizzando questa scheda, puoi tenere traccia di come vengono menzionati gli altri in relazione al tuo marchio in diverse categorie e aree geografiche. Monitorarne la presenza e le prestazioni nei segmenti di mercato. Per personalizzare il tracciamento:

1. Fai clic sul pulsante **Aggiungi**.
2. Nella nuova finestra di configurazione, seleziona la **Categoria**. Le categorie create in precedenza verranno visualizzate qui.
3. Aggiungi il nome dell’altro.
4. Se necessario, personalizza gli altri alias e domini.
5. Fai clic su **Salva**.

Per eliminare una voce dall’elenco, fai clic sull’icona Elimina.

## Alias del brand {#brand-aliases}

Utilizzando gli alias del brand, puoi configurare nomi alternativi e varianti del brand da monitorare in diverse categorie e aree geografiche. Questo garantisce un monitoraggio completo di tutte le menzioni dei brand. Per aggiungere un alias del brand:

1. Fai clic sul pulsante **Aggiungi**.
2. Nella nuova finestra di configurazione, seleziona la **Categoria**. Le categorie create in precedenza verranno visualizzate qui.
3. Selezionare l&#39;**Area** in cui verrà monitorato l&#39;alias.
4. Aggiungi l’alias del brand.
5. Fai clic su **Salva** per visualizzare l&#39;alias del brand nell&#39;elenco.

Per eliminare un alias del brand, fai clic sull’icona Elimina dall’elenco degli alias.

## Configurazione CDN {#cdn-configuration}

Da questa scheda, puoi configurare i flussi CDN per consentire a Adobe LLM Optimizer di analizzare i dati CDN. Questi dati verranno utilizzati per alimentare le dashboard (come Traffico agente), fornendo informazioni approfondite su pattern di traffico, metriche delle prestazioni e opportunità di ottimizzazione. Per integrare il provider CDN, fai clic su **CDN integrato**.

![CDN configurazione cliente](/help/overview/assets/cc-cdn.png)

Nella finestra **Provider CDN integrato**:

1. Seleziona il provider CDN.
2. Fai clic su **Onboard** per abilitare l&#39;inoltro del registro.

Se selezioni **Altro**, dovrai contattare llmo-now@adobe.com per assistenza.
