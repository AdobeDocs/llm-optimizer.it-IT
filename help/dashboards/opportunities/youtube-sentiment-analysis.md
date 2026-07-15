---
title: Analisi del sentiment YouTube
description: Scopri come LLM Optimizer analizza i video e i commenti di YouTube per fornire consigli su come migliorare la percezione e la visibilità del tuo brand nei risultati di ricerca basati sull’IA.
feature: Opportunities
autotag-review: '2026-07-15T18:00:20.630Z'
TQID: 'https://experienceleague.adobe.com/qWlMzK13noSQULxakuUKHlDGZ-307yJjGJ4vsru2W6M'
product_v2:
  - id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2:
  - id: e1b649f0-0a61-46e4-9082-64d5cb2576c6
subfeature_v2:
  - id: fe92ae96-fc87-4fea-96a0-adc06310d4f4
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
  - id: fc314d1d-7cb9-4a38-8dbd-8f9b6478f40d
source-git-commit: 2705cf26faea9c09817bbdcec4b4c531552df7ba
workflow-type: tm+mt
source-wordcount: 1255
ht-degree: 100%

---


# Analisi del sentiment YouTube

YouTube è una delle piattaforme più influenti nel plasmare la percezione dei consumatori e la reputazione dei brand. Sempre più spesso, quando i sistemi di intelligenza artificiale rispondono a domande sul tuo brand, citano come fonti i video di YouTube. Il modo in cui si parla del tuo brand in questi contenuti ha quindi un impatto diretto sulle risposte generate dall’IA.

L’opportunità di analisi del sentiment di YouTube si presenta quando i video di YouTube vengono rilevati come citazioni per i prompt nel set di prompt della dashboard Presenza del brand. I video citati e i relativi commenti vengono analizzati in termini di sentiment, share of voice e argomenti ricorrenti. Successivamente, vengono visualizzati suggerimenti prioritari per migliorare la percezione e la rappresentazione del tuo brand nelle risposte generate dall’IA.

Il tuo brand viene analizzato in base a sei dimensioni:

- **Video analizzati**: numero di video di YouTube esaminati per menzioni del brand e sentiment.
- **Commenti analizzati**: numero di commenti esaminati nei video analizzati.
- **Menzioni del brand (video)**: con quale frequenza il tuo brand viene menzionato nei contenuti video.
- **Menzioni del brand (commenti)**: con quale frequenza il tuo brand viene menzionato nei commenti.
- **Sentiment generale (video)**: sentiment aggregato nei confronti del tuo brand su tutti i contenuti video.
- **Sentiment generale (commenti)**: sentiment aggregato nei confronti del tuo brand in base ai commenti.

>[!NOTE]
>L’analisi del sentiment di YouTube è attualmente nella versione beta. Le sue funzioni e la sua disponibilità potrebbero cambiare man mano che procede lo sviluppo di questa funzionalità.

![Dashboard di analisi del sentiment di YouTube](/help/dashboards/opportunities/assets/youtube-sentiment-overview.png)

## Come funziona

LLM Optimizer monitora i video di YouTube citati dai sistemi di intelligenza artificiale in base ai prompt presenti nel set di prompt della dashboard Presenza del brand. Quando vengono rilevati video citati, il sistema analizza tali video e i relativi commenti per individuare menzioni del brand, sentiment, share of voice e citazioni generate dall’IA. Questo strumento confronta le prestazioni del tuo brand con quelle della concorrenza di mercato e dei brand correlati, identifica gli argomenti ricorrenti che influenzano il sentiment e genera consigli per colmare le lacune nella percezione.

Se nel set di prompt non sono presenti video di YouTube, questa opportunità non verrà visualizzata nella dashboard.

I risultati vengono visualizzati in due schede:**Consigli** e **Prestazioni**.

## Suggerimenti

Questa scheda mostra i consigli per migliorare la percezione del tuo brand su YouTube. I consigli sono organizzati in tre sottoschede: **Consigli attuali**, **Consigli corretti** e **Consigli ignorati**.

