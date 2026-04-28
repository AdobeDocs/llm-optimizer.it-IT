---
title: Analisi Sentiment Reddit
description: Scopri come LLM Optimizer analizza i thread di Reddit per evidenziare i consigli che migliorano la percezione e la visibilità del tuo marchio nei risultati delle Ricerche IA.
feature: Opportunities
source-git-commit: fa8b994aa55869cf7f2607e792acc4e8abc213e7
workflow-type: tm+mt
source-wordcount: '1163'
ht-degree: 0%

---


# Analisi Sentiment Reddit

Reddit è un&#39;origine dati critica per i modelli di linguaggio di grandi dimensioni. Quando gli utenti chiedono agli assistenti AI informazioni sul brand, le risposte sono influenzate dal sentiment dei contenuti di Reddit. Il modo in cui il brand viene discusso tra i subreddit forma direttamente il modo in cui i sistemi di intelligenza artificiale lo comprendono e lo rappresentano nelle risposte generate.

L&#39;opportunità di analisi del Sentiment Reddit viene visualizzata quando i thread Reddit vengono rilevati come citazioni per i prompt nel set di prompt del dashboard di Presenza dei brand. Analizza i thread citati e i relativi commenti per sentiment, share of voice e argomenti ricorrenti. L’opportunità presenta quindi consigli con priorità per migliorare la percezione e la citazione del brand da parte dei sistemi di intelligenza artificiale.

Analizza il tuo marchio in quattro dimensioni:

- **Post analizzati** — Numero di post Reddit esaminati per menzioni dei brand e sentiment.
- **Commenti analizzati** — Numero di commenti esaminati nei post analizzati.
- **Menzioni dei brand (thread)**: con quale frequenza il brand viene menzionato nei thread analizzati.
- **sentiment complessivo (thread)**: sentiment aggregato per il brand tra i thread analizzati.

>[!NOTE]
>L’analisi del Sentiment Reddit è attualmente in versione beta. Le funzionalità e la disponibilità potrebbero cambiare man mano che la funzionalità continua a svilupparsi.

![Modifica dashboard analisi Sentiment](/help/dashboards/opportunities/assets/reddit-sentiment-overview.png)

## Come funziona

LLM Optimizer monitora i thread Reddit citati dai sistemi AI per i prompt nel set di prompt del dashboard di Presenza dei brand. Quando vengono rilevati i thread citati, analizza tali thread e i relativi commenti per menzioni dei brand, sentiment, share of voice e citazioni AI. Confronta le prestazioni del tuo marchio con quelle dei concorrenti del mercato, identifica gli argomenti ricorrenti che determinano il sentiment e genera consigli per affrontare i divari di percezione.

Se non vengono citati thread Reddit per i prompt nel set di prompt, questa opportunità non verrà visualizzata nel dashboard.

I risultati vengono visualizzati in due schede: **Suggerimenti** e **Prestazioni**.

## Suggerimenti

Questa scheda mostra i consigli per migliorare la percezione del brand su Reddit. I suggerimenti sono organizzati in tre schede secondarie: **Suggerimenti correnti**, **Suggerimenti corretti** e **Suggerimenti ignorati**.

![Scheda Suggerimenti](/help/dashboards/opportunities/assets/reddit-sentiment-suggestions.png)

La tabella dei suggerimenti include le colonne riportate di seguito.

- **Suggerimento**: il miglioramento consigliato per colmare il divario di percezione.
- **Priorità** — Livello di urgenza (critico, elevato, Medium, basso).
- **Elementi azione**: apre un pannello con passaggi specifici per implementare il consiglio, inclusi i team responsabili (ad esempio, PR, Gestione community, Marketing prodotto).
- **Evidence** - Apre una tabella Sources che mostra i thread Reddit dietro il suggerimento.

Quando si espande un suggerimento, viene visualizzata una sezione di **Analisi IA** con:

- **Perché è necessario apportare miglioramenti** — Spiega il divario di percezione identificato, compreso il contesto competitivo e il modo in cui il problema si sta formando tra i thread Reddit.
- **Come migliorare** — Indicazioni specifiche su quali contenuti o azioni colmerebbero il gap.
- **Risultato previsto**: risultato previsto dell&#39;implementazione del consiglio.

La tabella **Sources** mostra i thread Reddit che guidano il suggerimento, con le colonne seguenti:

- **Thread** — Titolo e collegamento al thread Reddit.
- **Subreddit**: subreddit in cui è stato pubblicato il thread.
- **Coinvolgimento** — Livello di coinvolgimento (basso, Medium, alto).
- **Menzioni dei brand**: numero di menzioni dei brand rispetto al totale delle menzioni nel thread.
- **Share of voice** - Quota di menzioni del tuo marchio relativa a tutti i marchi menzionati.
- **Primi 5 marchi**: i marchi più citati nel thread.
- **Sentiment**: sentiment complessivo verso il tuo marchio nel thread.
- **Citazioni IA** — Numero di risposte IA che hanno citato questo thread.

## Prestazioni

La scheda **Prestazioni** fornisce un raggruppamento dettagliato delle prestazioni del brand nei contenuti Reddit. È organizzato in quattro sezioni.

### Panorama del mercato

