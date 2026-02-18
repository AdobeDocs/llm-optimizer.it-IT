---
title: Presenza del brand
description: Scopri come utilizzare la dashboard Presenza del brand per comprendere come viene percepito il tuo brand a livello di risposte generate dall’IA.
feature: Brand Presence
source-git-commit: 24183fbe2577bb9402f8b6aaaf1e46c75403383d
workflow-type: ht
source-wordcount: '1299'
ht-degree: 100%

---


# Presenza del brand {#brand-presence}

La dashboard Presenza del brand fornisce una panoramica dettagliata di come viene percepito il tuo brand a livello di risposte generate dall’IA.Mostra dove, con quale frequenza e in quale contesto viene menzionato il tuo brand.Puoi utilizzare la dashboard per misurare la visibilità, tenere traccia delle citazioni ed esplorare le tendenze del sentiment.La dashboard è suddivisa in diverse sezioni, ciascuna delle quali fornisce insight diversi.Sono inoltre disponibili filtri personalizzabili per aiutarti a perfezionare i dati visualizzati.

![Presenza del brand](/help/dashboards/assets/brand-main.png)

Questa pagina descrive quanto segue:

* [Filtri](#filters)
* [Metriche di panoramica](##key-metrics)
* [Confronto con altri brand](##others-comparison)
* [Tendenza sentiment](#sentiment-trend)
* [Insight di dati](#data-insights)

## Filtri {#filters}

Nella parte superiore della pagina, puoi applicare i filtri per definire la vista. I filtri scelti influiranno su **tutte** le sezioni presenti nella dashboard. Puoi personalizzare quanto segue:

* **Intervallo di date**: seleziona l’arco temporale per i dati da visualizzare. Ad esempio, le ultime 4 settimane. Puoi anche personalizzare il periodo di tempo selezionando l’opzione **Settimane personalizzate**.
* **Categoria**: filtra i risultati visualizzati in base a categorie predefinite o personalizzate.
* **Argomento**: filtra per argomento per analizzare i temi dei contenuti e le aree tematiche in cui il tuo brand appare nelle risposte IA.
* **Piattaforma**: scegli quale motore di IA analizzare.Attualmente LLM Optimizer supporta ChatGPT, panoramiche IA di Google, modalità IA di Google, Microsoft Co-pilot, Google Gemini e Perplexity.
* **Origine prompt**: scegli l’origine dei prompt.L’origine può essere inserita dall’utente o generata dall’IA.
* **Branding del prompt**: filtra i risultati in base a prompt con brand o senza brand.
* **Area geografica**: filtra i risultati per area geografica.Al momento del lancio non tutte le aree geografiche saranno disponibili.

Dopo aver selezionato il filtro, fai clic su **Applica filtri** per applicare la selezione alla dashboard.

## Metriche di panoramica {#overview-metrics}

La dashboard evidenzia tre metriche molto importanti nella parte superiore della pagina: punteggio di visibilità, menzioni e citazioni.Minore è il valore di queste metriche, peggiore sarà la percezione del tuo brand; dovresti quindi agire per migliorarne la presenza.Di seguito è riportata una breve descrizione di ciascuna metrica e di ciò che rappresenta.

![Metriche di panoramica](/help/dashboards/assets/overview-metrics.png)

### Punteggio visibilità {#visibility-score}

Il punteggio di visibilità è composto da fattori come: menzioni, citazioni, sentiment e ranking.Ciascun fattore ha un certo “peso” associato ad esso che si aggiunge al punteggio finale.

### Menzioni del brand {#mentions}

Questa metrica rappresenta il numero totale di volte in cui il brand o le categorie sono stati menzionati nei prompt IA campionati.Ad esempio, se il tuo brand è “Coffe B”, con le categorie “Macchine” e “Accessori”, questa metrica conta il numero totale di volte in cui questi elementi compaiono nelle risposte IA campionate.

### Citazioni {#citations}

Questa metrica rappresenta il numero di volte in cui il tuo sito è stato menzionato come origine.

Gli indicatori di tendenza per ciascuna metrica chiave mostrano come questi valori cambiano nel tempo rispetto al periodo precedente.

## Confronto con altri brand {#others-comparison}

Nella sezione Confronto con altri brand puoi selezionarne fino a cinque altri e confrontarne menzioni e citazioni con il tuo brand. In questo modo, puoi visualizzare e confrontare le tue prestazioni rispetto ad altri brand.

![Confronto con altri brand](/help/dashboards/assets/other-comparison.png)

Quando fai clic su **Applica filtri**, gli altri brand sono selezionati dall’elenco a discesa e i grafici vengono aggiornati.I grafici mostrano le menzioni e le citazioni del brand su base settimanale affiancate.Puoi anche passare il puntatore del mouse lungo il grafico per visualizzare l’evoluzione dei dati nell’arco temporale settimanale.

## Analisi della tendenza del sentiment {#sentiment-trend}

Nella sezione Analisi della tendenza del sentiment puoi tenere traccia di come il tuo brand viene percepito nelle risposte IA campionate.La metrica tendenza del sentiment può essere positiva, neutra o negativa.Ad esempio, può essere positiva se le risposte evidenziano la qualità del prodotto o negativa se menzionano un servizio scadente.Il grafico tendenze mostra i cambiamenti nella percezione del brand su base settimanale.Questa sezione viene compilata solo dopo che il tuo brand è stato menzionato.

![Tendenza del sentiment](/help/dashboards/assets/sentiment-trend.png)

## Insight di dati e quota di voce {#data-insights}

A completamento della dashboard, sono disponibili due tabelle importanti: insight di dati e quota di voce. Le informazioni presentate in queste tabelle ti aiuteranno a identificare i punti di forza del tuo brand e le aree in cui è necessaria un’ottimizzazione.

Utilizzando la tabella **Insight di dati** puoi esplorare argomenti e domande degli utenti per valutare e ottimizzare l’impatto dei contenuti.I risultati sono dettagliati per argomenti e prompt.Allo stesso tempo, nella tabella **Quota di voce**, la voce del tuo brand viene confrontata con quella di altri brand per argomenti diversi, identificando le lacune e dando priorità ad argomenti futuri.

![Insight di dati](/help/dashboards/assets/data-insights.png)

Entrambe le tabelle hanno un campo di ricerca per l’accesso rapido agli argomenti e puoi personalizzare le metriche visualizzate facendo clic sul pulsante **Configura colonne**.Inoltre, puoi utilizzare l’opzione **Esporta** per scaricare il file .csv della tabella e condividerne gli insight con il tuo team oppure includere le tabelle nel reporting per il management.

Per informazioni dettagliate su ciascuna tabella e sulle metriche associate, fai clic sulle schede seguenti.

>[!BEGINTABS]

>[!TAB Insight di dati]

La tabella Insight di dati ti consente di esplorare argomenti e prompt degli utenti per valutare e ottimizzare l’impatto dei contenuti.La tabella mostra le metriche seguenti:

* **Argomento**: la categoria di argomenti rappresenta le parole chiave SEO e le domande degli utenti relative al tuo brand.Puoi fare clic per espandere ciascun argomento e visualizzare i singoli prompt analizzati per la presenza del brand.Ciascun argomento presenta un pulsante **Dettagli** quando passi il puntatore del mouse su di esso.Facendo clic sul pulsante viene visualizzata una finestra separata con ulteriori dettagli.
* **Area geografica**: mostra l’area geografica dei prompt.
* **Popolarità**: la categoria popolarità rappresenta il volume di ricerche per questo argomento rispetto a tutti gli altri argomenti dell’analisi.Il valore può essere alto, medio o basso.
* **Punteggio di visibilità**: il punteggio di visibilità dell’argomento.Riflette fattori ponderati come menzioni, citazioni, sentiment e ranking.
* **Menzioni**: il numero di volte in cui il tuo brand è stato menzionato nelle risposte IA per questo argomento o questa combinazione argomento/prompt.
* **Sentiment**: la percezione del brand nelle risposte IA in relazione a ciascun argomento calcolata come media su tutte le settimane.Viene compilato solo quando il tuo brand viene effettivamente menzionato.
* **Posizione**: la rilevanza relativa del tuo brand nelle risposte IA, calcolata come media su tutte le settimane.
* **Tutte le citazioni**: il numero di origini univoche citate nelle risposte IA per questo argomento o per questa combinazione argomento/prompt, incluse le citazioni di proprietà.
* **Citazioni di proprietà**: il numero di volte in cui il tuo brand è stato citato nelle risposte IA per questa parola chiave o questa combinazione parola chiave/domanda.
  <!--* **Executions**-->

Puoi anche visualizzare ulteriori dettagli per ciascun argomento facendo clic sull’icona **Dettagli** alla fine di ogni riga.

>[!TAB Quota di voce]

La tabella Quota di voce offre una panoramica comparativa sulle prestazioni del brand tra gli argomenti chiave nelle risposte dell’IA generativa.Ti consente di identificare le lacune della visibilità, tenere traccia delle prestazioni della concorrenza e assegnare priorità alle aree per l’ottimizzazione.La tabella mostra le metriche seguenti:

* **Argomento**: l’argomento analizzato.
* **Popolarità**: il volume della ricerca per questo argomento rispetto a tutti gli altri argomenti nell’analisi.
* **Menzioni**: il numero di volte in cui il tuo brand è stato menzionato nelle risposte IA per questo argomento o questa combinazione argomento/prompt.
* **Ranking**: il ranking della quota di voce del tuo brand rispetto a tutti gli altri brand identificati.
* **Quota di voce**: la percentuale di menzioni totali del tuo brand nelle risposte generate dall’IA.
* **5 altri brand principali**: i cinque brand menzionati con maggiore frequenza per gli stessi argomenti. I brand sono organizzati in base al loro share of voice, dal più alto al più basso.

>[!ENDTABS]

### Utilizzo della tabella Insight di dati {#using-data-insights}

La tabella Insight di dati consente di passare dalle metriche alle azioni suddividendo le prestazioni a livello di argomento e prompt.

Metodi principali per utilizzare questa tabella:

* Dai priorità agli argomenti più popolari con bassa visibilità: concentra l’ottimizzazione sui contenuti con un’elevata domanda da parte del pubblico ma in cui la presenza del brand risulta debole.
* Tieni traccia dei cambiamenti di sentiment: individua gli argomenti in cui le menzioni tendono a essere negative o neutre, e coordina la tua strategia di risposta.
* Confronta le citazioni rispetto alle citazioni di proprietà: individua i prompt in cui viene menzionato il tuo brand ma vengono citati i contenuti di altri brand, in quanto questo suggerisce possibili lacune nei contenuti.
* Valuta il livello di posizionamento: monitora se il brand compare nelle prime risposte fornite dall’IA, (posizioni da 1 a 3), o più in basso (da 6 a 10).
