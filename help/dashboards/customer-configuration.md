---
title: Configurazione cliente
description: Utilizza la configurazione del cliente per definire in che modo il tuo marchio verrà monitorato e analizzato all’interno della piattaforma di ottimizzazione LLM.
source-git-commit: 653a6be856412faac8783fa9dc7b759a7c6e1f68
workflow-type: tm+mt
source-wordcount: '1594'
ht-degree: 0%

---


# Configurazione cliente

Nella configurazione del cliente puoi definire in che modo il brand verrà monitorato e analizzato all’interno della piattaforma di ottimizzazione LLM. Puoi personalizzare le categorie (ad esempio, business unit o linee di prodotti), tenere traccia dei concorrenti e aggiungere alias di menzione del brand per acquisire tutte le varianti del brand in tutti i prompt. Questa configurazione garantisce che la piattaforma personalizzi le informazioni sul contesto aziendale, consentendo un’analisi accurata del traffico, delle opportunità e della visibilità.

![Dashboard configurazione cliente](/help/dashboards/assets/customer-config.png)


## Best practice per la configurazione di categorie, argomenti e prompt

Questa sezione descrive le best practice per decidere come impostare categorie, argomenti, prompt e concorrenti.

Si tratta di un primo passo fondamentale. Le decisioni prese determinano il modo in cui le informazioni vengono adattate al contesto aziendale. Eventuali modifiche apportate alle categorie in futuro reimposteranno i dati storici.

### Best practice per le categorie

Le categorie consentono di organizzare i contenuti in business unit strategiche o raggruppamenti logici. Sono il bucket &quot;dove appartiene&quot; e la struttura organizzativa di livello superiore per il contenuto.

Quando decidi come impostare le categorie, prendi in considerazione i tuoi obiettivi e chi deve agire in base a ciò che stai segnalando.

>[!IMPORTANT]
>
> Assicurati che le categorie siano configurate correttamente fin dall’inizio, man mano che le modifiche apportate alle categorie reimpostano i dati storici. Ciò significa che se modifichi questi, perdi i dati storici precedenti alla modifica.

Ecco una panoramica dei tipi di approcci possibili e quando scegliere un particolare approccio:

| Approccio | Descrizione | Vantaggio |
|---------|----------|---------|
| Unità aziendale strategica (SBU) | Utilizza questo approccio se l’organizzazione è divisa per P&amp;L (ad esempio, Consumer, Enterprise, Services). | Puoi ottenere rapporti puliti per linea di business e responsabilità più semplice. |
| Directory di primo livello del sito Web (URL_DIR) | Da utilizzare se l&#39;architettura delle informazioni del sito rispecchia la proprietà (/products/, /support/, /docs/, /news/). | Ottieni l’allineamento con il modo in cui i team pubblicano e gestiscono i contenuti. |
| Categoria di prodotto (o servizio) | Utilizzalo se vendi un catalogo (SKU/servizi). | Si ottengono visualizzazioni assortimento, analisi gap e risposte &quot;quale categoria ha bisogno di contenuti&quot;. |

La modalità di impostazione delle categorie dipende da una domanda: **Chi deve intervenire sul report?**

* Se sei un *Business Leader*, scegli l&#39;approccio **SBU**.
* Se sei un *proprietario Web/contenuto*, scegli l&#39;approccio **URL_DIR**.
* Se sei un *manager di merchandising/offerte*, scegli l&#39;approccio **categoria prodotto/servizio**.

>[!IMPORTANT]
>
> * Scegli un approccio e attieniti ad esso.
> * Puoi avere solo **un** modello di categoria per account/marchio. Non combinare **SBU** e **URL_DIR** contemporaneamente.

Esempio:

| Tipo di sito | Categoria | Esempi di tassonomia degli argomenti |
|---------|----------|---------|
| Aziende con più aziende | SBU | serie di intenti di piccole dimensioni (procedure, risoluzione dei problemi, confronto, prezzi, criteri) |
| Documentazione/supporto pesante del sito | URL_DIR | Procedure, risoluzione dei problemi, riferimenti e note sulla versione |
| Catalogo eCommerce/Services | Prodotto/Servizio | Confronto, Recensioni, Prezzi/Disponibilità, Procedure, Risoluzione dei problemi |

