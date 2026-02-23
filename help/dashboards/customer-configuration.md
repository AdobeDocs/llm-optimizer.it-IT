---
title: Configurazione cliente
description: Utilizza la configurazione cliente per definire in che modo il tuo brand verrà monitorato e analizzato all’interno della piattaforma LLM Optimizer.
feature: Customer Configuration
source-git-commit: 3fab5f21311a741e51e7a31cd3a26de79fcbff95
workflow-type: tm+mt
source-wordcount: '2100'
ht-degree: 40%

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
* [Google Search Console](#google-console)

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

Per eliminare un alias del brand, fai clic sull&#39;icona **Elimina** dall&#39;elenco degli alias.

## Configurazione CDN {#cdn-configuration}

Da questa scheda, puoi configurare i flussi CDN per consentire ad Adobe LLM Optimizer di analizzare i dati CDN. Questi dati verranno utilizzati per alimentare le dashboard (come Traffico da IA agentica), fornendo insight su pattern di traffico, metriche delle prestazioni e opportunità di ottimizzazione. Per effettuare l’onboarding del provider CDN, fai clic su **Effettua onboarding CDN**.

![Configurazione cliente CDN](/help/overview/assets/cc-cdn.png)

Nella finestra **Onboarding provider CDN**:

1. Seleziona il provider CDN.
2. Fai clic su **Onboarding** per abilitare l’inoltro del registro.

Se selezioni **Altro**, dovrai contattare llmo-now@adobe.com per assistenza.

## Google Search Console {#google-console}

Adobe LLM Optimizer consente di integrare l’account Google Search Console per inserire query di ricerca reali direttamente nell’interfaccia. Facendo emergere query reali della console di Google Search, puoi creare set di prompt basati sul comportamento di ricerca effettivo e sui pattern di individuazione ad alto intento. In questo modo è possibile assegnare priorità ai prompt in base a una domanda comprovata e allineare le attività di ottimizzazione LLM al modo in cui gli utenti eseguono attualmente le ricerche. Inoltre, si mantiene il controllo completo perché le query non vengono mai aggiunte automaticamente e devono essere selezionate in modo esplicito prima di diventare prompt attivi.

### Come funziona {#how-it-works}

La cosa principale da ricordare sull&#39;integrazione tra LLM Optimizer e Google Search Console è la seguente: invece di indovinare manualmente cosa i clienti potrebbero chiedere a un assistente AI, esaminiamo cosa stanno già cercando **e trasformiamo le query reali in prompt naturali e conversazionali.** Questo processo di spostamento dalle query di ricerca ai prompt AI è esemplificato nel diagramma seguente.

![Flusso di processo](/help/dashboards/assets/diagram-flow.png)

In generale, il processo prevede cinque fasi:

#### Passaggio 1: raccogliere i dati di ricerca reali {#gsc-one}

Il processo inizia con le parole chiave che il pubblico sta effettivamente utilizzando quando trova il tuo sito web tramite Google. Questo set di dati non elaborati (spesso migliaia di query univoche) è la base per tutto ciò che segue.

#### Passaggio 2 — Analizzare il significato e filtrare per la sicurezza {#gsc-two}

Ogni query viene analizzata per il suo significato semantico (ciò che l’utente chiede realmente) e sottoposta a screening attraverso un filtro di sicurezza che rimuove i contenuti inappropriati o fuori marca. In questo modo, solo le parole chiave pulite e pertinenti possono essere spostate in avanti.

#### Passaggio 3: raggruppare in categorie e argomenti {#gsc-three}

Le query correlate vengono raggruppate automaticamente in **categorie** (temi di business generali) e **argomenti** (argomenti secondari mirati in ogni categoria). Il sistema assegna priorità alle categorie già configurate nella configurazione di LLM Optimizer. Inoltre, può anche far emergere nuove categorie rivelate dai dati di ricerca, ma non ancora monitorate. Il diagramma seguente è un esempio di categorie e argomenti per un marchio di mobili:

![Marchio per mobili](/help/dashboards/assets/diagram-example.png)

#### Passaggio 4 — Generare i prompt con una messa a terra in parole chiave reali {#gsc-four}

Per ogni argomento, il sistema genera prompt simili al modo in cui le persone reali parlano con gli assistenti AI. Ogni prompt è direttamente influenzato dalle parole chiave di ricerca effettive provenienti dalla console di ricerca di Google, trasformando l’intento delle parole chiave in domande conversazionali naturali.

Questo approccio (basato su parole chiave) significa:

* I prompt riflettono la domanda reale, non le domande ipotetiche.
* Il linguaggio rispecchia il modo in cui i clienti formulano le cose.
* La copertura copre l&#39;intera gamma di ciò che gli utenti cercano sul tuo sito.

La generazione rapida considera anche il profilo del tuo marchio (inclusi prodotti, concorrenti, posizionamento nel settore e pubblico target) per garantire che i prompt siano contestualmente precisi.

#### Fase 5 - Garanzia di qualità e consegna {#gsc-five}

Prima della consegna, ogni prompt viene sottoposto a diversi controlli di qualità automatizzati:

* Deduplicazione: i prompt quasi identici vengono rimossi.
* Bilanciamento del rapporto di branding: garantisce un mix realistico (~75% senza branding, ~25% con branding).
* Qualità del linguaggio: elimina il fraseggio robotico e richiede un suono naturale.
* Controlli di coerenza: convalida le date, rimuove le frasi di riempimento e assicura una lunghezza concisa.

Inoltre, a ogni prompt vengono assegnati tag con la categoria, l’argomento, il tipo di intento e la classificazione branded/unbranded, pronti per essere monitorati da LLM Optimizer.

#### Anatomia prompt {#prompt-anatomy}

Al termine della procedura, ogni richiesta inviata a LLM Optimizer presenta i seguenti attributi:

| Campo | Descrizione |
|---------|----------|
| Testo | Il prompt, simile a come verrebbe digitato da un utente in un assistente AI |
| Categoria | L’ampio tema di business assegnato a questo prompt. |
| Argomento | Argomento secondario specifico all&#39;interno della categoria. |
| Area geografica | Il mercato di riferimento (ad esempio, Stati Uniti, Regno Unito e così via). |
| Intento | La mentalità dell’utente: informativa, comparativa, transazionale, istruttiva, di pianificazione o delega. |
| Tipo | Il tipo può essere di marca (menziona il marchio/i prodotti) o senza marca (domanda generica del settore). |

### Procedura di utilizzo {#how-to-use}

Segui i passaggi descritti di seguito per integrare e utilizzare le query della console di Google Search con LLM Optimizer.

#### Collegare la console di Google Search {#connect-console}

Prima di utilizzare questa funzione è necessario integrare l’account Google Search Console con l’ottimizzatore LLM.

1. Apri la dashboard Configurazione cliente.
1. Passare alla scheda Console Google Search e fare clic su **Connetti account**.
   ![Console di Google Search](/help/dashboards/assets/google-console.png)
1. Accedi con un account Google che abbia accesso alla proprietà della console di ricerca desiderata.
   ![Account Google](/help/dashboards/assets/google-account.png)
1. Scegliere la proprietà da connettere.
   ![Proprietà console](/help/dashboards/assets/console-property.png)
1. Al termine della connessione, LLM Optimizer inizia a recuperare le query di ricerca rilevanti.
   ![Recupero dati](/help/dashboards/assets/console-complete.png)

#### Rivedere e cercare le query {#search-query}

Dopo aver integrato l’account Google Search Console con l’ottimizzatore LLM, puoi rivedere l’elenco degli argomenti e delle richieste originate dalla console di ricerca e aggiungere le richieste dall’elenco.

1. Nella scheda Console di ricerca di Google, controlla l’elenco degli argomenti e delle richieste generate dalla console di ricerca.
   ![Elenco richieste](/help/dashboards/assets/prompts-list.png)
1. Fare clic sull&#39;argomento o sulla categoria di prompt desiderata per espandere l&#39;elenco.
1. Utilizza il pulsante **Aggiungi** per aggiungere i prompt dall&#39;elenco. È inoltre possibile aggiungere in blocco richieste e categorie utilizzando **Aggiungi tutto**.
   ![Aggiungi prompt](/help/dashboards/assets/add-prompts.png)
1. Una volta effettuata la selezione, fare clic su **Salva** nel messaggio di notifica.

#### Visualizzare le query aggiunte nell&#39;elenco Prompt {#prompts-list}

Una volta aggiunta, la query viene visualizzata nella scheda [Prompts](#prompts-brand) del dashboard Configurazione cliente. I prompt originati da Google Search Console sono contrassegnati con l&#39;icona di Google Search Console nella colonna **Origin**. L’icona consente di distinguere tra i prompt basati sul comportamento effettivo di ricerca dell’utente e quelli aggiunti manualmente o da altre origini.

### Domande frequenti {#gsc-faq}

D: Con quale frequenza vengono aggiornati i prompt nella dashboard di Google Search Console?

I prompt originati dalla console Google Search vengono in genere aggiornati una volta al mese. Ogni aggiornamento richiama i dati più recenti delle query di ricerca dalla console Google Search, esegue nuovamente la pipeline di generazione e aggiorna il set di prompt. In questo modo i prompt rimangono allineati con le tendenze di ricerca correnti e i cambiamenti stagionali nel comportamento degli utenti.

D: Quanti prompt vengono in genere originati dalla console Google Search?

Il numero dipende dalle dimensioni della distribuzione e dalla quantità di categorie tracciate. Ad esempio:

| Categorie | Argomenti totali | Richieste inviate |
|---------|----------|----------|
| 1-2 | 3-8 | ~65-180 |
| 4-5 | 12-20 | ~270-450 |
| 10 | 30 - 40 | ~675-900 |

Il nostro obiettivo è quello di fornire set di prompt che soddisfino gli obiettivi di qualità comunicati durante le fasi di prova e onboarding: almeno 20 prompt per argomento, con 3-4 argomenti per categoria e un equilibrio salutare tra branding e non branding.

D: quanto tempo dopo la connessione alla console di Google Google Search visualizzerò le richieste provenienti da tale console?

Le richieste sono in genere disponibili **entro poche ore** dopo l&#39;attivazione della connessione alla console di Google Search. La pipeline estrae automaticamente i dati di ricerca, li elabora attraverso i passaggi di generazione e controllo della qualità e distribuisce il prompt finale impostato su LLM Optimizer.

D: Chi può collegarsi alla console di Google Search?

Chiunque abbia **Proprietario** o **Autorizzazione completa** nella proprietà Console di Google Search può autorizzare la connessione. Si tratta dei livelli di autorizzazione che consentono l&#39;accesso in lettura ai dati delle query di ricerca. Se non sei sicuro del tuo livello di autorizzazione, puoi controllarlo in **Impostazioni>Utenti** e autorizzazioni nella console di Google Search.

D: Posso contrassegnare i prompt come ignorati o saltati in modo da non visualizzarli nell’elenco dei prompt della console di ricerca di Google?

Sì, è possibile eliminare qualsiasi richiesta che non si desidera monitorare. I prompt eliminati vengono rimossi dall&#39;elenco dei prompt attivi e non verranno visualizzati nei rapporti futuri. Se un prompt eliminato viene rigenerato in un successivo aggiornamento mensile, è possibile rimuoverlo nuovamente.

D: Una volta aggiunte le richieste da Google Search Console all’elenco delle richieste, quanto tempo visualizzerò per Presenza dei brand i dati di tali richieste?

I dati di presenza dei brand per i nuovi prompt aggiunti verranno visualizzati durante il prossimo aggiornamento dei dati pianificato, che in genere viene eseguito all’inizio di ogni settimana. A seconda del momento in cui si aggiungono le richieste, è possibile che i risultati vengano visualizzati entro pochi giorni.
