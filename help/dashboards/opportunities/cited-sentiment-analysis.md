---
title: Analisi del sentiment delle citazioni
description: Scopri come LLM Optimizer analizza gli URL più citati per proporre consigli su come migliorare la percezione e la visibilità del tuo brand nei risultati delle ricerche IA.
feature: Opportunities
autotag-review: '2026-07-15T17:45:11.828Z'
TQID: 'https://experienceleague.adobe.com/B-gDBklZ7XjMCQx-HaYx8H8yr9eZbXBvuRTAUfqJ-QU'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: e1b649f0-0a61-46e4-9082-64d5cb2576c6id: ab7fdb62-bd53-4cfd-8c2c-169f7e47f20e
subfeature_v2: id: cd42f7fa-7c4e-41cf-ba86-6e0de16ed456
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: e1e0219c-f879-479f-8427-888ed2a6e9c2
source-git-commit: 2705cf26faea9c09817bbdcec4b4c531552df7ba
workflow-type: tm+mt
source-wordcount: 1030
ht-degree: 100%

---


# Analisi del sentiment delle citazioni

Quando i sistemi di IA rispondono a domande sul tuo brand, si basano su un set di URL più citati: pagine web di terze parti a cui si fa spesso riferimento nelle risposte generate dall’IA. Il modo in cui il tuo brand è rappresentato su tali pagine determina direttamente il modo in cui i sistemi di IA lo presentano agli utenti.

L’opportunità di analisi del sentiment delle citazioni analizza gli URL più citati rilevati per i prompt presenti nel set di prompt della dashboard Presenza del brand. Valuta menzioni del brand, sentiment, share of voice e argomenti ricorrenti in tali pagine. Propone quindi consigli prioritari per migliorare la percezione del brand nell’IA per la gestione dei contenuti su cui i sistemi si basano maggiormente.

Mette in evidenza quattro metriche chiave:

- **Pagine analizzate**: numero di pagine web citate esaminate per individuare menzioni del brand e sentiment.
- **Pagine ignorate**: numero di pagine che non è stato possibile analizzare (ad esempio, a causa di restrizioni di accesso).
- **Menzioni del brand (pagine)**: con quale frequenza il brand è menzionato nelle pagine analizzate.
- **Sentiment complessivo (pagine)**: sentiment aggregato verso il brand nelle pagine analizzate.

>[!NOTE]
>L’analisi del sentiment delle citazioni è attualmente in versione Beta. Le sue funzioni e la sua disponibilità potrebbero cambiare man mano che procede lo sviluppo di questa funzionalità.

![Dashboard dell’analisi del sentiment delle citazioni](/help/dashboards/opportunities/assets/cited-sentiment-overview.png)

## Come funziona

LLM Optimizer identifica gli URL più citati che compaiono nelle risposte generate dall’IA per i prompt presenti nel set di prompt della dashboard della presenza del brand. Analizza le pagine per individuare menzioni del brand, sentiment, share of voice e citazioni AI. Confronta le prestazioni del tuo brand con quelle dei concorrenti del mercato, identifica gli argomenti ricorrenti e genera consigli per risolvere i divari di percezione sulle pagine che hanno più importanza per i sistemi di IA.

Se non vengono rilevati URL citati per i prompt presenti nel set di prompt, questa opportunità non viene visualizzata nella dashboard.

I risultati vengono visualizzati in due schede:**Consigli** e **Prestazioni**.

## Suggerimenti

Questa scheda mostra i consigli per migliorare la percezione del tuo brand negli URL più citati. I suggerimenti sono organizzati in tre sottoschede: **Suggerimenti correnti**, **Suggerimenti corretti** e **Suggerimenti ignorati**.

![Scheda suggerimenti](/help/dashboards/opportunities/assets/cited-sentiment-suggestions.png)

La tabella dei suggerimenti include le seguenti colonne:

- **Suggerimento**: il miglioramento consigliato per risolvere un divario di percezione.
- **Priorità**: livello di urgenza (critica, elevata, media, bassa).
- **Elementi di azione**: apre un pannello con passaggi specifici per implementare il consiglio, inclusi i team responsabili.

Quando si espande un suggerimento, viene visualizzata una sezione di **Analisi IA** contenente quanto segue:

- **Perché sono necessari miglioramenti**: spiegazione del divario di percezione identificato, inclusi gli URL citati che non rappresentano adeguatamente il brand e il contesto competitivo.
- **Come migliorare**: indicazioni specifiche su azioni di divulgazione, creazione di contenuti o collaborative per risolvere il divario.
- **Risultato atteso**: il risultato previsto dell’implementazione del consiglio.

## Prestazioni

La scheda **Prestazioni** fornisce un raggruppamento dettagliato delle prestazioni del brand nelle pagine più citate. È organizzata in quattro sezioni.

