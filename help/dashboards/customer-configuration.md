---
title: Configurazione cliente
description: Utilizza la configurazione del cliente per definire in che modo il tuo marchio verrà monitorato e analizzato all’interno della piattaforma di ottimizzazione LLM.
source-git-commit: 4192fe32c9e7cea4218ea580a9300f1fceb0f909
workflow-type: tm+mt
source-wordcount: '789'
ht-degree: 0%

---


# Configurazione cliente

Nella configurazione del cliente puoi definire in che modo il brand verrà monitorato e analizzato all’interno della piattaforma di ottimizzazione LLM. Puoi personalizzare le categorie (ad esempio, business unit o linee di prodotti), tenere traccia dei concorrenti e aggiungere alias di menzione del brand per acquisire tutte le varianti del brand in tutti i prompt. Questa configurazione garantisce che la piattaforma personalizzi le informazioni sul contesto aziendale, consentendo un’analisi accurata del traffico, delle opportunità e della visibilità.

![Dashboard configurazione cliente](/help/dashboards/assets/customer-config.png)

## Dashboard di configurazione del cliente

La dashboard di configurazione del cliente è uno strumento potente che fornisce informazioni approfondite sulla visibilità del brand in LLM. Impostando correttamente categorie, argomenti, prompt e concorrenti, puoi garantire che il tuo marchio sia ben posizionato per essere visualizzato nelle risposte generate da LLM. Rivedere regolarmente informazioni quali Share of Voice, visibilità dei contenuti e opportunità ti aiuterà ad adattare la tua strategia e restare al passo con la concorrenza.

Per configurare il modo in cui LLM Optimizer monitora e analizza la presenza del brand in diversi mercati e scenari competitivi, puoi accedere alle seguenti schede:

* [Categorie](#categories)
* [Tracciamento concorrenti](#competitor-tracking)
* [Alias del marchio](#brand-aliases)
* [Approfondimenti dati](#data-insights)
* [CDN agente](#agentic-cdn)

## Categorie {#categories}

Dalla scheda Categorie è possibile definire le categorie commerciali o le linee di prodotti che si desidera monitorare e associarle a specifiche aree geografiche. Nel complesso, la scheda Categorie fa riferimento a tutte le altre personalizzazioni presenti in questa pagina, poiché le categorie verranno visualizzate nel campo categoria per le altre personalizzazioni (monitoraggio dei concorrenti, alias e così via). Per aggiungere una nuova categoria:

1. Fai clic sul pulsante **Aggiungi**.
2. Nella nuova finestra di configurazione, aggiungi **Nome categoria**.
3. Personalizza la **Area associata** in cui verrà monitorata la categoria.
4. Fai clic su **Salva** per visualizzare la nuova categoria nell&#39;elenco delle categorie.

L&#39;aggiunta di nuove categorie non genererà automaticamente argomenti e prompt, che dovranno essere aggiunti manualmente dalla scheda [Data Insights](#data-insights).

Per eliminare una categoria, fare clic sull&#39;icona Elimina nell&#39;elenco delle categorie. Fai attenzione, perché **l&#39;eliminazione di una categoria comporta anche l&#39;eliminazione degli elementi associati**, ad esempio i concorrenti che potresti aver configurato o gli alias del brand collegati a quella categoria specifica.

## Tracciamento concorrenti {#competitor-tracking}

Utilizzando il monitoraggio dei concorrenti, puoi monitorare in che modo i tuoi concorrenti vengono menzionati in relazione al tuo marchio, in diverse categorie e aree geografiche. Monitorarne la presenza e le prestazioni nei segmenti di mercato. Per personalizzare il monitoraggio della concorrenza:

1. Per aggiungere un nuovo concorrente, fare clic sul pulsante **Aggiungi**.
2. Nella nuova finestra di configurazione, seleziona la **Categoria**. Le categorie create in precedenza verranno visualizzate qui.
3. Aggiungere il nome del concorrente.
4. Se necessario, personalizza l’alias e i domini del concorrente.
5. Fare clic su **Salva** per visualizzare il nuovo concorrente nell&#39;elenco dei concorrenti.

Per eliminare un concorrente, fare clic sull&#39;icona Elimina nell&#39;elenco dei concorrenti.

## Alias del marchio {#brand-aliases}

Utilizzando gli alias del brand, puoi configurare nomi alternativi e varianti del brand da monitorare in diverse categorie e aree geografiche. Ciò assicura un monitoraggio completo di tutte le menzioni del marchio. Per aggiungere un alias del brand:

1. Fai clic sul pulsante **Aggiungi**.
2. Nella nuova finestra di configurazione, seleziona la **Categoria**. Le categorie create in precedenza verranno visualizzate qui.
3. Selezionare l&#39;**Area** in cui verrà monitorato l&#39;alias.
4. Aggiungi l’alias del brand.
5. Fai clic su **Salva** per visualizzare l&#39;alias del brand nell&#39;elenco.

Per eliminare un alias del brand, fai clic sull’icona Elimina dall’elenco degli alias.

## Approfondimenti dati {#data-insights}

Da questa scheda è possibile rivedere, gestire e personalizzare i prompt. Puoi caricare un file con estensione csv di [Informazioni sulla presenza del brand](/help/dashboards/brand-presence.md#data-insights) e compilare l&#39;elenco con i prompt e gli argomenti di tale analisi. Se necessario, è inoltre possibile eliminare, modificare e aggiungere argomenti e relative richieste.

Per importare un file .csv di approfondimenti dati, devi innanzitutto esportare un file dal dashboard Presenza marchio. Per informazioni su come eseguire questa operazione, consulta la sezione [approfondimenti sui dati](/help/dashboards/brand-presence.md#data-insights). Una volta ottenuto il file:

1. Nel dashboard, fai clic su **Carica CSV**.
2. Nella finestra Importa approfondimenti dati, trascina e rilascia o scegli manualmente il file.
3. Fare clic su **Carica dati**.

Puoi anche creare un nuovo file CSV scaricando il modello dalla finestra **Importa dati**. Una volta ottenuto il modello, aprilo e inserisci gli argomenti con i prompt, le categorie e le aree a essi associati in una nuova riga.

Inoltre, è possibile aggiungere argomenti/prompt all&#39;elenco indipendentemente da un file CSV. A questo scopo, nel dashboard devi:

1. Fare clic sul pulsante **Aggiungi argomento**.
2. Nella nuova finestra di configurazione, seleziona la **Categoria**. Le categorie create in precedenza verranno visualizzate qui.
3. Immettere il nome dell&#39;argomento.
4. Aggiungete il testo del prompt.
5. Seleziona la regione.
6. Fare clic su **Aggiungi prompt** per visualizzare l&#39;argomento con il prompt nell&#39;elenco.

>[!NOTE]
>Le nuove richieste aggiunte non verranno visualizzate in Presenza marchio fino al completamento dell’elaborazione.

Nell&#39;elenco è possibile fare clic su ogni argomento e verranno visualizzati i prompt associati. Per eliminare l&#39;argomento e i prompt associati, fare clic sull&#39;icona Elimina dall&#39;elenco.

<!--## Agentic CDN {#agentic-cdn}

Not available (will it be available for release?).-->