![Scheda suggerimenti](/help/dashboards/opportunities/assets/youtube-sentiment-suggestions.png)

La tabella dei suggerimenti include le seguenti colonne:

- **Suggerimento**: il miglioramento consigliato per risolvere un divario di percezione.
- **Priorità**: livello di urgenza (critica, elevata, media, bassa).
- **Elementi azione**: apre un pannello con passaggi specifici per implementare il consiglio, inclusi i team responsabili (ad esempio, strategia dei contenuti, Influencer Marketing, Product Marketing).
- **Elementi di prova**: apre una tabella Origini che mostra i video alla base del suggerimento.

Quando si espande un suggerimento, viene visualizzata una sezione di **Analisi IA** con:

- **Perché è necessario apportare miglioramenti**: spiega il divario di percezione identificato, compreso il contesto competitivo e il modo in cui il problema si sta formando nei contenuti di YouTube.
- **Come migliorare**: indicazioni specifiche su quali contenuti o azioni colmerebbero il divario.
- **Risultato previsto**: risultato previsto se il consiglio viene implementato.

La tabella **Origini** mostra i video di YouTube che hanno generato il suggerimento, con le seguenti colonne:

- **Video**: titolo e link al video di YouTube.
- **Canale**: il canale YouTube che ha pubblicato il video.
- **Coinvolgimento**: livello di coinvolgimento (basso, medio, alto).
- **Menzioni del brand**: numero di menzioni del brand rispetto al totale delle menzioni nel video.
- **Share of voice**: quota di menzioni del tuo brand rispetto a tutti i brand menzionati.
- **Primi 5 brand**: i brand più menzionati nel video.
- **Sentiment**: sentiment generale verso il tuo brand nel video.
- **Citazioni IA**: numero di risposte IA che hanno citato questo video.

## Prestazioni

La scheda **Prestazioni** fornisce un raggruppamento dettagliato delle prestazioni del brand nei contenuti di YouTube. È organizzata in quattro sezioni.

### Panorama del mercato

Confronta le prestazioni del tuo brand rispetto ai brand associati e alla concorrenza di mercato in base alle menzioni.

![Panorama del mercato](/help/dashboards/opportunities/assets/youtube-sentiment-market-landscape.png)

Mostra:

- **Menzioni del brand nei video**: il tuo share of voice rispetto ai brand associati e alla concorrenza di mercato.
- **Menzioni del brand nei commenti**: lo stesso confronto tra i contenuti dei commenti.
- **Tracciamento del mercato**: un grafico filtrabile in cui è possibile selezionare fino a cinque brand della concorrenza per confrontare lo share of voice tra video e commenti.

### Analisi del sentiment

Tiene traccia della percezione del brand nei contenuti analizzati con un grafico **Distribuzione sentiment** che mostra la suddivisione percentuale del sentiment favorevole, neutro e sfavorevole sia per i video sia per i commenti.

![Analisi del sentiment](/help/dashboards/opportunities/assets/youtube-sentiment-distribution.png)

### Video

Una tabella dettagliata dei video di YouTube analizzati con le seguenti colonne:

- **Video**: titolo e link al video di YouTube.
- **Canale**: il canale YouTube che ha pubblicato il video.
- **Coinvolgimento**: livello di coinvolgimento (basso, medio, alto).
- **Menzioni del brand**: numero di menzioni del brand rispetto al totale delle menzioni nel video.
- **Share of voice**: quota di menzioni del tuo brand rispetto a tutti i brand menzionati.
- **Primi 5 brand**: i brand più menzionati nel video.
- **Sentiment**: sentiment generale verso il tuo brand nel video.
- **Citazioni IA**: numero di segnali di citazione IA associati al video.

La scheda Prestazioni mostra i pannelli **Video** e **Argomenti** in un’unica vista (con **Video** selezionati). La figura seguente include la tabella a livello di video e sotto di essa il riepilogo **Argomenti**.

