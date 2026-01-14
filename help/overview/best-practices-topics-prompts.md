---
title: Best practice per categorie, argomenti, prompt e altri
description: Ottimizza le informazioni di LLM configurando categorie, argomenti, prompt e altri marchi da monitorare, inclusa la concorrenza, per il monitoraggio del marchio personalizzato e l’analisi strategica dei contenuti.
feature: Best Practices, Customer Configuration
source-git-commit: f6d33387337ca097747407099891cbc6b586b9bb
workflow-type: tm+mt
source-wordcount: '1417'
ht-degree: 0%

---


# Best practice per configurare categorie, argomenti, prompt e altri per il tracciamento

Questa sezione descrive le best practice per decidere come impostare categorie, argomenti, prompt e altri da monitorare. Include inoltre informazioni sulla libreria Prompt di settore, sviluppata da Adobe con un&#39;ampia ricerca condotta con esperti del settore.

Si tratta di un primo passo fondamentale. Le decisioni prese determinano il modo in cui le informazioni vengono adattate al contesto aziendale. Eventuali modifiche apportate alle categorie in futuro reimposteranno i dati storici.

Nel dashboard [[!UICONTROL Configurazione cliente]](/help/dashboards/customer-configuration.md) puoi definire in che modo il tuo marchio verrà monitorato e analizzato nella piattaforma di ottimizzazione LLM. Per informazioni su come utilizzare la dashboard, consulta [[!UICONTROL Configurazione del cliente]](/help/dashboards/customer-configuration.md).

![Finestra di configurazione del cliente](/help/assets/best-practices/customer-configuration-best-practices.png)

Nel dashboard [!UICONTROL Configurazione cliente], puoi personalizzare le categorie (ad esempio, business unit o linee di prodotti), tenere traccia di altri marchi e aggiungere alias di menzione del brand per acquisire tutte le varianti del brand nei prompt. Questa configurazione garantisce che la piattaforma personalizzi le informazioni sul contesto aziendale, consentendo un’analisi accurata del traffico, delle opportunità e della visibilità.

## Libreria dei prompt di settore

Per aiutarti a iniziare con prompt e argomenti, Adobe ha creato una libreria Prompt di settore sviluppata attraverso approfondite ricerche con esperti del settore e analisi del comportamento di ricerca di intelligenza artificiale in oltre 6.000 clienti. Questa libreria identifica gli argomenti e i prompt più rilevanti in base alle tendenze specifiche del settore, agli obiettivi aziendali convalidati e ai modelli di ricerca dei clienti nel mondo reale.

Per utilizzare la libreria dei prompt di settore:

1. Passa alla dashboard **Configurazione cliente**.
1. Selezionare **Scarica libreria richieste** per scaricare il file della libreria da LLM Optimizer.
   ![Download della libreria di richieste di settore](/help/assets/best-practices/customer-configuration-prompts-library.png)
1. Rivedi **Argomenti** e **Prompts** suggeriti per il settore del tuo marchio nella relativa scheda e scegli le opzioni più rilevanti.
1. Rivedi **Colonna fase Percorso clienti** per visualizzare le opzioni dei prompt nel ciclo di vita del cliente (ad esempio, individuazione per la conversione in conservazione). I prompt early stage/top di funnel sono altamente prioritari, ma anche prendere in considerazione opzioni di fase successiva per promuovere la conservazione, abilitare l’assistenza clienti e così via.
1. Modifica gli argomenti o i prompt in base alle esigenze per supportare al meglio i tuoi obiettivi e obiettivi prima di caricare gli argomenti e i prompt in Adobe LLM Optimizer (ad esempio, aggiungi il nome del tuo marchio o prodotto e aggiungi la terminologia del tuo marchio). I prompt possono essere aggiunti a LLM Optimizer manualmente o tramite il caricamento in blocco utilizzando il modello *.csv* fornito.

>[!TIP]
>
> Utilizza una combinazione di prompt specifici del dominio consigliati da LLM Optimizer durante la configurazione iniziale e dalla libreria dei prompt di settore per curare la tua strategia dei prompt.

### Base di ricerca della Libreria Prompt

La libreria Industry Prompt è stata sviluppata attraverso un&#39;iniziativa di ricerca completa che combina:

* **Informazioni sui clienti:** analisi del comportamento e delle preferenze di ricerca di IA in oltre 6.000 clienti
* **Competenze del settore:** prospettive di esperti nei settori Auto, Financial Services, Healthcare, Telecom e Travel.
* **Informazioni basate sui dati:** identificazione di argomenti ad alto impatto e modelli di query che determinano il coinvolgimento e la conversione dei clienti.

Argomenti principali ricercati dai clienti nei diversi settori:

* **Auto:** Risoluzione dei problemi relativi all&#39;auto, confronto tra veicoli e finanziamento/leasing
* **Servizi finanziari:** ricerca prodotti finanziari
* **Sanità:** ricerca di sintomi o problemi di salute, confronto delle opzioni di trattamento, comprensione dei risultati di laboratorio o dei termini medici
* **Telecomunicazioni:** Confronto tra piani, termini di contratto e promozioni, verifica del servizio nell&#39;area locale
* **Viaggi:** Preparazione al viaggio, Ricerca e prenotazione del viaggio

