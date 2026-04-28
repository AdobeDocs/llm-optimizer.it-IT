---
title: Recupera visibilità dei contenuti
description: Scopri come LLM Optimizer identifica le pagine in cui i contenuti critici sono nascosti dagli agenti di intelligenza artificiale e come recuperare tale visibilità utilizzando l’ottimizzazione basata su Edge.
feature: Opportunities
source-git-commit: fd3c1b5ab75b54a93be06460ba15b382e74d8e3a
workflow-type: tm+mt
source-wordcount: '928'
ht-degree: 1%

---


# Recupera visibilità dei contenuti

Gli agenti di intelligenza artificiale possono solo citare contenuti a cui possono accedere. Quando i contenuti chiave sulle pagine sono nascosti dietro il rendering lato client e i carichi dinamici (come descrizioni di prodotti, valutazioni degli utenti, ricette e commenti), gli agenti di intelligenza artificiale li perdono completamente, lasciando contenuti preziosi invisibili ai sistemi che potrebbero citarli.

L&#39;opportunità Recover Visibilità dei contenuti identifica le pagine del sito in cui è presente questo gap di visibilità. Per ogni pagina interessata, mostra esattamente quale contenuto manca dalla vista dell’agente di intelligenza artificiale, evidenzia il gap e consente di applicare correzioni senza alcuna modifica di CMS o coinvolgimento degli sviluppatori.

Mostra tre metriche chiave a colpo d’occhio:

- **URL** — Numero di pagine identificate con un intervallo di visibilità dei contenuti.
- **Guadagno stimato del contenuto**: il moltiplicatore stimato del contenuto che può essere recuperato applicando l&#39;ottimizzazione.
- **Visibilità dei contenuti media**: la percentuale media di contenuto attualmente visibile agli agenti di intelligenza artificiale nelle pagine interessate.

![Ripristina dashboard Visibilità dei contenuti](/help/dashboards/opportunities/assets/recover-content-visibility-overview.png)

