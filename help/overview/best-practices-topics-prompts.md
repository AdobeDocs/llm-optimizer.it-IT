---
title: Best practice per categorie, argomenti e prompt
description: Ottimizza le informazioni di LLM configurando categorie, argomenti, prompt e concorrenti per il monitoraggio del marchio personalizzato e l’analisi strategica dei contenuti.
source-git-commit: 29e067086f9b6dd41c04b349c86ddc1c2baf8d2f
workflow-type: tm+mt
source-wordcount: '945'
ht-degree: 0%

---


# Best practice per la configurazione di categorie, argomenti, prompt e concorrenti

Questa sezione descrive le best practice per decidere come impostare categorie, argomenti, prompt e concorrenti.

Si tratta di un primo passo fondamentale. Le decisioni prese determinano il modo in cui le informazioni vengono adattate al contesto aziendale. Eventuali modifiche apportate alle categorie in futuro reimposteranno i dati storici.

Nel dashboard [[!UICONTROL Configurazione cliente]](/help/dashboards/customer-configuration.md) puoi definire in che modo il tuo marchio verrà monitorato e analizzato nella piattaforma di ottimizzazione LLM. Per informazioni su come utilizzare la dashboard, consulta [[!UICONTROL Configurazione del cliente]](/help/dashboards/customer-configuration.md).

![Finestra di configurazione del cliente](/help/assets/best-practices/customer-configuration-best-practices.png)

Nel dashboard [!UICONTROL Configurazione cliente], puoi personalizzare le categorie (ad esempio, business unit o linee di prodotti), tenere traccia dei concorrenti e aggiungere alias di menzione del brand per acquisire tutte le varianti del brand in tutte le richieste. Questa configurazione garantisce che la piattaforma personalizzi le informazioni sul contesto aziendale, consentendo un’analisi accurata del traffico, delle opportunità e della visibilità.

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

>[!IMPORTANT]
>
> * Scegli un approccio e attieniti ad esso.
> * Puoi avere solo **un** modello di categoria per account/marchio. Non combinare **SBU** e **URL_DIR** contemporaneamente.
>   <!--Can you mix Product/Service with these?-->

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

Durante la creazione dell’elenco, considera quanto segue:

* Un editor è in grado di comprendere l’argomento in 5 secondi dal testo del prompt? In caso contrario, rinominare/semplificare.
* Un team diverso sarà proprietario della correzione per argomenti diversi? Se sì, sono stati selezionati argomenti utili.
  <!-- Last bullet point does not make sense. Clarification needed.-->

Alcuni utili suggerimenti aggiuntivi:

* Utilizza la conoscenza della tua azienda o del tuo sito per definire argomenti in linea con gli obiettivi strategici del tuo marchio
* Considera il confronto tra il tuo marchio e quello della concorrenza all’interno di argomenti specifici.

>[!IMPORTANT]
>
> * Mantieni gli argomenti basati sulle finalità, non organizzativi.
> * Non aggiungere categorie/filtri per marchio/non marchio/area geografica, in quanto è possibile filtrare specificamente per questo nella scheda **[!UICONTROL Marchi]**.
> * Gli argomenti sono suddivisi in diverse categorie. È possibile **non** avere argomenti diversi per categoria.
> * Un singolo prompt può essere presente in diversi argomenti o categorie.

## Best practice per i prompt

I prompt identificano le domande o le query specifiche poste dai clienti, che possono avere un impatto sull&#39;azienda. Si tratta di domande o query effettive che gli utenti inseriscono nei moduli LLM.

Assicurati di rivedere e aggiornare regolarmente i prompt per garantire che siano in linea con le esigenze dei clienti e gli obiettivi aziendali.

>[!TIP]
>
>* Puoi utilizzare strumenti come Adobe LLM Optimizer e Google Search Console con filtri regex per identificare strutture di domande comuni (ad esempio, &quot;come&quot;, &quot;cosa&quot;, &quot;quando&quot;, &quot;dove&quot;) e scoprire quali prompt vengono utilizzati dalle persone per visitare il tuo sito.
>* Per scoprire quali prompt sono rilevanti per il sito o il brand, puoi utilizzare i dati di ricerca nel sito, le domande frequenti nelle pagine dei risultati dei motori di ricerca o anche chiedere direttamente ai chatbot LLM quali domande i clienti potrebbero porre sul brand.

## Best practice per i concorrenti

I concorrenti consentono di monitorare la visibilità e le menzioni nelle risposte LLM per i prompt e gli argomenti importanti per la propria attività.

La scheda [!UICONTROL **Tracciamento concorrenti**] consente di aggiungere concorrenti e di tenere traccia della loro visibilità per prompt e argomenti specifici.

Con il tracciamento dei concorrenti, puoi vedere con quale frequenza i concorrenti vengono menzionati insieme al tuo marchio in diverse regioni e categorie e confrontare la loro visibilità con la tua.

>[!TIP]
>
>Rivedi regolarmente le menzioni e le citazioni dei concorrenti per identificare le aree in cui il tuo marchio può migliorare.

## Ulteriori informazioni

* [Il dashboard Configurazione cliente](/help/dashboards/customer-configuration.md) è il luogo in cui puoi configurare categorie, argomenti, prompt e concorrenti.
* [Best practice per LLM Optimizer](/help/tutorials/best-practices.md) descrive le best practice per l&#39;ottimizzazione LLM

