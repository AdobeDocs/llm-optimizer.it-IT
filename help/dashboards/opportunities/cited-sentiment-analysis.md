---
title: Analisi Sentiment citati
description: Scopri come LLM Optimizer analizza gli URL più citati per evidenziare i consigli che migliorano la percezione e la visibilità del tuo marchio nei risultati delle Ricerche IA.
feature: Opportunities
autotag-review: '2026-05-15T17:39:50.086Z'
TQID: 'https://experienceleague.adobe.com/ZqgWup29QoQ-j0fDM6DqhGpzRqscg1f-fdXHTMN9fIk'
product_v2:
  - id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2:
  - id: a0b5a505-2fd7-4c3d-b61c-b557fb6f0558
  - id: c0713b97-4af8-4c41-b742-5afcc6ced468
subfeature_v2:
  - id: e1b649f0-0a61-46e4-9082-64d5cb2576c6
source-git-commit: 7a92587197cf6a9eec6b01bd4eaeeaf1194d3088
workflow-type: tm+mt
source-wordcount: 1030
ht-degree: 1%

---


# Analisi Sentiment citati

Quando i sistemi di intelligenza artificiale rispondono a domande sul tuo marchio, si basano su un set di URL citati in alto: pagine web di terze parti a cui si fa spesso riferimento nelle risposte generate dall’intelligenza artificiale. Il modo in cui il brand viene rappresentato su tali pagine determina direttamente il modo in cui i sistemi di intelligenza artificiale lo rappresentano per gli utenti.

L’opportunità Analisi Sentiment citata analizza gli URL più citati rilevati per i prompt nel set di prompt del dashboard di Presenza dei brand. Valuta menzioni dei brand, sentiment, share of voice e argomenti ricorrenti in tali pagine. Successivamente, vengono visualizzati consigli con priorità per migliorare la percezione del brand sui contenuti su cui i sistemi di IA si basano di più.

Presenta quattro metriche chiave:

- **Pagine analizzate** — Numero di pagine Web citate esaminate per menzioni dei brand e sentiment.
- **Pagine ignorate** — Numero di pagine che non è stato possibile analizzare (ad esempio, a causa di restrizioni di accesso).
- **Menzioni dei brand (pagine)** — frequenza con cui il brand viene menzionato nelle pagine analizzate.
- **sentiment complessivo (pagine)** — sentiment aggregato per il brand tra le pagine analizzate.

>[!NOTE]
>L’analisi dei Sentiment citati è attualmente in versione beta. Le funzionalità e la disponibilità potrebbero cambiare man mano che la funzionalità continua a svilupparsi.

![Dashboard analisi Sentiment citata](/help/dashboards/opportunities/assets/cited-sentiment-overview.png)

## Come funziona

LLM Optimizer identifica gli URL più citati che compaiono nelle risposte generate dall’intelligenza artificiale per i prompt nel set di prompt del dashboard di Presenza dei brand. Analizza tali pagine per menzioni dei brand, sentiment, share of voice e citazioni AI. Confronta le prestazioni del tuo marchio con quelle dei concorrenti del mercato, identifica argomenti ricorrenti e genera consigli per risolvere i gap di percezione sulle pagine che contano di più per i sistemi di intelligenza artificiale.

Se non vengono rilevati URL citati per i prompt nel set di prompt, questa opportunità non verrà visualizzata nel dashboard.

I risultati vengono visualizzati in due schede: **Suggerimenti** e **Prestazioni**.

## Suggerimenti

Questa scheda mostra consigli per migliorare la percezione del brand negli URL principali. I suggerimenti sono organizzati in tre schede secondarie: **Suggerimenti correnti**, **Suggerimenti corretti** e **Suggerimenti ignorati**.

![Scheda Suggerimenti](/help/dashboards/opportunities/assets/cited-sentiment-suggestions.png)

La tabella dei suggerimenti include le colonne riportate di seguito.

- **Suggerimento**: il miglioramento consigliato per colmare il divario di percezione.
- **Priorità** — Livello di urgenza (critico, elevato, Medium, basso).
- **Azioni**: apre un pannello con passaggi specifici per implementare il consiglio, inclusi i team responsabili.

Quando si espande un suggerimento, viene visualizzata una sezione di **Analisi IA** con:

- **Perché questo richiede un miglioramento**: una spiegazione del divario di percezione identificato, inclusi gli URL citati che non rappresentano adeguatamente il tuo marchio e il contesto competitivo.
- **Come migliorare** — Linee guida specifiche su attività di sensibilizzazione, creazione di contenuti o azioni di partnership per colmare il divario.
- **Risultato previsto**: risultato previsto dell&#39;implementazione del consiglio.

## Prestazioni

La scheda **Prestazioni** fornisce un raggruppamento dettagliato delle prestazioni del brand nelle pagine sopra citate. È organizzato in quattro sezioni.

### Panorama del mercato