Per una panoramica video di questa opportunità, puoi guardare [Recupera Visibilità dei contenuti](https://www.youtube.com/watch?v=BigPyJssFCw).

Questa opportunità può essere ottimizzata utilizzando [Ottimizza in Edge](/help/dashboards/optimize-at-edge/overview.md). Le ottimizzazioni vengono distribuite esclusivamente agli agenti di intelligenza artificiale senza alcun impatto sui visitatori umani (consegna solo bot). Le ottimizzazioni vengono quindi applicate a livello di CDN senza che siano necessarie modifiche a CMS e possono diventare effettive in pochi minuti senza il coinvolgimento degli sviluppatori, rendendola un’implementazione rapida e a basso rischio.

## Come funziona

LLM Optimizer analizza le pagine confrontando ciò a cui gli agenti di intelligenza artificiale possono accedere rispetto a ciò che è effettivamente presente sulla pagina. Le pagine che ricevono un traffico agentico elevato ma con una visibilità dei contenuti bassa vengono visualizzate nella tabella **URL con suggerimenti**, con priorità in base al volume di traffico agentico.

Per ogni URL interessato, LLM Optimizer fornisce:

- **Analisi IA**: descrizione del contenuto mancante e del motivo per cui è importante per la citabilità LLM, insieme a un elenco di riferimenti al contenuto che è possibile recuperare
- **Visibilità dei contenuti**: la percentuale di contenuto attualmente visibile agli agenti di intelligenza artificiale sulla pagina
- **Percentuale di guadagno contenuto**: il moltiplicatore stimato del contenuto recuperabile se viene applicata l&#39;ottimizzazione
- **Anteprima**: confronto affiancato di HTML che mostra l&#39;aspetto attuale della pagina rispetto alla post-ottimizzazione, in modo da poter convalidare la modifica prima della distribuzione

La correzione viene applicata utilizzando [Ottimizza in Edge](/help/dashboards/optimize-at-edge/overview.md), la funzionalità di distribuzione di Adobe basata su Edge che fornisce uno snapshot HTML completamente pre-renderizzato e compatibile con l&#39;intelligenza artificiale agli agenti utente LLM a livello CDN, recuperando i contenuti precedentemente nascosti senza toccare il CMS.

<!-- [URLs with suggestions](/help/dashboards/opportunities/assets/recover-content-visibility-urls.png)-->

## URL con suggerimenti

La tabella **URL con suggerimenti** elenca tutte le pagine interessate e può essere filtrata per classificazione. Per ogni URL è possibile:

- **Espandere la riga** per visualizzare l&#39;analisi di IA, specificando il contenuto mancante e il motivo per cui è importante.
- **Anteprima** del confronto affiancato di HTML tra la pagina corrente e la versione di post-ottimizzazione.
- **Contrassegna come risolto** dopo aver risolto il problema.
- **Ignora** suggerimenti non rilevanti.

I suggerimenti sono organizzati in tre visualizzazioni: **Suggerimenti correnti**, **Suggerimenti corretti** e **Suggerimenti ignorati**. Una volta distribuito, un suggerimento passa a Suggerimenti corretti con uno stato di **Ottimizzato** e un&#39;azione **Visualizza Live** per verificare che l&#39;ottimizzazione sia attiva per il traffico agente. È inoltre possibile eseguire il rollback dei suggerimenti corretti in qualsiasi momento.

![Sono stati corretti alcuni suggerimenti con stato Ottimizzato](/help/dashboards/opportunities/assets/recover-content-visibility-fixed.png)

## Distribuzione dell’ottimizzazione

Dopo aver rivisto i suggerimenti e selezionato gli URL da ottimizzare, fai clic su **Distribuisci ottimizzazioni** per pubblicare la correzione nel server Edge CDN. Una finestra di dialogo di conferma della **Distribuzione ad Edge** mostra gli URL selezionati, il loro tipo (Pre-rendering) e il suggerimento applicato. Dopo la distribuzione, una schermata di conferma conferma conferma gli URL ottimizzati correttamente.

>[!NOTE]
>
>La distribuzione delle ottimizzazioni richiede il completamento del processo di onboarding Ottimizza in Edge. Se non hai ancora effettuato l&#39;onboarding, fai clic su **Distribuisci ottimizzazioni** per passare al processo di onboarding. Per informazioni complete sul funzionamento di Ottimizza in Edge, sui provider CDN supportati e sul processo di onboarding, visita la pagina [Ottimizza in Edge](/help/dashboards/optimize-at-edge/overview.md).

![Finestra di dialogo Distribuisci in Edge](/help/dashboards/opportunities/assets/recover-content-visibility-deploy.png)

## Prova la demo

Visualizzare l&#39;opportunità Recover Visibilità dei contenuti in azione utilizzando l&#39;ambiente demo Frescopa.

[Visualizza Recupera Visibilità dei contenuti nella demo di Frescopa](https://play.llmo.now/org/demo-org/opportunities/prerender/75729489-756a-4c2b-9905-155b1715da5c)

## Domande frequenti

**Perché il contenuto della pagina è nascosto dagli agenti di IA?**

La maggior parte dei siti web moderni si basa su JavaScript per caricare il contenuto in modo dinamico dopo la richiesta della pagina iniziale. Gli agenti di intelligenza artificiale generalmente non eseguono JavaScript, pertanto il contenuto sottoposto a rendering lato client (elenchi di prodotti, recensioni degli utenti, collegamenti agli articoli di blog ed elementi simili) non viene mai visualizzato dall’agente di intelligenza artificiale, anche se è completamente visibile ai visitatori umani.

**Questa ottimizzazione influirà sui visitatori umani o sui bot SEO?**

No. Ottimizza in Edge esegue il targeting solo degli agenti utente di intelligenza artificiale. I visitatori umani e i bot SEO ricevono la pagina originale esattamente come prima, senza modifiche alla loro esperienza o alle loro prestazioni.

**Devo cambiare il mio CMS o coinvolgere sviluppatori?**

No. L’ottimizzazione viene applicata al server Edge della rete CDN e non richiede modifiche di authoring, distribuzioni del codice o coinvolgimento degli sviluppatori. Una volta effettuato l’onboarding per ottimizzare in Edge, puoi distribuire e ripristinare le modifiche in pochi minuti direttamente dall’interfaccia di LLM Optimizer.

**Cosa succede se il contenuto della pagina cambia dopo la distribuzione?**

Per Recover Visibilità dei contenuti, LLM Optimizer utilizza le impostazioni TTL della cache ridotta in modo che qualsiasi aggiornamento del contenuto sul sito attivi un aggiornamento in pochi minuti. Gli agenti di intelligenza artificiale riceveranno sempre la versione più aggiornata del contenuto.

**Come si inizia a utilizzare Ottimizza in Edge?**

Consulta la pagina [Ottimizza in Edge](/help/dashboards/optimize-at-edge/overview.md) per il processo di onboarding completo, le guide alla configurazione CDN e i prerequisiti.
