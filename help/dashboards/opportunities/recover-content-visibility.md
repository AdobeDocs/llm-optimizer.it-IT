---
title: Recupera visibilità dei contenuti
description: Scopri come LLM Optimizer identifica le pagine in cui i contenuti importanti sono nascosti agli agenti IA e come recuperarne la visibilità utilizzando l’ottimizzazione basata su rete edge.
feature: Opportunities
autotag-review: '2026-05-15T17:56:37.098Z'
TQID: 'https://experienceleague.adobe.com/rHqJL4RrJr1ghsy4fhXe-JLDrWruNSZgVhXQeRN-iyA'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: a0b5a505-2fd7-4c3d-b61c-b557fb6f0558id: c0713b97-4af8-4c41-b742-5afcc6ced468
subfeature_v2: id: e1b649f0-0a61-46e4-9082-64d5cb2576c6
topic_v2: id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
source-git-commit: 564171851fdccee43afd233da143d66182464889
workflow-type: tm+mt
source-wordcount: 928
ht-degree: 100%

---


# Recupera visibilità dei contenuti

Gli agenti IA possono citare solo i contenuti a cui hanno accesso. Se alcuni contenuti chiave delle tue pagine sono nascosti dietro il rendering lato client e il caricamento dinamico (come descrizioni di prodotti, valutazioni degli utenti, ricette e commenti), tali contenuti non possono essere rilevati dagli agenti IA. Contenuti preziosi diventano quindi invisibili a quei sistemi che dovrebbero invece essere in grado di citarli nelle loro risposte.

L’opportunità Recupera visibilità dei contenuti identifica le pagine del tuo sito che presentano questa lacuna di visibilità. Per ogni pagina identificata, vengono mostrati esattamente i contenuti invisibili all’agente IA, evidenzia il divario di visibilità e ti consente di applicare direttamente le correzioni senza apportare variazioni al CMS o coinvolgere gli sviluppatori.

Mette subito in evidenza tre metriche chiave:

- **Gli URL**: numero di pagine identificate con un divario di visibilità dei contenuti.
- **Il guadagno di contenuti stimato**: il moltiplicatore stimato di contenuti che potrebbero essere recuperati applicando l’ottimizzazione.
- **La visibilità media dei contenuti**: la percentuale media di contenuti attualmente visibili agli agenti IA nelle pagine interessate.

![Dashboard Recupera visibilità dei contenuti](/help/dashboards/opportunities/assets/recover-content-visibility-overview.png)