Confronta le prestazioni del tuo marchio con i marchi associati e con i concorrenti del mercato in base alle menzioni presenti nelle pagine citate.

![Orizzontale di mercato](/help/dashboards/opportunities/assets/cited-sentiment-landscape.png)

Mostra:

- **Menzioni dei brand nelle pagine**: il tuo share of voice rispetto ai marchi associati e ai concorrenti sul mercato.
- **Tracciamento del mercato**: un grafico filtrabile in cui è possibile selezionare fino a cinque marchi concorrenti per confrontare share of voice tra le pagine analizzate.

### Analisi del sentiment

Tiene traccia della percezione del brand tra le pagine analizzate con un grafico di **Distribuzione Sentiment** che mostra la suddivisione percentuale del sentiment favorevole, neutro e sfavorevole tra le pagine.

![Analisi Sentiment](/help/dashboards/opportunities/assets/cited-sentiment-distribution.png)

### Pagine

Una tabella dettagliata di pagine web citate analizzate con le seguenti colonne:

- **Pagina** — URL della pagina analizzata.
- **Menzioni dei brand**: numero di menzioni dei brand rispetto al totale delle menzioni nella pagina.
- **Share of voice** - Quota di menzioni del tuo marchio relativa a tutti i marchi menzionati.
- **Primi 5 marchi**: i marchi più citati nella pagina.
- **Sentiment**: sentiment complessivo verso il tuo marchio sulla pagina.
- **Citazioni IA** — Numero di risposte IA che hanno citato questa pagina.

### Argomenti

Una tabella di argomenti ricorrenti identificati nelle pagine analizzate, che mostra:

- **Argomento** - Il tema o l&#39;oggetto ricorrente identificato.
- **Menzioni dei brand** — Numero di menzioni dei brand associate all&#39;argomento.
- **Sentiment** - sentiment complessivo associato all&#39;argomento.

Facendo clic su **Dettagli** su qualsiasi argomento viene aperto un drill-down con un riepilogo dell&#39;analisi e le pagine di origine che contribuiscono.

## Prova la demo

Visualizza l&#39;opportunità di analisi dei Sentiment citata in azione utilizzando l&#39;ambiente demo Frescopa - [Visualizza analisi dei Sentiment citata nella demo Frescopa](https://play.llmo.now/org/demo-org/opportunities/cited-analysis/d3a8b217-9f4c-4e88-a612-6b7f91e5c044?siteId=frescopa-demo).

## Domande frequenti

**Perché gli URL più citati sono importanti per le Ricerche IA?**

Gli URL più citati sono le pagine di terze parti a cui i sistemi di IA fanno più spesso riferimento durante la generazione di risposte sul tuo marchio. Il sentiment e l’inquadratura in tali pagine hanno un’influenza diretta e di dimensioni eccessive sul modo in cui l’intelligenza artificiale rappresenta il tuo marchio, più di quelle pagine che vengono raramente citate. Migliorare il modo in cui il brand viene rappresentato su tali pagine specifiche è una delle azioni con la massima leva possibile per la visibilità AI.

**Perché questa opportunità non viene visualizzata nel dashboard?**

Questa opportunità viene visualizzata solo quando vengono rilevati gli URL citati per i prompt nel set di prompt del dashboard di Presenza dei brand. Se per tali prompt non sono stati identificati URL citati, l’opportunità non viene visualizzata.

**Cosa significa Pagine saltate?**

Le pagine ignorate sono URL citati che non è stato possibile analizzare, in genere perché la pagina si trova dietro un paywall, richiede l’autenticazione o blocca l’accesso automatico. Queste pagine vengono conteggiate ma escluse dall’analisi di sentiment e menzione del brand.

**Cos&#39;è Share of voice?**

Share of voice è la percentuale del tuo marchio sul totale delle menzioni dei brand su una determinata pagina o su tutte le pagine analizzate, rispetto a tutti gli altri marchi menzionati.

**Cosa sono le citazioni AI?**

Le citazioni basate su IA mostrano quante risposte basate su IA sono state citate in una determinata pagina. Un numero più elevato di citazioni IA indica che la pagina è attivamente utilizzata dai sistemi di IA durante la generazione di risposte su argomenti correlati, rendendo il sentiment su tali pagine particolarmente importante per la rappresentazione di IA del brand.

**Come vengono identificati i concorrenti del mercato?**

I concorrenti vengono identificati automaticamente in base al settore del tuo marchio e ai marchi più frequentemente citati nelle pagine analizzate. Puoi anche selezionare manualmente fino a cinque marchi da confrontare nel grafico Tracciamento del mercato.

**Con quale frequenza viene aggiornata l&#39;analisi?**

L’analisi riflette gli URL citati rilevati fino alla data indicata nell’intestazione della dashboard. Rivedi l’opportunità dopo aver implementato le raccomandazioni per tenere traccia delle modifiche in sentiment e share of voice.