Tendenze dei clienti sulla ricerca di IA e sul comportamento dei prompt negli strumenti LLM:

* I clienti preferiscono porre domande anziché utilizzare parole chiave durante l’utilizzo degli strumenti di ricerca LLM.
* Utilizzano principalmente strumenti di ricerca LLM per la ricerca e la scoperta in fase iniziale.
* I clienti tendono a menzionare un marchio o un nome di prodotto specifico nelle loro richieste.

## Best practice per le categorie

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

![Aggiunta di categorie in LLM Optimizer](/help/assets/best-practices/add-category.png)

>[!IMPORTANT]
>
> * Scegli un approccio e attieniti ad esso.
> * Puoi avere solo **un** modello di categoria per account/marchio. Non combinare **SBU** e **URL_DIR** contemporaneamente.
<!--Can you mix Product/Service with these?-->

Esempio:

| Tipo di sito | Categoria | Esempi di tassonomia degli argomenti |
|---------|----------|---------|
| Aziende con più aziende | SBU | Serie di intenti di piccole dimensioni (procedure, risoluzione dei problemi, confronto, prezzi, criteri) |
| Documentazione/supporto pesante del sito | URL_DIR | Procedure, risoluzione dei problemi, riferimenti e note sulla versione |
| Catalogo eCommerce/Services | Prodotto/Servizio | Confronto, Recensioni, Prezzi/Disponibilità, Procedure, Risoluzione dei problemi |

## Best practice per gli argomenti

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
* Aziendale/News (se ne hai davvero bisogno)

![Aggiunta di argomenti in LLM Optimizer](/help/assets/best-practices/add-topic.png)

Durante la creazione dell’elenco, considera quanto segue:

* Un editor è in grado di comprendere l’argomento in 5 secondi dal testo del prompt? In caso contrario, rinominare/semplificare.
* Un team diverso sarà proprietario della correzione per argomenti diversi? Se sì, sono stati selezionati argomenti utili.
  <!-- Last bullet point does not make sense. Clarification needed. Also not sure what is meant by "editor"?-->

Alcuni utili suggerimenti aggiuntivi:

* Utilizza la conoscenza della tua azienda o del tuo sito per definire argomenti in linea con gli obiettivi strategici del tuo marchio
* Considera il confronto tra il tuo brand e altri brand all’interno di argomenti specifici.

>[!IMPORTANT]
>
> * Mantieni gli argomenti basati sulle finalità, non organizzativi.
> * Non aggiungere categorie/filtri per marchio/non marchio/area geografica, in quanto è possibile filtrare specificamente per questo nella scheda **[!UICONTROL Marchi]**.
> * Gli argomenti sono suddivisi in diverse categorie. **impossibile** definire argomenti univoci per ogni categoria.
> * Un singolo prompt **can** esiste in diversi argomenti o categorie.

## Best practice per i prompt

I prompt identificano le domande o le query specifiche poste dai clienti, che possono avere un impatto sull&#39;azienda. Si tratta di domande o query effettive che gli utenti inseriscono nei moduli LLM.

Assicurati di rivedere e aggiornare regolarmente i prompt per garantire che siano in linea con le esigenze dei clienti e gli obiettivi aziendali.

Best practice per i prompt:

* Raggruppa i prompt simili in base alle domande degli utenti.
* Concentrati sui prompt più importanti per i tuoi clienti.
* Controlla se il tuo marchio ha buone probabilità di essere menzionato per determinati prompt.

>[!TIP]
>
>* Puoi utilizzare strumenti come Adobe LLM Optimizer e Google Search Console con filtri regex per identificare strutture di domande comuni (ad esempio, &quot;come&quot;, &quot;cosa&quot;, &quot;quando&quot;, &quot;dove&quot;) e scoprire quali prompt vengono utilizzati dalle persone per visitare il tuo sito.
>* Per scoprire quali prompt sono rilevanti per il sito o il brand, puoi utilizzare i dati di ricerca nel sito, le domande frequenti nelle pagine dei risultati dei motori di ricerca o anche chiedere direttamente ai chatbot LLM quali domande i clienti potrebbero porre sul brand.

## Best practice per tenere traccia di altri marchi

Il tracciamento di Altri consente di monitorare la visibilità e le menzioni nelle risposte LLM per i prompt e gli argomenti importanti per la propria attività.

La scheda [!UICONTROL **Tracciamento altri**] ti consente di aggiungere altri, inclusi i concorrenti, per tenere traccia della loro visibilità per prompt e argomenti specifici.

Con il tracciamento di altri utenti, puoi vedere con quale frequenza vengono menzionati altri marchi insieme al tuo marchio in diverse aree geografiche e categorie e confrontarne la visibilità con la tua.

>[!TIP]
>
>Rivedi regolarmente le menzioni dei concorrenti o di altri per identificare le aree in cui il tuo marchio può migliorare.

## Ulteriori informazioni

* [Il dashboard Configurazione cliente](/help/dashboards/customer-configuration.md) è il luogo in cui puoi configurare il tracciamento di categorie, argomenti, prompt e altri.
* [Best practice per LLM Optimizer](/help/tutorials/best-practices.md) descrive le best practice per l&#39;ottimizzazione LLM

