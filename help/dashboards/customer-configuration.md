---
title: Configurazione cliente
description: Utilizza la configurazione cliente per definire in che modo il tuo brand verrà monitorato e analizzato all’interno della piattaforma LLM Optimizer.
feature: Customer Configuration
source-git-commit: 5d8b59ea4281c88bb42dc48096c07a3faaeb2e88
workflow-type: ht
source-wordcount: '836'
ht-degree: 100%

---


# Configurazione cliente {#customer-configuration}

La dashboard Configurazione cliente è uno strumento potente che fornisce insight sulla visibilità del brand in LLM. Impostando correttamente categorie, argomenti e prompt, puoi assicurarti che il brand sia ben posizionato per essere visualizzato nelle risposte generate da LLM. Grazie a questa configurazione, la piattaforma è in grado di personalizzare gli insight in base al contesto del tuo business, per un’analisi accurata della visibilità, del traffico e delle opportunità.

![Dashboard Configurazione cliente](/help/dashboards/assets/customer-config.png)

Per configurare il modo in cui LLM Optimizer monitora e analizza la presenza del tuo brand in diversi mercati e scenari competitivi, puoi accedere alle seguenti schede:

* [Prompt](#prompts-brand)
* [Categorie](#categories)
* [Altri brand](#other-brands)
* [Alias del brand](#brand-aliases)
* [Configurazione CDN](#agentic-cdn)

>[!IMPORTANT]
>
> Per ulteriori dettagli sulla configurazione delle categorie, degli argomenti e dei prompt, consulta la pagina [Best practice per la configurazione di categorie, argomenti e prompt](/help/overview/best-practices-topics-prompts.md).

## Prompt {#prompts-brand}

Da questa scheda puoi rivedere, gestire e personalizzare i prompt. Puoi caricare un file con .csv di [analisi della presenza del brand](/help/dashboards/brand-presence.md), e l’elenco verrà popolato con i prompt e gli argomenti di tale analisi. Oppure, [scarica una libreria di prompt](/help/overview/best-practices-topics-prompts.md) creata da Adobe. Se necessario, puoi anche eliminare, modificare e aggiungere argomenti e relativi prompt.

Per importare un file .csv con insight sui dati, devi innanzitutto esportare un file dalla dashboard Presenza del brand. Per informazioni su come eseguire questa operazione, consulta la sezione [Insight sui dati](/help/dashboards/brand-presence.md#data-insights). Una volta che disponi del file:

1. Nella dashboard, fai clic su **Carica CSV**.
2. Nella finestra Importa insight sui dati, trascina o scegli manualmente il file.
3. Fai clic su **Carica dati**.

Puoi anche creare un nuovo file CSV scaricando il modello dalla finestra **Importa insight sui dati**. Una volta scaricato, apri il modello e inserisci i tuoi argomenti con relativi prompt, categorie e aree geografiche, ciascuno in una nuova riga.

Per informazioni su come scaricare e utilizzare la libreria di prompt di settore creata da Adobe, consulta la sezione Libreria di prompt di settore in [questa pagina](/help/overview/best-practices-topics-prompts.md)

Puoi inoltre aggiungere argomenti e prompt all’elenco indipendentemente da un file CSV o da una libreria di prompt. A tale scopo, nella dashboard:

1. Fai clic sul pulsante **Aggiungi argomento**.
2. Nella nuova finestra di configurazione, seleziona la **Categoria**. Le categorie create in precedenza verranno visualizzate qui.
3. Inserisci il nome dell’argomento.
4. Aggiungi il testo del prompt.
5. Seleziona l’area geografica.
6. Fai clic su **Aggiungi prompt** per visualizzare nell’elenco l’argomento con il prompt.

>[!NOTE]
>I nuovi prompt aggiunti appariranno nella presenza del brand solo al termine dell’elaborazione.

Nell’elenco puoi fare clic su ogni argomento per visualizzare i relativi prompt. Per eliminare l’argomento e i relativi prompt, fai clic sull’icona Elimina dall’elenco.

## Categorie {#categories}

Nella scheda Categorie puoi definire le categorie di business o le linee di prodotti di cui tenere traccia e associarle ad aree geografiche specifiche. Nel complesso, la scheda Categorie si riferisce a quasi tutte le altre personalizzazioni in questa pagina, perché le categorie verranno visualizzate nel campo categoria per le altre personalizzazioni (tracciamento di altri brand, alias e così via). Per aggiungere una nuova categoria:

1. Fai clic sul pulsante **Aggiungi**.
2. Nella nuova finestra di configurazione, aggiungi il **Nome categoria**.
3. Personalizza l’**Area geografica associata** in cui verrà monitorata la categoria.
4. Fai clic su **Salva** per visualizzare la nuova categoria nell’elenco delle categorie.

L’aggiunta di nuove categorie non genera automaticamente argomenti e prompt, che dovrai aggiungere manualmente dalla scheda [Insight sui dati](#data-insights).

Per eliminare una categoria, fai clic sull’icona Elimina nell’elenco delle categorie. Presta attenzione, perché **l’eliminazione di una categoria comporta anche l’eliminazione degli elementi associati**, come gli alias del brand collegati a quella specifica categoria.

## Altri brand {#others-tracking}

Utilizzando questa scheda, puoi tenere traccia di come vengono menzionati altri brand in relazione al tuo in diverse categorie e aree geografiche. Puoi monitorarne la presenza e le prestazioni nei tuoi segmenti di mercato. Per personalizzare il tracciamento:

1. Fai clic sul pulsante **Aggiungi**.
2. Nella nuova finestra di configurazione, seleziona la **Categoria**. Le categorie create in precedenza verranno visualizzate qui.
3. Aggiungi il nome dell’altro brand.
4. Se necessario, personalizza gli alias e i domini dell’altro brand.
5. Fai clic su **Salva**.

Per eliminare una voce dall’elenco, fai clic sull’icona Elimina.

## Alias del brand {#brand-aliases}

Utilizzando gli alias del brand, puoi configurare nomi e varianti alternativi del tuo brand da tracciare in diverse categorie e aree geografiche. Questo garantisce un monitoraggio completo di tutte le menzioni del brand. Per aggiungere un alias del brand:

1. Fai clic sul pulsante **Aggiungi**.
2. Nella nuova finestra di configurazione, seleziona la **Categoria**. Le categorie create in precedenza verranno visualizzate qui.
3. Seleziona l’**Area geografica** in cui verrà monitorato l’alias.
4. Aggiungi l’alias del brand.
5. Fai clic su **Salva** per visualizzare l’alias del brand nell’elenco.

Per eliminare un alias del brand, fai clic sull’icona Elimina dall’elenco degli alias.

## Configurazione CDN {#cdn-configuration}

Da questa scheda, puoi configurare i flussi CDN per consentire ad Adobe LLM Optimizer di analizzare i dati CDN. Questi dati verranno utilizzati per alimentare le dashboard (come Traffico da IA agentica), fornendo insight su pattern di traffico, metriche delle prestazioni e opportunità di ottimizzazione. Per effettuare l’onboarding del provider CDN, fai clic su **Effettua onboarding CDN**.

![Configurazione cliente CDN](/help/overview/assets/cc-cdn.png)

Nella finestra **Onboarding provider CDN**:

1. Seleziona il provider CDN.
2. Fai clic su **Onboarding** per abilitare l’inoltro del registro.

Se selezioni **Altro**, dovrai contattare llmo-now@adobe.com per assistenza.