Confronta le prestazioni del tuo marchio con i marchi associati e con i concorrenti del mercato in base alle menzioni nei thread.

![Orizzontale di mercato](/help/dashboards/opportunities/assets/reddit-sentiment-landscape.png)

Mostra:

- **Menzioni dei brand nei thread**: il tuo share of voice rispetto ai marchi associati e ai concorrenti sul mercato.
- **Tracciamento del mercato**: un grafico filtrabile in cui è possibile selezionare fino a cinque marchi concorrenti per confrontare share of voice tra thread diversi.

### Analisi del sentiment

Tiene traccia della percezione del brand tra i thread analizzati con un grafico di **Distribuzione Sentiment** che mostra la suddivisione percentuale del sentiment favorevole, neutro e sfavorevole tra i thread.

![Analisi Sentiment](/help/dashboards/opportunities/assets/reddit-sentiment-distribution.png)

### Thread

Una tabella dettagliata dei thread Reddit analizzati con le seguenti colonne:

- **Thread** — Titolo e collegamento al thread Reddit.
- **Subreddit**: subreddit in cui è stato pubblicato il thread.
- **Coinvolgimento** — Livello di coinvolgimento (basso, Medium, alto).
- **Menzioni dei brand**: numero di menzioni dei brand rispetto al totale delle menzioni nel thread.
- **Share of voice** - Quota di menzioni del tuo marchio relativa a tutti i marchi menzionati.
- **Primi 5 marchi**: i marchi più citati nel thread.
- **Sentiment**: sentiment complessivo verso il tuo marchio nel thread.
- **Citazioni IA** — Numero di risposte IA che hanno citato questo thread.

### Argomenti

Una tabella di argomenti ricorrenti identificati tra i thread analizzati, che mostra:

- **Argomento** - Il tema o l&#39;oggetto ricorrente identificato.
- **Menzioni dei brand** — Numero di menzioni dei brand associate all&#39;argomento.
- **Sentiment** - sentiment complessivo associato all&#39;argomento.

Facendo clic su **Dettagli** su qualsiasi argomento viene aperto un pannello di espansione con due schede:

- **Analisi**: riepilogo delle discussioni del brand tra i thread associati all&#39;argomento.
- **Origini**: thread Reddit specifici che contribuiscono al segnale di sentiment dell&#39;argomento.

## Prova la demo

Osserva l’opportunità di analisi del Sentiment Reddit in azione utilizzando l’ambiente demo Frescopa.

[Visualizzare l’analisi del Sentiment Reddit nella demo di Frescopa](https://play.llmo.now/org/demo-org/opportunities/reddit-analysis/b7e4d9a0-3c1f-4e2b-9d5a-8f2c1e0a7b4d?siteId=frescopa-demo)

## Domande frequenti

**Perché Reddit è importante per le Ricerche IA?**

Reddit è una delle fonti più pesantemente ponderate nei dati di apprendimento LLM e nel recupero in tempo reale. Quando i sistemi di intelligenza artificiale generano risposte su marchi, prodotti e argomenti, le discussioni su Reddit spesso informano il tono, l’inquadratura e le affermazioni fattuali in tali risposte. Un marchio che viene discusso in modo sfavorevole o impreciso su Reddit è più probabile che venga rappresentato in questo modo nelle risposte generate dall’intelligenza artificiale.

**Perché questa opportunità non viene visualizzata nel dashboard?**

Questa opportunità viene visualizzata solo quando i thread di Reddit vengono rilevati come citazioni per i prompt nel set di prompt del dashboard di Presenza dei brand. Se per tali prompt non vengono citati thread Reddit, l’opportunità non viene visualizzata. Man mano che il tuo marchio acquisisce una maggiore copertura Reddit e tali thread vengono citati dai sistemi di intelligenza artificiale per il set di prompt, l’opportunità diventerà disponibile.

**Che cosa significa Sentiment complessivo?**

Il sentiment complessivo riflette il tono aggregato dei thread in cui viene menzionato il brand: calcolato in modo favorevole, neutro o sfavorevole su tutti i thread analizzati.

**Cos&#39;è Share of voice?**

Share of voice è la percentuale del totale di menzioni dei brand del tuo marchio in un determinato thread o in tutti i thread analizzati, rispetto a tutti gli altri brand menzionati.

**Cosa sono le citazioni AI?**

Le citazioni di IA mostrano quante risposte di IA hanno citato un determinato thread. Un numero più elevato di citazioni IA indica che il thread è utilizzato attivamente dai sistemi di IA durante la generazione di risposte su argomenti correlati, rendendo il sentiment in tali thread particolarmente importante per la rappresentazione di IA del brand.

**Come vengono identificati i concorrenti del mercato?**

I concorrenti vengono identificati automaticamente in base al settore del tuo marchio e ai marchi più frequentemente citati nei thread analizzati. Puoi anche selezionare manualmente fino a cinque marchi da confrontare nel grafico Tracciamento del mercato.

**Con quale frequenza viene aggiornata l&#39;analisi?**

L’analisi Reddit riflette il contenuto analizzato fino alla data mostrata nell’intestazione della dashboard. Rivedi l’opportunità dopo aver implementato le raccomandazioni per tenere traccia delle modifiche in sentiment e share of voice.
