---
title: Configurazione cliente
description: Utilizza la configurazione cliente per definire in che modo il tuo brand verrà monitorato e analizzato all’interno della piattaforma LLM Optimizer.
feature: Customer Configuration
autotag-review: '2026-05-15T17:45:12.067Z'
TQID: 'https://experienceleague.adobe.com/qa7zk54n9G19-Azz9f6mn7V1kAGvnJSOJjpxbTBeHgc'
product_v2:
  - id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2:
  - id: a0b5a505-2fd7-4c3d-b61c-b557fb6f0558
  - id: d1956731-2adb-4bb7-8301-2b239254ac72
subfeature_v2:
  - id: e69d5a42-0217-4ca5-9396-a9a826a170da
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
source-git-commit: 564171851fdccee43afd233da143d66182464889
workflow-type: tm+mt
source-wordcount: 2249
ht-degree: 100%

---


# Configurazione cliente {#customer-configuration}

La dashboard Configurazione cliente è uno strumento potente che fornisce insight sulla visibilità del brand in LLM. Impostando correttamente categorie, argomenti e prompt, puoi assicurarti che il brand sia ben posizionato per essere visualizzato nelle risposte generate da LLM. Grazie a questa configurazione, la piattaforma è in grado di personalizzare gli insight in base al contesto del tuo business, per un’analisi accurata della visibilità, del traffico e delle opportunità.

La dashboard Configurazione cliente (mostrata di seguito) viene utilizzata se la tua organizzazione utilizza ancora questo tipo di navigazione.

![Dashboard Configurazione cliente](/help/dashboards/assets/customer-config.png)

Per configurare il modo in cui LLM Optimizer monitora e analizza la presenza del tuo brand in diversi mercati e scenari competitivi, puoi accedere alle seguenti schede:

