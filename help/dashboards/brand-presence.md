---
title: Presenza del brand
description: Scopri come utilizzare la dashboard Presenza dei brand per comprendere come viene percepito il brand a livello di risposte generate dall’intelligenza artificiale.
feature: Brand Presence
source-git-commit: 24183fbe2577bb9402f8b6aaaf1e46c75403383d
workflow-type: tm+mt
source-wordcount: '1292'
ht-degree: 1%

---


# Presenza del brand {#brand-presence}

Il dashboard Presenza dei brand fornisce una panoramica dettagliata di come viene percepito il brand a livello di risposte generate dall’intelligenza artificiale. Mostra dove, con quale frequenza e in quale contesto viene menzionato il tuo marchio. Puoi utilizzare il dashboard per misurare la visibilità, tenere traccia delle citazioni ed esplorare le tendenze dei sentiment. Il dashboard è suddiviso in diverse sezioni, ciascuna delle quali fornisce informazioni diverse. Sono inoltre disponibili filtri personalizzabili per aiutarti a perfezionare i dati visualizzati.

![Presenza dei brand](/help/dashboards/assets/brand-main.png)

In questa pagina sono disponibili i dettagli riportati di seguito.

* [Filtri](#filters)
* [Metriche di panoramica](##key-metrics)
* [Confronto con altri](##others-comparison)
* [Tendenza sentiment](#sentiment-trend)
* [Insight di dati](#data-insights)

## Filtri {#filters}

Nella parte superiore della pagina, puoi applicare i filtri per perfezionare la visualizzazione. I filtri scelti influiranno su **tutte** le sezioni presenti nel dashboard. Puoi personalizzare quanto segue:

* **Intervallo date** - Selezionare l&#39;intervallo di tempo per i dati visualizzati. Ad esempio, le ultime 4 settimane. Puoi anche personalizzare il periodo di tempo selezionando l&#39;opzione **Settimane personalizzate**.
* **Categoria** - Filtra i risultati visualizzati in base a categorie predefinite o personalizzate.
* **Argomento** - Filtra per argomento per analizzare i temi del contenuto e le aree dell&#39;oggetto in cui il brand appare nelle risposte AI.
* **Piattaforma** - Scegli quale motore di intelligenza artificiale analizzare. LLM Optimizer attualmente supporta ChatGPT, le panoramiche di IA di Google, la modalità di intelligenza artificiale di Google, il Co-pilota di Microsoft, Google Gemini e Perplexity.
* **Prompts Origin** - Scegli l&#39;origine dei prompt. L’origine può essere inserita dall’utente o generata tramite IA.
* **Branding del prompt** - Filtra i risultati in base a prompt con marchio o senza marchio.
* **Area** - Filtra i risultati per area geografica. Al momento del lancio non tutte le aree geografiche saranno disponibili.

Dopo aver selezionato il filtro desiderato, fare clic su **Applica filtri** per applicare la selezione al dashboard.

## Metriche di panoramica {#overview-metrics}

La dashboard evidenzia tre metriche molto importanti nella parte superiore della pagina: punteggio di visibilità, menzioni e citazioni. Minore è il conteggio di queste metriche, peggiore sarà la percezione del tuo marchio, e dovresti agire per migliorare la tua presenza dei brand. Di seguito è riportata una breve descrizione di ciascuna metrica e di ciò che rappresenta.

![Metriche Panoramica](/help/dashboards/assets/overview-metrics.png)

### Punteggio visibilità {#visibility-score}

Il punteggio di visibilità è composto da fattori come: menzioni, citazioni, sentiment e rango. Ogni fattore ha un certo &quot;peso&quot; associato ad esso che si aggiunge al punteggio finale.

### Menzioni dei brand {#mentions}

Questa metrica rappresenta il numero totale di volte in cui il brand o le categorie sono stati menzionati nei prompt di IA campionati. Ad esempio, se hai il marchio &quot;Coffe B&quot;, con le categorie &quot;Macchine&quot; e &quot;Accessori&quot; questa metrica conta il numero totale di volte che questi compaiono nelle risposte AI campionate.

### Citazioni {#citations}

Questa metrica rappresenta il numero di volte in cui si è fatto riferimento al sito come origine.

Gli indicatori di tendenza per ciascuna metrica chiave mostrano le modifiche di questi valori nel tempo rispetto al periodo precedente.

## Confronto con altri {#others-comparison}

Nella sezione altri confronti puoi selezionare fino a cinque altri marchi e confrontarne menzioni e citazioni con il tuo marchio. In questo modo, puoi visualizzare e confrontare le tue prestazioni rispetto ad altri marchi.

![Confronto altri](/help/dashboards/assets/other-comparison.png)

Gli altri marchi vengono selezionati dall&#39;elenco a discesa e i grafici vengono aggiornati quando si fa clic su **Applica filtri**. I grafici mostrano affiancati menzioni dei brand settimanali e citazioni del marchio. Puoi anche passare il cursore del mouse lungo il grafico per vedere l’evoluzione dei dati nell’intervallo di tempo settimanale.

## Analisi della tendenza del sentiment {#sentiment-trend}

Nella sezione analisi delle tendenze del sentiment puoi tenere traccia di come il tuo brand viene percepito nelle risposte AI campionate. La metrica tendenza dei sentiment può essere positiva, neutra o negativa. Ad esempio, può essere positivo se le risposte evidenziano la qualità del prodotto o negativo se menzionano un servizio scadente. Il grafico di tendenza mostra i cambiamenti nella percezione del brand settimana dopo settimana. Questa sezione viene compilata solo dopo che il tuo marchio è menzionato.

![Tendenza dei sentiment](/help/dashboards/assets/sentiment-trend.png)

## Approfondimenti dati e Share of voice {#data-insights}

Per arrotondare il dashboard, abbiamo due tabelle importanti: approfondimenti sui dati e share of voice. Le informazioni presentate in queste tabelle ti aiuteranno a identificare la forza del tuo marchio e dove è necessaria l’ottimizzazione.

Utilizzando la tabella **approfondimenti dati** puoi esplorare argomenti e domande degli utenti per valutare e ottimizzare l&#39;impatto dei contenuti. I risultati sono dettagliati da argomenti e prompt. Nel frattempo, nella tabella **share of voice**, la voce del tuo marchio viene confrontata con quella di altri marchi per argomenti diversi, identificando le lacune e dando priorità ad argomenti futuri.

![Informazioni dati](/help/dashboards/assets/data-insights.png)

Entrambe le tabelle dispongono di un campo di ricerca per l&#39;accesso rapido agli argomenti ed è possibile personalizzare le metriche visualizzate facendo clic sul pulsante **Configura colonne**. Inoltre, puoi utilizzare l&#39;opzione **Esporta** per scaricare la tabella .csv e condividere le informazioni con il tuo team oppure includere le tabelle nei report manageriali.

Per informazioni dettagliate su ciascuna tabella e sulle metriche associate, fai clic sulle schede seguenti.

>[!BEGINTABS]

>[!TAB Informazioni dati]

La tabella Approfondimenti dati consente di esplorare argomenti e prompt degli utenti per valutare e ottimizzare l’impatto sui contenuti. Vengono visualizzate le metriche seguenti:

* **Argomento** - La categoria di argomenti rappresenta le parole chiave SEO e le domande utente relative al tuo marchio. È possibile fare clic su per espandere ogni argomento e visualizzare i singoli prompt analizzati per la presenza dei brand. Ogni argomento ha un pulsante **Dettagli** quando passi il puntatore del mouse su di esso. Facendo clic sul pulsante viene visualizzata una finestra separata con ulteriori dettagli.
* **Area** - visualizza l&#39;area dei prompt.
* **Popolarità** - La categoria di popolarità rappresenta il volume di ricerca per questo argomento relativo a tutti gli altri argomenti dell&#39;analisi. Il valore può essere Alto, Medium o Basso.
* **Punteggio di visibilità** - Il punteggio di visibilità dell&#39;argomento. Riflette fattori ponderati come menzioni, citazioni, sentiment e rango.
* **Menzioni** - Il numero di volte in cui il tuo marchio è stato menzionato nelle risposte AI per questo argomento o per questa combinazione di argomento/prompt.
* **Sentiment** - La percezione del brand nelle risposte AI in relazione a ciascun argomento calcolata come media in tutte le settimane. Viene popolato solo quando il tuo marchio viene effettivamente menzionato.
* **Posizione** - La rilevanza relativa del tuo marchio nelle risposte AI, calcolata come media in tutte le settimane.
* **Tutte le citazioni** - Numero di origini univoche citate nelle risposte AI per questo argomento o per questa combinazione argomento/prompt (citazioni di proprietà incluse).
* **Citazioni di proprietà** - Il numero di volte in cui il brand è stato citato nelle risposte AI per questa parola chiave o per questa combinazione di parola chiave/domanda.
  <!--* **Executions**-->

Puoi anche visualizzare ulteriori dettagli per ogni argomento facendo clic sull&#39;icona **Dettagli** alla fine di ogni riga.

>[!TAB Share of voice]

La tabella Share of voice fornisce uno sguardo comparativo sulle prestazioni del brand in argomenti chiave nelle risposte di IA generativa. Consente di identificare i divari di visibilità, monitorare le prestazioni della concorrenza e assegnare priorità alle aree per l&#39;ottimizzazione. Vengono visualizzate le metriche seguenti:

* **Argomento** - L&#39;argomento analizzato.
* **Popolarità**: il volume di ricerca dell&#39;argomento relativo a tutti gli altri argomenti dell&#39;analisi.
* **Menzioni** - Numero di volte in cui il tuo marchio è stato menzionato nelle risposte AI per l&#39;argomento o la combinazione argomento/prompt.
* **Classifica**: la classificazione dei Share of voice del tuo marchio, relativa a tutti gli altri marchi identificati.
* **Share of voice** - La percentuale del totale delle menzioni che il tuo brand contiene nelle risposte generate dall’intelligenza artificiale.
* **Altri 5 principali** - I cinque marchi più frequentemente menzionati per gli stessi argomenti. I marchi sono organizzati dai Share of voice (dal più alto al più basso).

>[!ENDTABS]

### Utilizzo della tabella Approfondimenti dati {#using-data-insights}

La tabella Approfondimenti dati consente di passare dalle metriche alle azioni suddividendo le prestazioni a livello di argomento e prompt.

Metodi principali per utilizzare la tabella:

* Dai priorità agli argomenti di elevata popolarità con visibilità ridotta: ottimizzazione dell’attenzione dove la domanda di pubblico è forte ma la presenza dei brand è debole.
* Tracciare i cambiamenti di sentiment: individua gli argomenti in cui le menzioni tendono a essere negative o neutre e coordina la risposta.
* Confronto tra citazioni e citazioni di proprietà: identifica i prompt in cui viene menzionato il tuo marchio ma vengono citati i contenuti di altri marchi, segnalando una lacuna nei contenuti.
* Valuta l’intervallo di posizioni: monitora se il brand compare nelle prime risposte AI (posizioni 1-3) o più in basso (6-10).