Per una panoramica video di questa opportunità, puoi guardare [Recupera visibilità dei contenuti](https://www.youtube.com/watch?v=BigPyJssFCw).

Questa opportunità può essere ottimizzata mediante l’[ottimizzazione nella rete edge](/help/dashboards/optimize-at-edge/overview.md). Le ottimizzazioni sono fornite esclusivamente agli agenti IA, senza alcun impatto sui visitatori umani (consegna solo a bot). Le ottimizzazioni sono quindi applicate a livello CDN senza dover apportare variazioni al CMS e possono avere effetto in pochi minuti senza coinvolgere gli sviluppatori, garantendo un’implementazione rapida e a basso rischio.

## Come funziona

LLM Optimizer analizza le tue pagine confrontando ciò a cui gli agenti IA possono accedere con ciò che è effettivamente presente sulla pagina. Le pagine che ricevono un traffico da IA agentica elevato ma hanno una bassa visibilità dei contenuti vengono proposte nella tabella degli **URL con suggerimenti**, ordinate per priorità in base al volume di traffico da IA agentica.

Per ciascun URL interessato, LLM Optimizer fornisce:

- **L’analisi IA**: descrizione del contenuto mancante e del motivo della sua rilevanza per la citabilità negli LLM, insieme a un elenco di riferimenti al contenuto che potrebbero essere recuperati
- **La visibilità dei contenuti**: percentuale di contenuti attualmente visibili agli agenti IA in quella pagina
- **Il rapporto di guadagno dei contenuti**: moltiplicatore stimato dei contenuti recuperabili se viene applicata l’ottimizzazione
- **L’anteprima**: confronto di HTML affiancati che mostra l’aspetto attuale della pagina rispetto a quello successivo all’ottimizzazione, affinché tu possa convalidare la modifica prima dell’implementazione

La correzione viene applicata utilizzando[Ottimizza su Edge](/help/dashboards/optimize-at-edge/overview.md), la funzionalità di implementazione basata su Edge di Adobe che offre un’istantanea HTML con pre-rendering completo e ottimizzata per l’IA agli user agent di LLM a livello CDN, recuperando contenuti precedentemente nascosti senza intervenire sul CMS.

<!-- [URLs with suggestions](/help/dashboards/opportunities/assets/recover-content-visibility-urls.png)-->

## URL con suggerimenti

La tabella degli **URL con suggerimenti** elenca tutte le pagine interessate e può essere filtrata per classificazione. Per ciascun URL puoi:

- **Espandere la riga** per visualizzare l’analisi IA, inclusi i contenuti mancanti e il motivo della rilevanza.
- **Mostrare l’anteprima** del confronto di HTML affiancati tra la pagina corrente e la versione successiva all’ottimizzazione.
- **Contrassegnarlo come corretto** dopo aver risolto il problema.
- **Ignorare** i suggerimenti non pertinenti.

I suggerimenti sono organizzati in tre viste: **Suggerimenti correnti**, **Suggerimenti corretti** e **Suggerimenti ignorati**. Una volta implementato, un suggerimento passa in Suggerimenti corretti con stato **Ottimizzato** e un’azione **Visualizza live** per verificare che l’ottimizzazione sia attiva per il traffico da IA agentica. È inoltre possibile ripristinare la versione precedente dei suggerimenti corretti in qualsiasi momento.

![Suggerimenti corretti con stato Ottimizzato](/help/dashboards/opportunities/assets/recover-content-visibility-fixed.png)

## Implementazione dell’ottimizzazione

Dopo aver rivisto i suggerimenti e selezionato gli URL da ottimizzare, fai clic su **Implementa ottimizzazioni** per pubblicare la correzione su Edge CDN. Una finestra di dialogo di conferma **Implementa su Edge** mostra gli URL selezionati, il loro tipo (Pre-rendering) e il suggerimento applicato. Dopo l’implementazione, una schermata conferma gli URL ottimizzati correttamente.

>[!NOTE]
>
>L’implementazione delle ottimizzazioni richiede il completamento del processo di onboarding Ottimizza su Edge. Se non hai ancora effettuato l’onboarding, facendo clic su **Implementa ottimizzazioni** ti consentirà di passare al processo di onboarding. Per informazioni complete sul funzionamento di Ottimizza su Edge, sui provider CDN supportati e sul processo di onboarding, consulta la pagina [Ottimizza su Edge](/help/dashboards/optimize-at-edge/overview.md).

![Finestra di dialogo Ottimizza su Edge](/help/dashboards/opportunities/assets/recover-content-visibility-deploy.png)

## Prova nella demo

Guarda in azione l’opportunità Recupera visibilità dei contenuti utilizzando l’ambiente demo di Frescopa.

[Visualizza Recupera visibilità dei contenuti nella demo di Frescopa](https://play.llmo.now/org/demo-org/opportunities/prerender/75729489-756a-4c2b-9905-155b1715da5c)

## Domande frequenti

**Perché il contenuto della mia pagina è nascosto agli agenti IA?**

La maggior parte dei siti web moderni si basa su JavaScript per caricare contenuti in modo dinamico dopo la richiesta della pagina iniziale. Gli agenti IA generalmente non eseguono JavaScript, pertanto i contenuti sottoposti a rendering lato client (inserzioni di prodotti, recensioni degli utenti, collegamenti agli articoli di blog ed elementi simili) non sono mai visualizzati dall’agente IA, anche se è del tutto visibile ai visitatori umani.

**Questa ottimizzazione interessa i visitatori umani o i bot della SEO?**

No. Ottimizza su Edge è mirato solo agli user agent di IA. I visitatori umani e i bot della SEO ricevono la pagina originale esattamente come prima, senza variazioni della loro esperienza o delle loro prestazioni.

**Devo cambiare il mio CMS o coinvolgere sviluppatori?**

No. L’ottimizzazione è applicata alla CDN Edge non richiede modifiche di authoring, implementazioni del codice o coinvolgimento degli sviluppatori. Una volta effettuato l’onboarding in Ottimizza su Edge, puoi implementare e ripristinare la versione precedente delle modifiche in pochi minuti direttamente dall’interfaccia di LLM Optimizer.

**Cosa succede se il contenuto della mia pagina cambia dopo la distribuzione?**

Per Recupera visibilità dei contenuti, LLM Optimizer utilizza impostazioni TTL della cache ridotta in modo che qualsiasi aggiornamento del contenuto sul sito attivi un aggiornamento in pochi minuti. Gli agenti IA riceveranno sempre la versione più aggiornata del contenuto.

**Come posso iniziare a usare Ottimizza su Edge?**

Consulta la pagina [Ottimizza su Edge](/help/dashboards/optimize-at-edge/overview.md) per il processo di onboarding completo, le guide alla configurazione CDN e i prerequisiti.