### Panorama del mercato

Confronta le prestazioni del tuo brand con i brand associati e i concorrenti del mercato in base alle menzioni nelle pagine citate.

![Panorama del mercato](/help/dashboards/opportunities/assets/cited-sentiment-landscape.png)

Mostra:

- **Le menzioni del brand nelle pagine**: il tuo share of voice rispetto ai brand associati e ai concorrenti del mercato.
- **Il tracciamento nel mercato**: un grafico filtrabile in cui è possibile selezionare fino a cinque brand concorrenti per confrontare lo share of voice nelle pagine analizzate.

### Analisi del sentiment

Monitora la percezione del brand nelle pagine analizzate mediante un grafico di **Distribuzione del sentiment** che riporta il raggruppamento percentuale del sentiment favorevole, neutro e sfavorevole nelle varie pagine.

![Analisi del sentiment](/help/dashboards/opportunities/assets/cited-sentiment-distribution.png)

### Pagine

Una tabella dettagliata delle pagine web citate analizzate con le seguenti colonne:

- **Pagina**: URL della pagina analizzata.
- **Menzioni del brand**: numero di menzioni del brand rispetto al totale delle menzioni nella pagina.
- **Share of voice**: quota di menzioni del brand rispetto a tutti i brand menzionati.
- **Primi 5 brand**: i brand più menzionati nella pagina.
- **Sentiment**: sentiment complessivo verso il brand nella pagina.
- **Citazioni IA**: numero di risposte IA che hanno citato questa pagina.

### Argomenti

Una tabella di argomenti ricorrenti identificati nelle pagine analizzate, che riporta:

- **Argomento**: il tema ricorrente identificato.
- **Menzioni del brand**: numero di menzioni del brand associate all’argomento.
- **Sentiment**: sentiment complessivo associato all’argomento.

Facendo clic su **Dettagli** in qualsiasi argomento si apre un riepilogo dell’analisi e le pagine di origine che forniscono un contributo.

## Prova nella demo

Guarda in azione l’opportunità Analisi del sentiment delle citazioni utilizzando l’ambiente demo di Frescopa: [Visualizza l’analisi del sentiment delle citazioni nella demo di Frescopa](https://play.llmo.now/org/demo-org/opportunities/cited-analysis/d3a8b217-9f4c-4e88-a612-6b7f91e5c044?siteId=frescopa-demo).

## Domande frequenti

**Perché gli URL più citati sono importanti per la ricerca IA?**

Gli URL più citati sono le pagine di terze parti a cui i sistemi di IA fanno riferimento più frequentemente quando generano risposte relative al tuo brand. Il sentiment e la struttura di queste pagine hanno un’influenza diretta e sproporzionata sul modo in cui l’IA presenta il tuo brand, molto più di quella delle pagine che vengono citate raramente. Migliorare la rappresentazione del brand su tali pagine specifiche è una delle azioni più efficaci a tua disposizione per aumentare la visibilità per l’IA.

**Perché questa opportunità non viene visualizzata nella mia dashboard?**

L’opportunità viene visualizzata solo quando gli URL citati sono rilevati per i prompt presenti nel set di prompt della dashboard della presenza del brand. Se non sono stati identificati URL citati per tali prompt, l’opportunità non viene visualizzata.

**Che cosa significa pagine ignorate?**

Le pagine ignorate sono URL citati che non è stato possibile analizzare, di solito perché la pagina è a pagamento, richiede l’autenticazione o blocca l’accesso automatizzato. Queste pagine vengono conteggiate ma sono escluse dall’analisi del sentiment e delle menzioni del brand.

**Che cosa è lo share of voice?**

Lo share of voice è la percentuale di menzioni totali del tuo brand in una determinata pagina o in tutte le pagine analizzate, rispetto a tutti gli altri brand menzionati.

**Cosa sono le citazioni IA?**

Le citazioni IA mostrano quante risposte IA hanno citato una determinata pagina. Un numero più elevato di citazioni IA indica che la pagina è utilizzata attivamente dai sistemi di IA durante la generazione di risposte su argomenti correlati, rendendo il sentiment in tali pagine particolarmente importante per la rappresentazione IA del tuo brand.

**Come vengono identificati i concorrenti del mercato?**

I concorrenti vengono identificati automaticamente in base al settore del tuo brand e ai brand più frequentemente menzionati nelle pagine analizzate. Puoi anche selezionare manualmente fino a cinque brand da confrontare nel grafico Tracciamento del mercato.

**Con quale frequenza viene aggiornata l’analisi?**

L’analisi riflette gli URL citati rilevati fino alla data visualizzata nell’intestazione della dashboard. Rivedi l’opportunità dopo aver implementato i consigli per tenere traccia delle modifiche del sentiment e dello share of voice.
