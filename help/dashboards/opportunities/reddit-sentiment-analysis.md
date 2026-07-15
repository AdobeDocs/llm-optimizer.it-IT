---
title: Analisi del sentiment Reddit
description: Scopri come LLM Optimizer analizza i thread di Reddit per proporre consigli che migliorano la percezione e la visibilità del tuo brand nei risultati di ricerca IA.
feature: Opportunities
autotag-review: '2026-07-15T18:05:47.495Z'
TQID: 'https://experienceleague.adobe.com/trt7J6hxXtRdGat8Ohhd32JkwwIAJ26G8M98pBrN1CY'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: e1b649f0-0a61-46e4-9082-64d5cb2576c6
subfeature_v2: id: fe92ae96-fc87-4fea-96a0-adc06310d4f4
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: e1e0219c-f879-479f-8427-888ed2a6e9c2
source-git-commit: 2705cf26faea9c09817bbdcec4b4c531552df7ba
workflow-type: tm+mt
source-wordcount: 1163
ht-degree: 100%

---


# Analisi del sentiment Reddit

Reddit costituisce un’origine dati importante per i modelli linguistici di grandi dimensioni. Quando gli utenti chiedono agli assistenti IA informazioni sul tuo brand, le risposte sono influenzate dal sentiment dei contenuti di Reddit. Il modo in cui si parla del tuo brand nei subreddit influenza direttamente il modo in cui i sistemi di IA lo comprendono e lo presentano nelle risposte che generano.

L’opportunità Analisi del sentiment Reddit viene visualizzata quando vengono rilevati dei thread di Reddit come citazioni per il set di prompt della dashboard Presenza del brand. I thread citati e i relativi commenti vengono analizzati per individuare sentiment, share of voice e argomenti ricorrenti. L’opportunità propone quindi consigli prioritari per migliorare la percezione e la citazione del brand da parte dei sistemi di IA.

Il tuo brand viene analizzato in base a quattro dimensioni:

- **Post analizzati**: numero di post Reddit esaminati per individuare menzioni del brand e sentiment.
- **Commenti analizzati**: numero di commenti esaminati nei post analizzati.
- **Menzioni del brand (thread)**: con quale frequenza il brand è menzionato nei thread analizzati.
- **Sentiment complessivo (thread)**: sentiment aggregato verso il brand nei thread analizzati.

>[!NOTE]
>La funzione Aanalisi del sentiment Reddit è attualmente in versione Beta. Le sue funzioni e la sua disponibilità potrebbero cambiare man mano che procede lo sviluppo di questa funzionalità.

![Dashboard dell’analisi del sentiment Reddit](/help/dashboards/opportunities/assets/reddit-sentiment-overview.png)

## Come funziona

LLM Optimizer monitora i thread di Reddit citati dai sistemi di IA per individuare i prompt presenti nel set di prompt della dashboard della presenza del brand. Quando vengono rilevati i thread citati, li analizza insieme ai relativi commenti per individuare menzioni del brand, sentiment, share of voice e citazioni IA. Confronta le prestazioni del tuo brand con quelle dei concorrenti del mercato, identifica gli argomenti ricorrenti che promuovono il sentiment e genera consigli per risolvere i divari di percezione.

Se non vengono citati thread di Reddit per i prompt presenti nel set di prompt, questa opportunità non viene visualizzata nella dashboard.

I risultati vengono visualizzati in due schede:**Consigli** e **Prestazioni**.

## Suggerimenti

Questa scheda mostra i consigli per migliorare la percezione del tuo brand su Reddit. I consigli sono organizzati in tre sottoschede: **Consigli attuali**, **Consigli corretti** e **Consigli ignorati**.

![Scheda suggerimenti](/help/dashboards/opportunities/assets/reddit-sentiment-suggestions.png)

La tabella dei suggerimenti include le seguenti colonne:

- **Suggerimento**: il miglioramento consigliato per risolvere un divario di percezione.
- **Priorità**: livello di urgenza (critica, elevata, media, bassa).
- **Elementi di azione**: apre un pannello con passaggi specifici per implementare il consiglio, inclusi i team responsabili (ad esempio, PR, gestione community, marketing prodotto).
- **Prove documentali**: apre una tabella Origini che mostra i thread di Reddit su cui si basa il suggerimento.

Quando si espande un suggerimento, viene visualizzata una sezione di **Analisi IA** contenente quanto segue:

- **Perché sono necessari miglioramenti**: spiegazione del divario di percezione identificato, compresi il contesto competitivo e il modo in cui il problema sta assumendo forma nei thread di Reddit.
- **Come migliorare**: indicazioni specifiche su quali contenuti o azioni colmerebbero il divario.
- **Risultato previsto**: risultato previsto se il consiglio viene implementato.

La tabella **Origini** mostra i thread di Reddit su cui si basa il suggerimento, con le seguenti colonne:

- **Thread**: titolo e collegamento al thread di Reddit.
- **Subreddit**: il subreddit in cui è stato pubblicato il thread.
- **Coinvolgimento**: livello di coinvolgimento (basso, medio, elevato).
- **Menzioni del brand**: numero di menzioni del brand rispetto al totale delle menzioni nel thread.
- **Share of voice**: quota di menzioni del brand rispetto a tutti i brand menzionati.
- **Primi 5 brand**: i brand più menzionati nel thread.
- **Sentiment**: sentiment complessivo verso il brand nel thread.
- **Citazioni IA**: numero di risposte IA che hanno citato questo thread.