![Tabelle Video e Argomenti nella scheda Prestazioni](/help/dashboards/opportunities/assets/youtube-sentiment-videos.png)

### Commenti

Una tabella dettagliata dei commenti di YouTube analizzati con le stesse colonne della tabella Video, filtrata in base ai dati a livello di commento.

### Argomenti

Una tabella di argomenti ricorrenti identificati nei contenuti analizzati, che mostra:

- **Argomento**: il tema ricorrente identificato.
- **Menzioni del brand**: numero di menzioni del brand associate all’argomento.
- **Sentiment**: sentiment complessivo associato all’argomento.

La tabella **Argomenti** viene visualizzata nella stessa vista Prestazioni della tabella Video. Consulta la figura nella sezione [Video](#videos) precedente.

## Prova nella demo

Scopri l’opportunità di analisi del sentiment di YouTube in azione utilizzando l’ambiente dimostrativo di Frescopa.

[Visualizzare l’analisi del sentiment di YouTube nella versione dimostrativa di Frescopa](https://play.llmo.now/org/demo-org/opportunities/youtube-analysis/971280f5-6a07-4506-85bf-d7419dca9803?siteId=frescopa-demo)

## Domande frequenti

**Perché YouTube è importante per la ricerca IA?**

I sistemi di intelligenza artificiale citano sempre più i video di YouTube durante la generazione di risposte su brand, prodotti e argomenti. Quando i video citati parlano del tuo brand in modo sfavorevole o impreciso, quel sentiment si nutre direttamente del modo in cui i sistemi di intelligenza artificiale rappresentano il tuo brand. Migliorare il modo in cui il brand viene discusso nei contenuti di YouTube che i sistemi di intelligenza artificiale già citano è uno dei modi più diretti per influenzare la percezione del brand generata dall’intelligenza artificiale.

**Perché questa opportunità non viene visualizzata nella dashboard?**

Questa opportunità viene visualizzata solo quando i video di YouTube vengono rilevati come citazioni per i prompt nel set di prompt della dashboard Presenza del brand. Se per tali prompt non viene citato alcun video di YouTube, l’opportunità non viene visualizzata. Man mano che il tuo brand acquisisce una maggiore copertura su YouTube e tali video vengono citati dai sistemi di intelligenza artificiale per il set di prompt, l’opportunità diventerà disponibile.

**Che cosa significa sentiment complessivo?**

Il sentiment complessivo riflette il tono aggregato dei contenuti in cui viene menzionato il brand: favorevole, neutro o sfavorevole. Viene calcolato separatamente per video e commenti, in quanto questi possono differire in modo significativo.

**Che cos&#39;è la share of voice?**

La share of voice è la percentuale di menzioni totali del tuo brand all’interno di un singolo contenuto o di tutti i contenuti analizzati, calcolata rispetto a tutti gli altri brand menzionati.

**Che cosa sono le citazioni IA?**

Le citazioni basate sull’intelligenza artificiale mostrano quante risposte dell’IA citano un determinato video. Un numero maggiore di citazioni IA indica che il video è utilizzato attivamente dai sistemi di intelligenza artificiale durante la generazione di risposte su argomenti correlati, rendendo il sentiment in tali video particolarmente importante per la rappresentazione IA del tuo brand.

**Come viene identificata la concorrenza di mercato?**

La concorrenza viene identificata automaticamente in base al settore in cui opera il tuo brand e ai brand più frequentemente citati nei contenuti analizzati. Puoi anche selezionare manualmente fino a cinque brand da confrontare nel grafico Tracciamento del mercato.

**Con quale frequenza viene aggiornata l’analisi?**

L’analisi di YouTube riflette il contenuto analizzato fino alla data mostrata nell’intestazione della dashboard. Rivedi l’opportunità dopo aver implementato i consigli per tenere traccia delle modifiche del sentiment e dello share of voice.
