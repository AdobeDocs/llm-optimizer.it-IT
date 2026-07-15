---
title: Configurazione cliente
description: Utilizza la configurazione cliente per definire in che modo il tuo brand verrà monitorato e analizzato all’interno della piattaforma LLM Optimizer.
feature: Customer Configuration
autotag-review: '2026-07-15T17:48:20.742Z'
TQID: 'https://experienceleague.adobe.com/BvaFF-pMzojy1TNZvCQQRbcT5c5AQ75OqjclmDi14Z0'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: c898dfb2-0885-42fb-b2af-b2d756752646id: d1956731-2adb-4bb7-8301-2b239254ac72id: e1b649f0-0a61-46e4-9082-64d5cb2576c6
subfeature_v2: id: e69d5a42-0217-4ca5-9396-a9a826a170da
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: aa2f3246-cb95-4b30-8899-fdf7d73550ccid: cdd65e7e-8839-44a2-bc21-0e03623b5dd1id: e1e0219c-f879-479f-8427-888ed2a6e9c2id: eddd9b14-83bd-4ff4-9072-54a4a484abb7id: fc314d1d-7cb9-4a38-8dbd-8f9b6478f40d
source-git-commit: 2705cf26faea9c09817bbdcec4b4c531552df7ba
workflow-type: tm+mt
source-wordcount: 3935
ht-degree: 57%

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
* [Suggerimenti rapidi basati su tentativi di citazione e Traffico da referral](#prompt-suggestions)

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

## Suggerimenti rapidi basati su tentativi di citazione e Traffico da referral {#prompt-suggestions}

Invece di indovinare quali prompt hanno importanza, **Suggerimenti prompt** partono da quali agenti e utenti di IA stanno già accedendo o sono a cui si fa riferimento sul tuo sito.

Adobe LLM Optimizer analizza i dati CDN per identificare le pagine a cui gli agenti di IA accedono già in modo coerente (tentativi di citazione) e a cui gli utenti fanno riferimento (traffico da referral LLM). Successivamente, genera automaticamente suggerimenti di prompt in base alle lacune nella copertura dei prompt corrente. Invece di indovinare quali URL assegnare la priorità e quali prompt creare, il flusso di lavoro inizia da veri e propri segnali di traffico: pagine a cui gli agenti stanno già cercando di accedere e che poi definiscono il tipo di prompt utente a cui dovrebbero rispondere tali pagine.

Quando gli agenti AI accedono già in modo coerente a una pagina, la domanda non è come far sì che gli agenti sappiano della pagina, ma a quali domande il contenuto della pagina potrebbe rispondere. Senza i prompt configurati per queste pagine, non hai alcuna visibilità su come il tuo brand viene visualizzato nelle risposte AI sugli argomenti più importanti. Suggerimenti prompt da Agentic Traffic (Traffico agente) consente di colmare questo gap e iniziare a monitorare e migliorare la visibilità dei brand delle pagine in cui gli agenti sono già più attivi.

>[!NOTE]
>
> Nella [esperienza incentrata sul marchio](/help/overview/quick-start.md#brand-centric-experience), i suggerimenti dei prompt vengono visualizzati nella sezione **Gestione dei prompt**.

### Come funziona {#prompt-suggestions-how-it-works}

Il flusso di lavoro Suggerimenti prompt viene eseguito in quattro passaggi, trasformando i segnali di traffico CDN in suggerimenti di prompt pronti per la configurazione. Ogni passaggio si basa su quello precedente: partendo da pagine in cui l’attività dell’agente IA è già stata dimostrata, comprendendo a cosa servono tali pagine, verificando ciò che è già coperto e generando prompt specifici, fondati e pronti per la pubblicazione.

![Suggerimenti dal flusso di lavoro Traffico agente](/help/dashboards/assets/prompt-suggestions-workflow.png)

#### Passaggio 1 — Identificare le pagine a segnale elevato dal traffico agente {#prompt-suggestions-step-1}

La pipeline inizia identificando le pagine del sito con cui i sistemi di intelligenza artificiale sono già attivamente coinvolti, utilizzando due segnali provenienti dai dati CDN: con quale frequenza i sistemi di intelligenza artificiale accedono alle pagine come origine e rispondono a domande reali degli utenti; e se tali pagine stanno già spingendo utenti reali verso il sito dalle risposte generate dall’intelligenza artificiale.

* **Tentativi**: il modo in cui i sistemi di intelligenza artificiale accedono a una pagina come potenziale origine durante la risposta alle domande dell&#39;utente. La pipeline cerca le pagine che mostrano un’attività coerente per i tentativi di citazione, settimana per settimana, fornendo un’immagine più olistica di interesse rispetto a un singolo punto nel tempo.
* **traffico da referral LLM**: istanze in cui un utente ha fatto clic da una risposta generata da IA per passare all&#39;URL. La pipeline si concentra sui dati di riferimento più recenti e assegna priorità alle pagine con il maggior volume di visite guidate dall’intelligenza artificiale, garantendo che i suggerimenti si fondino su modelli di consigli di intelligenza artificiale attuali e collaudati.

| Segnale | Significato |
|--------|---------------|
| Solo tentativi di citazione | Gli agenti accedono regolarmente a questa pagina come potenziale sorgente |
| Solo traffico da referral LLM | Gli agenti stanno inviando attivamente gli utenti a questa pagina |
| Entrambi | Gli agenti vi accedono e gli utenti fanno clic — il target con la massima affidabilità |

Una pagina può essere qualificata tramite segnale o entrambi. Le pagine che mostrano entrambi i segnali rappresentano i target con la massima affidabilità per la generazione immediata.

#### Passaggio 2 — Analizzare il contenuto e le finalità della pagina {#prompt-suggestions-step-2}

Per ogni pagina qualificata, la pipeline legge il contenuto della pagina e:

* **Riepiloga** il documento in una descrizione concisa e basata sui fatti che diventa la base di tutto ciò che segue.
* **Classifica** il tipo di pagina, che si tratti di un prodotto, una risorsa, un supporto o un hub.
* Identifica l&#39;**intento di percorso primario**, ovvero il tipo di domanda a cui la pagina è meglio posizionata per rispondere, ad esempio informativa, istruttiva, comparativa o transazionale.

Le due classificazioni funzionano insieme. Ad esempio, i prompt generati da una pagina di supporto come una guida alla configurazione o un tutorial hanno più probabilità di essere rilevanti per un utente tipo esistente rispetto a un nuovo pubblico.

#### Passaggio 3 — Controllare la copertura del prompt esistente {#prompt-suggestions-step-3}

Prima di generare qualsiasi nuova pagina, la pipeline controlla se ogni pagina qualificata è già coperta da prompt configurati nel tuo account LLM Optimizer, in esecuzione in due passaggi:

1. Scansione per similarità semantica che identifica rapidamente i prompt candidati provenienti dalla libreria di prompt esistente che sono potenzialmente correlati alla pagina.
2. Una revisione basata su LLM che valuta l’allineamento di ciascun candidato al prompt con il contenuto della pagina, non solo se è correlato a livello topico, ma anche se copre l’aspetto della pagina.

Una pagina è considerata coperta se almeno un prompt esistente soddisfa tale soglia. Le pagine che non presentano una corrispondenza adeguata vengono identificate come spazi vuoti e passano al passaggio 4.

#### Passaggio 4: generazione, controllo qualità e richiesta di classificazione per URL {#prompt-suggestions-step-4}

![Generazione dei prompt e controllo qualità](/help/dashboards/assets/prompt-suggestions-generation.png)

Per ogni pagina vuota, la pipeline genera prompt dal suono naturale e basati sulla descrizione del contenuto della pagina. Inizia con l&#39;identificare i personaggi rilevanti — qualcuno che realisticamente farebbe domande a cui questa pagina risponde e costruisce uno scenario realistico intorno a quell&#39;individuo prima di generare i candidati prompt.

Ogni prompt viene sottoposto a un controllo automatico della qualità suddiviso in tre dimensioni:

* Indica se la pagina è **specifica** anziché una domanda generica che può essere applicata a qualsiasi pagina della categoria.
* Indica se la pagina è **messa a terra** nel contenuto effettivo.
* Indica se può sembrare qualcosa che un **utente reale** digiterebbe in uno strumento di intelligenza artificiale come ChatGPT.

I prompt che non superano questa revisione vengono riscritti con un feedback specifico e riesaminati. Se ancora non passano, cadono.

Il passaggio finale è un controllo di diversità, le richieste tra URL troppo simili tra loro vengono eliminate dall’elenco finale. Ogni prompt viene contrassegnato con l&#39;argomento e la categoria preconfigurati e include un campo di ragionamento che spiega perché l&#39;URL di origine è stato oggetto di targeting in base ai segnali di tentativo di citazione e di traffico da referral. Ai prompt viene inoltre assegnata una classificazione di priorità che consente di sapere su quali suggerimenti agire per primi; una priorità più elevata significa un segnale di IA combinato più forte proveniente dall’URL sorgente. I prompt sono quindi pronti per essere esaminati nella scheda **Suggerimenti prompt** della dashboard Configurazione cliente.

### Procedura di utilizzo {#prompt-suggestions-how-to-use}

1. Apri il dashboard **Configurazione cliente** e passa alla scheda **Suggerimenti prompt**.
1. Utilizza il filtro **Source** per selezionare **Tentativo di citazione** per visualizzare i suggerimenti generati dal traffico agente.
1. Rivedi le colonne **Motivazione** e **Priorità** per valutare ogni suggerimento.
1. Seleziona i prompt da aggiungere e fai clic su **Aggiungi selezione** per aggiungerli ai prompt configurati.

![Scheda Suggerimenti richiesta con filtro di origine Tentativo di citazione](/help/dashboards/assets/prompt-suggestions-citation-attempt.png)

![Aggiungi suggerimenti prompt selezionati](/help/dashboards/assets/prompt-suggestions-add-selection.png)

### Domande frequenti {#prompt-suggestions-faq}

D: La mia organizzazione ha bisogno di una configurazione aggiuntiva per utilizzare questa funzione?

Questa funzione si basa sui dati di registro CDN. Se hai già abilitato [l&#39;inoltro del registro CDN](#cdn-configuration), non è necessaria alcuna configurazione aggiuntiva. Senza i registri CDN, i dati relativi ai tentativi di citazione o al traffico da referral non saranno disponibili per l’analisi.

D: Perché un URL specifico non viene visualizzato nei suggerimenti?

Ci sono alcuni motivi comuni. La pagina potrebbe non avere ancora un’attività di recupero di IA coerente o un traffico da referral significativo; senza uno di questi segnali, non entra nella pipeline. Potrebbe già essere coperta da un prompt configurato esistente poiché la pipeline genera solo suggerimenti per spazi vuoti reali. Oppure il tipo di pagina potrebbe non essere idoneo per la generazione di prompt.

D: I suggerimenti possono cambiare nel tempo?

Sì. La pipeline viene eseguita periodicamente quando diventano disponibili nuovi dati CDN. Man mano che il comportamento di utente e agente si evolve (quali pagine vengono accessibili, con quale frequenza e quali sono i fattori che determinano il traffico da referral), i suggerimenti riflettono tali modifiche. Le pagine che prima non erano a segnale elevato potrebbero qualificarsi nelle esecuzioni future e le lacune esistenti che sono state corrette non genereranno più nuovi suggerimenti.

D: perché trovo URL che non mi aspettavo nei suggerimenti?

Gli URL visualizzati si basano interamente sul comportamento degli agenti osservati, pagine a cui i sistemi di intelligenza artificiale accedono regolarmente o alle quali indirizzano gli utenti, indipendentemente da quanto siano prominenti nella strategia dei contenuti. In alcuni casi, potrebbero essere pagine che non hai mai considerato importanti, ma per le quali l’intelligenza artificiale ha ripetutamente raggiunto. Se nei suggerimenti viene visualizzato un URL, è perché i dati lo supportano. Sei sempre libero di ignorare i suggerimenti che non si adattano alla tua strategia, ma i dati dietro ogni suggerimento si basano su una vera attività di intelligenza artificiale.

D: Cosa significa il campo di ragionamento?

Ogni prompt include una spiegazione del motivo per cui il relativo URL di origine è stato elencato come suggerimento. Per le pagine che si qualificano tramite tentativi di citazione, viene mostrato come la pagina viene classificata tra tutte le pagine a cui si accede in base ai tentativi settimanali. Per le pagine che si qualificano tramite il traffico da referral, viene visualizzato lo stesso per le visualizzazioni pagina di riferimento. Le pagine con entrambi i segnali mostrano entrambi. Questo consente di comprendere la priorità e scegliere quali suggerimenti pubblicare per primi.

Per una pagina con entrambi i segnali, il ragionamento potrebbe essere simile al seguente: *Generato per [URL pagina] — si classifica nel 3% dei primi tentativi di citazione settimanali mediani e nell&#39;1% dei primi tentativi di citazione per traffico da referral LLM.*

D: Come viene determinata la priorità?

La priorità si basa su un punteggio combinato di due segnali: il modo in cui una pagina viene classificata tra tutte le pagine in base ai tentativi di citazione e il modo in cui viene classificata tra tutte le pagine in base alle visualizzazioni delle pagine di riferimento LLM. Entrambi sono espressi come percentili e sommati, pertanto le pagine con un punteggio elevato su entrambi i segnali risalgono naturalmente all’inizio. Una pagina a cui AI accede e invia utenti in modo coerente, sarà sempre più in alto di una pagina con un solo segnale.

D: In che modo la pipeline decide quali pagine sono idonee in base ai tentativi di citazione?

La pipeline cerca le pagine che mostrano un’attività di recupero dell’intelligenza artificiale coerente nel tempo. Per essere idonea, una pagina deve soddisfare due condizioni: deve mostrare un’attività significativa in almeno metà delle settimane nei dati disponibili e il suo conteggio mediano degli hit agentici durante tali settimane attive deve rientrare nel primo 25% in tutte le pagine. Entrambe le condizioni devono essere soddisfatte: la sola frequenza non è sufficiente e nemmeno il volume degli hit è sufficiente.

D: In che modo la pipeline decide quali pagine sono idonee in base al traffico da referral?

Una pagina è idonea se viene visualizzata nel primo 10% di tutte le pagine per numero totale di visite di riferimento LLM negli ultimi tre mesi. In questo modo i suggerimenti si basano su pagine che stanno già generando un click-through reale e misurabile dalle risposte AI, in base al comportamento recente.

D: I suggerimenti dei prompt sono disponibili in lingue diverse dall’inglese?

Non ancora. Al momento la pipeline genera prompt solo in inglese. In una versione futura verrà aggiunto il supporto multilingue.