### Best practice per gli argomenti

Gli argomenti consentono di comprendere le finalità dell&#39;utente, ovvero di mostrare ciò che l&#39;utente desidera. Consentono di raggruppare i prompt con finalità utente simili. Immaginatelo come un raggruppamento di prompt rilevanti.

>[!IMPORTANT]
>
>Gli argomenti sono universali per **tutte** le categorie, ovvero rimangono coerenti indipendentemente dalla categoria a cui sono assegnati. Rappresentano cluster di domande o prompt che condividono un intento comune.

Quando decidi gli argomenti, vuoi creare un breve elenco semplice (massimo 6-12). Ad esempio:

* Prodotti/servizi
* Procedura (configurazione/utilizzo)
* Risoluzione dei problemi (errori/problemi)
* Confronto (X vs Y; &quot;best ... for ...&quot;)
* Recensioni e valutazioni
* Prezzi e disponibilità
* Regole e garanzia
* Contatto assistenza
* Aziende / News (se ne avete veramente bisogno)

Durante la creazione dell’elenco, considera quanto segue:

* Un editor è in grado di comprendere l’argomento in 5 secondi dal testo del prompt? In caso contrario, rinominare/semplificare.
* Un team diverso sarà proprietario della correzione per argomenti diversi? Se sì, sono stati selezionati argomenti utili.

Alcuni utili suggerimenti aggiuntivi:

* Utilizza la conoscenza della tua azienda o del tuo sito per definire argomenti in linea con gli obiettivi strategici del tuo marchio
* Considera il confronto tra il tuo marchio e quello della concorrenza all’interno di argomenti specifici.

>[!IMPORTANT]
>
> * Mantieni gli argomenti basati sulle finalità, non organizzativi.
> * Non aggiungere categorie/filtri per marchio/non marchio/area geografica, in quanto è possibile filtrare specificamente per questo nella scheda **Marchi**.
> * Gli argomenti sono suddivisi in diverse categorie. È possibile **non** avere argomenti diversi per categoria.
> * Un singolo prompt può essere presente in diversi argomenti o categorie.

### Best practice per i prompt

I prompt identificano le domande o le query specifiche poste dai clienti, che possono avere un impatto sull&#39;azienda. Si tratta di domande o query effettive che gli utenti inseriscono nei moduli LLM.

Assicurati di rivedere e aggiornare regolarmente i prompt per garantire che siano in linea con le esigenze dei clienti e gli obiettivi aziendali.

>[!TIP]
>
>* Puoi utilizzare strumenti come LLM Optimizer e Google Search Console con filtri regex per identificare strutture di domande comuni (ad esempio, &quot;come&quot;, &quot;cosa&quot;, &quot;quando&quot;, &quot;dove&quot;).
>* Per scoprire quali prompt sono rilevanti per il sito o il brand, puoi utilizzare i dati di ricerca nel sito, le domande frequenti nelle pagine dei risultati dei motori di ricerca o anche chiedere direttamente ai chatbot LLM quali domande i clienti potrebbero porre sul brand.

### Best practice per i concorrenti

I concorrenti consentono di monitorare la visibilità e le menzioni nelle risposte LLM per i prompt e gli argomenti importanti per la propria attività.

La scheda [!UICONTROL **Tracciamento concorrenti**] consente di aggiungere concorrenti e di tenere traccia della loro visibilità per prompt e argomenti specifici.

Con il tracciamento dei concorrenti, puoi vedere con quale frequenza i concorrenti vengono menzionati insieme al tuo marchio in diverse regioni e categorie e confrontare la loro visibilità con la tua.

>[!TIP]
>
>Rivedi regolarmente le menzioni e le citazioni dei concorrenti per identificare le aree in cui il tuo marchio può migliorare.

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

## CDN agente {#agentic-cdn}

Non disponibile (disponibile per il rilascio?).