## Prestazioni

La scheda **Prestazioni** fornisce un raggruppamento dettagliato delle prestazioni del brand nei contenuti di Reddit. È organizzata in quattro sezioni.

### Panorama del mercato

Confronta le prestazioni del tuo brand con i brand associati e i concorrenti del mercato in base alle menzioni nei thread.

![Panorama del mercato](/help/dashboards/opportunities/assets/reddit-sentiment-landscape.png)

Mostra:

- **Le menzioni del brand nei thread**: il tuo share of voice rispetto ai brand associati e ai concorrenti del mercato.
- **Il tracciamento nel mercato**: un grafico filtrabile in cui è possibile selezionare fino a cinque brand concorrenti per confrontare lo share of voice nei vari thread.

### Analisi del sentiment

Monitora la percezione del brand nei thread analizzati mediante un grafico di **Distribuzione del sentiment** che riporta il raggruppamento percentuale del sentiment favorevole, neutro e sfavorevole nei vari thread.

![Analisi del sentiment](/help/dashboards/opportunities/assets/reddit-sentiment-distribution.png)

### Thread

Una tabella dettagliata dei thread di Reddit analizzati con le seguenti colonne:

- **Thread**: titolo e collegamento al thread di Reddit.
- **Subreddit**: il subreddit in cui è stato pubblicato il thread.
- **Coinvolgimento**: livello di coinvolgimento (basso, medio, elevato).
- **Menzioni del brand**: numero di menzioni del brand rispetto al totale delle menzioni nel thread.
- **Share of voice**: quota di menzioni del brand rispetto a tutti i brand menzionati.
- **Primi 5 brand**: i brand più menzionati nel thread.
- **Sentiment**: sentiment complessivo verso il brand nel thread.
- **Citazioni IA**: numero di risposte IA che hanno citato questo thread.

### Argomenti

Una tabella di argomenti ricorrenti identificati nei thread analizzati, che riporta:

- **Argomento**: il tema ricorrente identificato.
- **Menzioni del brand**: numero di menzioni del brand associate all’argomento.
- **Sentiment**: sentiment complessivo associato all’argomento.

Facendo clic su **Dettagli** in qualsiasi argomento si apre un pannello di approfondimenti composto di due schede:

- **Analisi**: riepilogo della discussione del tuo brand nei thread di Reddit associati a tale argomento.
- **Origini**: gli specifici thread di Reddit che contribuiscono al segnale di sentiment dell’argomento.

## Prova nella demo

Guarda in azione l’opportunità Analisi del sentiment di Reddit utilizzando l’ambiente demo di Frescopa.

[Visualizza l’analisi del sentiment di Reddit nella demo di Frescopa](https://play.llmo.now/org/demo-org/opportunities/reddit-analysis/b7e4d9a0-3c1f-4e2b-9d5a-8f2c1e0a7b4d?siteId=frescopa-demo)

## Domande frequenti

**Perché Reddit è importante per la ricerca IA?**

Reddit è una delle origini di dati di addestramento per LLM e di recupero in tempo reale con il maggior peso. Quando i sistemi di IA generano risposte su brand, prodotti e argomenti, le discussioni su Reddit spesso formano il tono, la struttura e le affermazioni fattuali di tali risposte. Un brand di cui si parla in modo sfavorevole o impreciso su Reddit avrà più probabilità di essere rappresentato in modo sfavorevole o impreciso anche nelle risposte generate dall’IA.

**Perché questa opportunità non viene visualizzata nella mia dashboard?**

L’opportunità viene visualizzata solo quando i thread di Reddit sono rilevati come citazioni per i prompt presenti nel set di prompt della dashboard della presenza del brand. Se non vengono citati thread di Reddit per tali prompt, l’opportunità non viene visualizzata. L’opportunità diventerà disponibile con l’aumentare della copertura del brand su Reddit e della citazione di tali thread da parte dei sistemi di IA per il set di prompt.

**Che cosa significa sentiment complessivo?**

Il sentiment complessivo riflette il tono aggregato dei thread in cui viene menzionato il brand: favorevole, neutro o sfavorevole, calcolato in tutti i thread analizzati.

**Che cosa è lo share of voice?**

Lo share of voice è la percentuale di menzioni totali del tuo brand in un determinato thread o in tutti i thread analizzati, rispetto a tutti gli altri brand menzionati.

**Cosa sono le citazioni IA?**

Le citazioni IA mostrano quante risposte IA hanno citato un determinato thread. Un numero più elevato di citazioni IA indica che il thread è utilizzato attivamente dai sistemi di IA durante la generazione di risposte su argomenti correlati, rendendo il sentiment in tali thread particolarmente importante per la rappresentazione IA del tuo brand.

**Come vengono identificati i concorrenti del mercato?**

I concorrenti vengono identificati automaticamente in base al settore del tuo brand e ai brand più frequentemente menzionati nei thread analizzati. Puoi anche selezionare manualmente fino a cinque brand da confrontare nel grafico Tracciamento del mercato.

**Con quale frequenza viene aggiornata l’analisi?**

L’analisi Reddit riflette il contenuto analizzato fino alla data visualizzata nell’intestazione della dashboard. Rivedi l’opportunità dopo aver implementato i consigli per tenere traccia delle modifiche del sentiment e dello share of voice.
