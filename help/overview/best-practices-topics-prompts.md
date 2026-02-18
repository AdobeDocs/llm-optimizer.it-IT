---
title: Best practice per categorie, argomenti, prompt e altri brand
description: Ottimizza gli insight LLM configurando categorie, argomenti, prompt e altri brand da tracciare, inclusa la concorrenza, per il monitoraggio personalizzato del brand e l’analisi strategica dei contenuti.
feature: Best Practices, Customer Configuration
source-git-commit: f6d33387337ca097747407099891cbc6b586b9bb
workflow-type: ht
source-wordcount: '1435'
ht-degree: 100%

---


# Best practice per configurare categorie, argomenti, prompt e altri brand da tracciare

Questa sezione descrive le best practice per decidere come impostare categorie, argomenti, prompt e altri brand da tracciare. Include inoltre informazioni sulla libreria di prompt di settore, sviluppata da Adobe con un’ampia ricerca condotta con la collaborazione di esperti del settore.

Si tratta di un primo passo fondamentale. Le decisioni prese determinano il modo in cui le informazioni vengono adattate al contesto del tuo business. Eventuali modifiche future apportate alle categorie reimposteranno i dati storici.

Nella dashboard [[!UICONTROL Configurazione cliente]](/help/dashboards/customer-configuration.md) puoi definire in che modo il tuo brand verrà monitorato e analizzato nella piattaforma LLM Optimizer. Per informazioni su come utilizzare la dashboard, consulta [[!UICONTROL Configurazione cliente]](/help/dashboards/customer-configuration.md).

![Finestra Configurazione cliente](/help/assets/best-practices/customer-configuration-best-practices.png)

Nella dashboard [!UICONTROL Configurazione cliente], puoi personalizzare le categorie (ad esempio, unità di business o linee di prodotti), tenere traccia di altri brand e aggiungere alias di menzione del brand per acquisire tutte le varianti del tuo brand nei prompt. Grazie a questa configurazione, la piattaforma è in grado di personalizzare gli insight in base al contesto del tuo business, per un’analisi accurata della visibilità, del traffico e delle opportunità.

## Libreria di prompt di settore

Per aiutarti a iniziare con prompt e argomenti, Adobe ha creato una libreria di prompt di settore sviluppata attraverso un’ampia ricerca con la collaborazione di esperti del settore e l’analisi del comportamento delle ricerche IA su oltre 6.000 clienti. Questa libreria identifica gli argomenti e i prompt più rilevanti in base alle tendenze specifiche del settore, a obiettivi di business convalidati e ai pattern di ricerca di clienti reali.

Per utilizzare la libreria di prompt di settore:

1. Passa alla dashboard **Configurazione cliente**.
1. Seleziona **Scarica libreria prompt** per scaricare il file della libreria da LLM Optimizer.
   ![Download della libreria di prompt di settore](/help/assets/best-practices/customer-configuration-prompts-library.png)
1. Rivedi gli **Argomenti** e i **Prompt** suggeriti per il settore del tuo brand nella relativa scheda e scegli le opzioni più rilevanti.
1. Rivedi la **colonna Fase percorso cliente** per visualizzare le opzioni dei prompt lungo il ciclo di vita del cliente (ad esempio, dall’individuazione alla conversione fino alla conservazione). I prompt della fase iniziale/alta del funnel hanno priorità elevata, ma considera anche le opzioni per le fasi successive per promuovere la conservazione, abilitare l’assistenza clienti e così via.
1. Modifica gli argomenti o i prompt in base alle esigenze per supportare al meglio i tuoi obiettivi prima di caricare gli argomenti e i prompt in Adobe LLM Optimizer; ad esempio, aggiungi il nome del tuo brand o dei tuoi prodotti, aggiungi la terminologia in linea con il brand, e così via. Puoi aggiungere i prompt a LLM Optimizer manualmente o tramite il caricamento in blocco utilizzando il modello *.csv* fornito.

>[!TIP]
>
> Per curare la tua strategia di prompt, utilizza una combinazione di prompt specifici del dominio consigliati da LLM Optimizer durante la configurazione iniziale, e prompt dalla libreria di prompt di settore.

### Ricerche alla base della libreria di prompt

La libreria di prompt di settore è stata sviluppata attraverso un’iniziativa di ricerca completa che combina:

* **Informazioni sul cliente:** analisi del comportamento e delle preferenze di ricerca IA su oltre 6.000 clienti
* **Competenze di settore:** prospettive di esperti nei settori Automotive, Servizi finanziari, Assistenza sanitaria, Telecomunicazioni e Viaggi.
* **Insight basati sui dati:** identificazione di argomenti a impatto elevato e modelli di query che promuovono il coinvolgimento e la conversione di clienti.

Argomenti principali ricercati da clienti nei diversi settori:

* **Automotive:** risoluzione di problemi relativi alle auto, confronto tra veicoli e finanziamento/leasing
* **Servizi finanziari:** ricerca di prodotti finanziari
* **Assistenza sanitaria:** ricerca di sintomi o problemi di salute, confronto delle opzioni di trattamento, comprensione dei referti di laboratorio o di termini medici
* **Telecomunicazioni:** confronto tra piani, termini di contratto e promozioni, verifica del servizio nell’area locale
* **Viaggi:** preparazione al viaggio, ricerca e prenotazione del viaggio

Tendenze nel comportamento di ricerca IA e nei prompt in strumenti LLM da parte di clienti:

* Quando utilizzano strumenti di ricerca LLM, gli utenti preferiscono porre domande anziché utilizzare parole chiave.
* Utilizzano principalmente gli strumenti di ricerca LLM nelle fasi iniziali di ricerca e individuazione.
* Nei prompt, tendono a menzionare un brand o un nome di prodotto specifico.

## Best practice per le categorie

Le categorie consentono di organizzare i contenuti in unità di business strategiche o raggruppamenti logici. Rappresentano il bucket “dove si trova” e la struttura organizzativa di livello superiore per il contenuto.

Quando decidi come impostare le categorie, considera sia i tuoi obiettivi, sia chi dovrà intervenire in base ai risultati dei rapporti.

>[!IMPORTANT]
>
> Assicurati che le categorie siano impostate correttamente fin dall’inizio: eventuali modifiche apportate in un secondo tempo alle categorie, infatti, reimposteranno i dati storici. In altre parole, se apporti delle modifiche, perderai i dati storici precedenti alla modifica.

Di seguito trovi una panoramica dei tipi di approcci possibili e quando scegliere un particolare approccio:

| Approccio | Descrizione | Vantaggio |
|---------|----------|---------|
| Unità di business strategica (SBU) | Utilizza questo approccio se l’organizzazione è divisa per P&amp;L (ad esempio: Consumer, Enterprise, Servizi). | Puoi ottenere rapporti chiari per linea di business e agevolare la rendicontazione. |
| Directory di livello superiore del sito web (URL_DIR) | Da utilizzare se l’architettura delle informazioni presenti nel tuo sito ne rispecchia anche i relativi responsabili: /products/, /support/, /docs/, /news/. | Ottieni l’allineamento con il modo in cui i vari team pubblicano e gestiscono i contenuti. |
| Categoria di prodotti (o servizi) | Utilizza questo approccio se offri un catalogo (di SKU/servizi). | Ottieni visualizzazioni dell’assortimento, analisi del divario e risposte a domande tipo “quale categoria necessita di contenuti?”. |

Per decidere come impostare le categorie, rispondi a questa domanda: **Chi dovrà intervenire sui risultati che emergono dai rapporti?**

* Se sei un *responsasile business*, scegli l’approccio **SBU**.
* Se sei *responsabile per il sito web o i contenuti*, scegli l&#39;approccio **URL_DIR**.
* Se sei un *responsabile di merchandising/offerte*, scegli l’approccio **categorie di prodotti/servizi**.

![Aggiunta di categorie in LLM Optimizer](/help/assets/best-practices/add-category.png)

>[!IMPORTANT]
>
> * Scegli un approccio e attieniti ad esso.
> * Puoi avere **un** solo modello di categorie per account o brand. Non combinare **SBU** e **URL_DIR** allo stesso tempo.
<!--Can you mix Product/Service with these?-->

Esempio:

| Tipo di sito | Categoria | Esempi di tassonomia degli argomenti |
|---------|----------|---------|
| Aziende con più business | SBU | Piccoli set di intenti (procedure, risoluzione dei problemi, confronto, prezzi, criteri) |
| Sito con molta documentazione/supporto | URL_DIR | Procedure, risoluzione dei problemi, riferimenti e note sulla versione |
| Catalogo e-commerce/servizi | Prodotti/Servizi | Confronto, recensioni, prezzi/disponibilità, procedure, risoluzione dei problemi |

## Best practice per gli argomenti