* [Prompt](#prompts-brand)
* [Categorie](#categories)
* [Altri brand](#other-brands)
* [Alias del brand](#brand-aliases)
* [Configurazione CDN](#agentic-cdn)
* [Google Search Console](#google-console)

Se utilizzi l’[esperienza incentrata sul brand](/help/overview/quick-start.md#brand-centric-experience), passa a **Gestione dei brand** per configurare i brand e gli alias dei brand e per definire la concorrenza da monitorare. La funzione **Gestione dei brand** viene utilizzata anche per configurare integrazioni quali Google Search Console, Adobe Analytics e l’inoltro di registri CDN relativi agli URL associati ai brand. A tal fine, fai clic sulle schede corrispondenti: GSC, CDN e così via.

![Gestione dei brand: navigazione nell’app (esperienza incentrata sul brand)](/help/assets/brand-centric-experience/llmo-app-shell.png)

![Gestione dei brand: panoramica della configurazione (esperienza incentrata sul brand)](/help/assets/brand-centric-experience/brands-management-configuration.png)

>[!IMPORTANT]
>
> Per ulteriori dettagli sulla configurazione delle categorie, degli argomenti e dei prompt, consulta la pagina [Best practice per la configurazione di categorie, argomenti e prompt](/help/overview/best-practices-topics-prompts.md).

## Prompt {#prompts-brand}

Dalla scheda **Prompt**, puoi rivedere, gestire e personalizzare i prompt. Puoi caricare un file con .csv di [analisi della presenza del brand](/help/dashboards/brand-presence.md), e l’elenco verrà popolato con i prompt e gli argomenti di tale analisi. Oppure, [scarica una libreria di prompt](/help/overview/best-practices-topics-prompts.md) creata da Adobe. Se necessario, puoi anche eliminare, modificare e aggiungere argomenti e relativi prompt.

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

Se utilizzi l’[esperienza incentrata sul brand](/help/overview/quick-start.md#brand-centric-experience), per aggiungere argomenti e prompt passa a **Gestione dei prompt**.

![Gestione dei prompt (esperienza incentrata sul brand)](/help/assets/brand-centric-experience/prompts-management.png)

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

Per eliminare un alias del brand, fai clic sull’icona **Elimina** dall’elenco degli alias.

## Configurazione CDN {#cdn-configuration}

Da questa scheda, puoi configurare i flussi CDN per consentire ad Adobe LLM Optimizer di analizzare i dati CDN. Questi dati verranno utilizzati per alimentare le dashboard (come Traffico da IA agentica), fornendo insight su pattern di traffico, metriche delle prestazioni e opportunità di ottimizzazione. Per effettuare l’onboarding del provider CDN, fai clic su **Effettua onboarding CDN**.

![Configurazione cliente CDN](/help/overview/assets/cc-cdn.png)

Nella finestra **Onboarding provider CDN**:

1. Seleziona il provider CDN.
2. Fai clic su **Onboarding** per abilitare l’inoltro del registro.

Se selezioni **Altro**, dovrai contattare llmo-now@adobe.com per assistenza.

## Google Search Console {#google-console}

Adobe LLM Optimizer consente di integrare l’account Google Search Console per importare query di ricerca reali direttamente nell’interfaccia. Facendo emergere query reali da Google Search Console, puoi generare set di prompt basati sul comportamento di ricerca effettivo e sui pattern di individuazione ad alto intento. In questo modo, puoi assegnare priorità ai prompt in base a una domanda comprovata e allineare le attività di ottimizzazione LLM al modo in cui gli utenti eseguono attualmente le ricerche. Inoltre, mantieni il pieno controllo poiché le query non vengono mai aggiunte automaticamente e devono essere selezionate in modo esplicito prima di diventare prompt attivi.

### Come funziona {#how-it-works}

L’aspetto principale da tenere presente sull’integrazione tra LLM Optimizer e Google Search Console è il seguente: invece di indovinare manualmente ciò che i clienti potrebbero chiedere a un assistente IA, esaminiamo le loro **ricerche attuali** e trasformiamo le query reali in prompt naturali e conversazionali. Questo processo di transizione dalle query di ricerca ai prompt per l’IA è esemplificato nel diagramma seguente.

![Flusso del processo](/help/dashboards/assets/diagram-flow.png)

In generale, il processo prevede cinque passaggi:

#### Passaggio 1: raccogliere i dati di ricerca reali {#gsc-one}

Il processo inizia con le parole chiave che il pubblico sta effettivamente utilizzando quando trova il tuo sito Web tramite Google. Questo set di dati non elaborati (spesso migliaia di query univoche) è la base per le operazioni successive.

#### Passaggio 2: analizzare il significato e filtrare per la sicurezza {#gsc-two}

Ogni query viene analizzata per il suo significato semantico (ciò che l’utente chiede realmente) e sottoposta a screening attraverso un filtro di sicurezza che rimuove i contenuti inappropriati o non coerenti con il brand. Ciò garantisce che solo le parole chiave pulite e pertinenti procedano alla fase successiva.

#### Passaggio 3: raggruppare in categorie e argomenti {#gsc-three}

Le query correlate vengono raggruppate automaticamente in **categorie** (temi di business generali) e **argomenti** (sottoargomenti specifici all’interno di ogni categoria). Il sistema assegna priorità alle categorie già impostate nella configurazione di LLM Optimizer. Inoltre, può anche far emergere nuove categorie che i dati di ricerca rivelano ma che non sono ancora monitorate. Il diagramma seguente è un esempio di categorie e argomenti per un brand operante nel settore dell’arredamento:

![Brand di arredamento](/help/dashboards/assets/diagram-example.png)

#### Passaggio 4: generare prompt basati su parole chiave reali {#gsc-four}

Per ogni argomento, il sistema genera prompt simili a quelli che gli utenti userebbero per interagire con gli assistenti virtuali basati sull’intelligenza artificiale. Ogni prompt è direttamente influenzato dalle reali parole chiave della Google Search Console, traducendo l’intento di ricerca degli utenti in domande conversazionali naturali.

Questo approccio (basato su parole chiave) implica che:

* I prompt rispecchiano la domanda effettiva, non scenari ipotetici.
* Il linguaggio rispecchia il modo in cui i tuoi clienti si esprimono realmente.
* La copertura abbraccia l’intera gamma di ricerche effettuate dagli utenti sul tuo sito.

Il processo di generazione dei prompt tiene conto anche del profilo del tuo brand, inclusi prodotti, concorrenza, posizionamento nel settore e pubblico target, per garantire che i prompt siano contestualmente accurati.

#### Passaggio 5: controllo qualità e consegna {#gsc-five}

Prima della consegna, ogni prompt viene sottoposto a diversi controlli di qualità automatizzati:

* Deduplicazione: i prompt quasi identici vengono rimossi.
* Bilanciamento della percentuale di prompt con brand: garantisce un mix realistico (circa il 75% di prompt senza brand e il 25% di prompt con brand).
* Qualità del linguaggio: elimina le frasi robotiche in modo che i messaggi risultino naturali.
* Controlli di coerenza: convalidano le date, rimuovono le frasi superflue e garantiscono una lunghezza concisa.

Inoltre, ogni prompt viene taggato con categoria, argomento, tipo di intento e classificazione con o senza brand, affinché LLM Optimizer avvii il monitoraggio.

#### Anatomia del prompt {#prompt-anatomy}

Una volta completata la procedura precedente, ogni prompt inviato a LLM Optimizer presenta i seguenti attributi:

| Campo | Descrizione |
|---------|----------|
| Testo | Il prompt, simile a come un utente lo digiterebbe in un assistente IA |
| Categoria | Il tema aziendale generale assegnato al prompt. |
| Argomento | Il sottotema specifico all’interno della categoria. |
| Area geografica | Il mercato target (ad esempio, Stati Uniti, Regno Unito e così via). |
| Intento | La mentalità dell’utente: informativa, comparativa, transazionale, didattica, di pianificazione o di delega. |
| Tipo | La tipologia può essere con brand (menziona il brand/prodotto) o senza brand (domanda generica sul settore). |

### Procedura di utilizzo {#how-to-use}

Segui i passaggi descritti di seguito per integrare e utilizzare le query di Google Search Console con LLM Optimizer.

#### Connessione della Google Search Console {#connect-console}

Prima di utilizzare questa funzionalità, integra il tuo account Google Search Console con LLM Optimizer.

1. Apri la dashboard **Configurazione cliente** (navigazione classica) o **Gestione dei brand** (Esperienza incentrata sul brand), quindi passa all’integrazione di Google Search Console (tag GSC nell’Esperienza incentrata sul brand).
1. Passa alla scheda Google Search Console e fai clic su **Connetti account**.
   ![Google Search Console](/help/dashboards/assets/google-console.png)
1. Accedi con un account Google che disponga dell’accesso alla proprietà di Search Console desiderata.
   ![Account Google](/help/dashboards/assets/google-account.png)
1. Seleziona la proprietà che desideri collegare.
   ![Proprietà di Console](/help/dashboards/assets/console-property.png)
1. Una volta stabilita la connessione, LLM Optimizer inizia a recuperare le query di ricerca pertinenti.
   ![Recupero dei dati](/help/dashboards/assets/console-complete.png)

#### Query di revisione e ricerca {#search-query}

Dopo aver integrato l’account Google Search Console con LLM Optimizer, puoi rivedere l’elenco di argomenti e prompt provenienti da Search Console e aggiungere i prompt presenti nell’elenco.

1. Nella scheda di Google Search Console, rivedi l’elenco di argomenti e prompt provenienti da Search Console.
   ![Elenco dei prompt](/help/dashboards/assets/prompts-list.png)
1. Fai clic sulla categoria di argomento/prompt desiderata per espandere l’elenco.
1. Utilizza il pulsante **Aggiungi** per aggiungere prompt dall’elenco. Inoltre, puoi aggiungere prompt e categorie in blocco utilizzando **Aggiungi tutto**.
   ![Aggiungi prompt](/help/dashboards/assets/add-prompts.png)
1. Dopo aver completato la selezione, fai clic su **Salva** nel messaggio di notifica.

#### Visualizza le query aggiunte nell’elenco dei prompt {#prompts-list}

Una volta aggiunta una query, questa appare nella scheda [Prompt](#prompts-brand) all’interno della dashboard Configurazione cliente (navigazione classica) oppure in **Gestione prompt** (Esperienza incentrata sul brand). I prompt provenienti da Google Search Console sono contrassegnati da un’icona di Google Search Console nella colonna **Origine**. L’icona ti aiuta a distinguere i prompt basati sul comportamento di ricerca effettivo dell’utente da quelli aggiunti manualmente o provenienti da altre fonti.

### Domande frequenti {#gsc-faq}

D: Con quale frequenza vengono aggiornati i prompt nella dashboard di Google Search Console?

I prompt provenienti da Google Search Console vengono generalmente aggiornati una volta al mese. Ogni aggiornamento recupera i dati più recenti delle query di ricerca dalla tua Google Search Console, riesegue la pipeline di generazione e aggiorna il set di prompt. Ciò garantisce che i prompt rimangano in linea con le tendenze di ricerca attuali e con i cambiamenti stagionali nel comportamento degli utenti.

D: Quanti prompt vengono in genere originati da Google Search Console?

Il numero dipende dalle dimensioni della distribuzione e dalla quantità di categorie tracciate. Ad esempio:

| Categorie | Argomenti totali | Prompt inviati |
|---------|----------|----------|
| 1-2 | 3-8 | Circa 65-180 |
| 4-5 | 12-20 | Circa 270-450 |
| 10 | 30-40 | Circa 675-900 |

Il nostro obiettivo è quello di fornire set di prompt che soddisfino gli obiettivi di qualità comunicati durante le fasi di prova e onboarding: almeno 20 prompt per argomento, con 3-4 argomenti per categoria e un equilibrio efficace tra prompt con brand e prompt senza brand.

D: Quanto tempo dopo la connessione a Google Search Console visualizzerò i prompt provenienti da Google Search Console?

I prompt sono in genere disponibili **entro poche ore** dopo l’attivazione della connessione a Google Search Console. La pipeline estrae automaticamente i dati di ricerca, li elabora attraverso i passaggi di generazione e controllo qualità e invia il set di prompt finale a LLM Optimizer.

D: Chi può connettersi a Google Search Console?

Chiunque disponga del livello di **Proprietario** o **Autorizzazione completa** nella proprietà di Google Search Console può autorizzare la connessione. Si tratta dei livelli di autorizzazione che concedono l’accesso in lettura ai dati delle query di ricerca. In caso di dubbi sul tuo livello di autorizzazione, puoi verificarlo in **Impostazioni>Utenti** e nelle autorizzazioni di Google Search Console.

D: Posso contrassegnare i prompt come ignorati o saltati in modo da non visualizzarli nell’elenco dei prompt di Google Search Console?

Sì, puoi eliminare qualsiasi prompt che non desideri monitorare. I prompt eliminati vengono rimossi dall’elenco dei prompt attivi e non verranno visualizzati nei rapporti futuri. Se un prompt eliminato viene rigenerato in un successivo aggiornamento mensile, puoi rimuoverlo nuovamente.

D: Una volta aggiunti i prompt di Google Search Console al mio elenco di prompt, entro quanto tempo vedrò i dati sulla presenza del brand per questi prompt?

I dati sulla presenza del brand per i prompt aggiunti di recente verranno visualizzati durante il successivo aggiornamento dei dati pianificato, che in genere viene eseguito all’inizio di ogni settimana. A seconda del momento in cui si aggiungono i prompt, è possibile che i risultati vengano visualizzati entro pochi giorni.