Gli argomenti consentono di comprendere l’intento dell’utente, ovvero mostrano ciò che l’utente desidera. Consentono di raggruppare i prompt con intenti dell’utente simili. In pratica, rappresentano insiemi di prompt rilevanti.

>[!IMPORTANT]
>
>Gli argomenti sono universali per **tutte** le categorie, ovvero rimangono coerenti indipendentemente dalla categoria a cui sono assegnati. Rappresentano insiemi di domande o prompt che condividono un intento comune.

Per decidere quali argomenti adottare, crea un breve elenco semplice (massimo 6-12). Ad esempio:

* Prodotti/servizi
* Procedure (configurazione/utilizzo)
* Risoluzione dei problemi (errori/problemi)
* Confronto (X rispetto a Y; “migliore ... per ...”)
* Recensioni e valutazioni
* Prezzi e disponibilità
* Criteri e garanzia
* Contatta l’assistenza
* Azienda/News (se ne hai davvero bisogno)

![Aggiunta di argomenti in LLM Optimizer](/help/assets/best-practices/add-topic.png)

Quando crei l’elenco di argomenti, considera quanto segue:

* Un editor è in grado di comprendere in 5 secondi l’argomento, in base al testo del prompt? In caso contrario, semplifica o cambia il nome dell’argomento.
* Un team diverso si occuperà della correzione di argomenti diversi? Se sì, hai scelto argomenti utili.
  <!-- Last bullet point does not make sense. Clarification needed. Also not sure what is meant by "editor"?-->

Alri suggerimenti utili:

* Utilizza la conoscenza del tuo business o sito per definire argomenti in linea con gli obiettivi strategici del tuo brand.
* Considera come si colloca il tuo brand rispetto ad altri brand per argomenti specifici.

>[!IMPORTANT]
>
> * Mantieni gli argomenti basati sull’intento, non organizzativi.
> * Non aggiungere categorie ofiltri per brand/non brand/area geografica, in quanto puoi applicare appositi filtri nella scheda **[!UICONTROL Brand]**.
> * Gli argomenti coprire diverse categorie. **Non puoi** definire argomenti univoci per ogni categoria.
> * Un singolo prompt **può** esistere in diversi argomenti o categorie.

## Best practice per i prompt

I prompt identificano domande specifiche poste dalla clientela, che possono avere un impatto sul tuo business. Si tratta di domande o richieste effettive che gli utenti inseriscono nelle ricerche LLM.

Rivedi e aggiorna regolarmente i prompt affinché siano sempre in linea con le esigenze della clientela e gli obiettivi di business.

Best practice per i prompt:

* Raggruppa i prompt simili in base alle domande poste delle persone.
* Concentrati sui prompt più importanti per la tua clientela.
* Controlla se il tuo brand ha buone probabilità di essere menzionato per determinati prompt.

>[!TIP]
>
>* Puoi utilizzare strumenti come Adobe LLM Optimizer e Google Search Console con filtri regex per identificare strutture di domande comuni, ad esempio, “come”, “cosa”, “quando”, “dove”, e scoprire quali sono i prompt utilizzati dalle persone per visitare il tuo sito.
>* Per scoprire i prompt rilevanti per il tuo sito o brand, puoi utilizzare i dati sulle ricerche nel sito, le domande frequenti nelle pagine dei risultati dei motori di ricerca o chiedere direttamente ai chatbot LLM quali domande la clientela potrebbe porre sul tuo brand.

## Best practice per il tracciamento di altri brand

Il tracciamento di altri brand consente di monitorare la visibilità e le menzioni nelle risposte LLM per i prompt e gli argomenti importanti per tuo business.

La scheda [!UICONTROL **Tracciamento altri**] ti consente di aggiungere altri brand, inclusa la concorrenza, per tenere traccia della loro visibilità per prompt e argomenti specifici.

Con il tracciamento di altri brand, puoi vedere con quale frequenza vengono menzionati insieme al tuo brand in diverse aree geografiche e categorie, e confrontarne la visibilità rispetto alla tua.

>[!TIP]
>
>Rivedi regolarmente le menzioni e le citazioni della concorrenza o di altri brand per identificare le aree di miglioramento per il tuo brand.

## Ulteriori informazioni

* La [dashboard Configurazione cliente](/help/dashboards/customer-configuration.md) consente di configurare il tracciamento di categorie, argomenti, prompt e altri brand.
* [Best practice per LLM Optimizer](/help/tutorials/best-practices.md) descrive le best practice per l’ottimizzazione LLM

