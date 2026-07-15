---
title: Arricchimento della pagina dettagli prodotto
description: Scopri come LLM Optimizer identifica le pagine di prodotto in cui i dati del catalogo sono nascosti dagli agenti di intelligenza artificiale e come recuperare tale visibilità utilizzando l’ottimizzazione basata su edge e gli approfondimenti del catalogo dei prodotti basati su Adobe Commerce.
feature: Opportunities
autotag-review: '2026-07-15T17:50:18.330Z'
TQID: 'https://experienceleague.adobe.com/UINqU57uqqbNJE3cV6zK56hxCcAmRrMMv-esNEfxqKI'
product_v2:
  - id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2:
  - id: e1b649f0-0a61-46e4-9082-64d5cb2576c6
  - id: ef4e63f5-cb4d-462d-bf9a-1f617edf2a3a
subfeature_v2:
  - id: a6256a78-8814-462c-9627-86699b39cee1
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
source-git-commit: 2705cf26faea9c09817bbdcec4b4c531552df7ba
workflow-type: tm+mt
source-wordcount: 1210
ht-degree: 7%

---


# Arricchisci pagine dettagli prodotto

Gli agenti di intelligenza artificiale possono solo consigliare prodotti che possono comprendere completamente. Nella maggior parte dei punti vendita commerce, le pagine di prodotto sono progettate per gli acquirenti umani. Di conseguenza, questi prodotti si basano su schede renderizzate da JavaScript, pannelli espandibili, procedure guidate per gli acquisti, modali interattivi e collegamenti a varianti, specifiche e funzioni dei prodotti di superficie. Gli agenti di intelligenza artificiale non analizzano le profondità della pagina dei dettagli del prodotto, il che significa che questi dati di prodotto avanzati non vengono mai visti dai crawler LLM che alimentano il rilevamento basato sull’intelligenza artificiale, anche quando è completamente visibile ai visitatori umani.

L’opportunità Arricchisci pagine dei dettagli del prodotto identifica le pagine dei prodotti nel catalogo Adobe Commerce in cui esiste questo gap di visibilità. Basato sul catalogo Adobe Commerce, confronta ciò a cui gli agenti di intelligenza artificiale possono accedere sulla vetrina con i dati completi sui prodotti disponibili nel catalogo e mette in evidenza tutti gli attributi, le varianti e la profondità delle caratteristiche dei prodotti mancanti dalla vista dell’agente di intelligenza artificiale.

Mostra le seguenti metriche chiave a colpo d’occhio:

- **Pagine prodotto**: l&#39;elenco di tutte le pagine dei dettagli prodotto identificate con un gap di visibilità dei dati del catalogo.
- **Traffico agente**: il totale delle visite e delle interazioni in un sito avviate e guidate da agenti di intelligenza artificiale autonomi (come assistenti o bot basati su LLM) che agiscono per conto degli utenti per scoprire, recuperare o interagire con i contenuti.

![Arricchisci dashboard pagine dettagli prodotto](/help/dashboards/opportunities/assets/enrich-product-detail-pages-overview.png)

Questa opportunità può essere ottimizzata mediante l’[ottimizzazione nella rete edge](https://experienceleague.adobe.com/it/docs/llm-optimizer/using/resources/optimize-at-edge/overview#what-is-optimize-at-edge). Le ottimizzazioni vengono distribuite esclusivamente agli agenti di intelligenza artificiale senza alcun impatto sui visitatori umani (consegna solo bot), vengono applicate a livello di CDN senza la necessità di modifiche a CMS o catalogo e possono avere effetto in pochi minuti senza il coinvolgimento degli sviluppatori, rendendolo un percorso di distribuzione veloce e a basso rischio per cataloghi di prodotti di grandi dimensioni.

## Come funziona

Adobe Commerce Catalog Agent legge i dati completi del catalogo dei prodotti, tra cui: varianti, relazioni di prodotto più approfondite, attributi, facet, metadati delle categorie e tutte le caratteristiche del prodotto. Quindi confronta i dati con ciò che è effettivamente accessibile agli agenti di intelligenza artificiale sulla corrispondente PDP della vetrina. Le pagine in cui i dati del catalogo sono nascosti dai crawler di IA vengono visualizzate nella tabella **URL con suggerimenti**, con priorità in base al volume di traffico agente.

Per ogni pagina di prodotto interessata, LLM Optimizer fornisce:

- **Anteprima analisi IA**: elenco completo delle informazioni del catalogo mancanti nella visualizzazione dell&#39;agente di IA e del motivo per cui sono importanti per l&#39;individuazione dei prodotti basata su LLM, incluso un elenco di punti dati recuperabili quali varianti di prodotto, opzioni di dimensione, specifiche del materiale e dettagli di compatibilità, tra gli altri.

La correzione viene applicata utilizzando [Ottimizza in Edge](https://experienceleague.adobe.com/it/docs/llm-optimizer/using/resources/optimize-at-edge/overview#what-is-optimize-at-edge), la funzionalità di distribuzione di Adobe basata su Edge che fornisce uno snapshot HTML completamente pre-renderizzato e compatibile con l&#39;intelligenza artificiale agli agenti utente LLM a livello CDN. In questo modo vengono recuperati tutti i dati del catalogo precedentemente nascosti (comprese le varianti di prodotto, le specifiche tecniche e i dettagli delle funzioni) senza toccare il catalogo Commerce o l’interfaccia utente visibile della vetrina.

![URL con tabella dei suggerimenti](/help/dashboards/opportunities/assets/enrich-product-detail-pages-suggestions.png)

## URL con suggerimenti

Nella tabella **URL con suggerimenti** sono elencate tutte le pagine di prodotto identificate che beneficiano di un&#39;ottimizzazione. Per ogni URL di prodotto puoi:

- **Anteprima** per visualizzare l&#39;analisi basata su IA, incluse le informazioni del catalogo mancanti e il motivo per cui sono importanti per la reperibilità basata su IA
- **Contrassegna come fisso** dopo la distribuzione e la convalida dell&#39;ottimizzazione
- **Ignora** suggerimenti non rilevanti per la tua strategia di merchandising

I suggerimenti sono organizzati in tre viste: **Suggerimenti correnti**, **Suggerimenti corretti** e **Suggerimenti ignorati**. Una volta distribuito, un suggerimento passa a Suggerimenti corretti con uno stato di **Ottimizzato** e un&#39;azione **Visualizza Live** per verificare che l&#39;arricchimento sia attivo per il traffico agente. I suggerimenti corretti possono essere ripristinati in qualsiasi momento.

## Implementazione dell’ottimizzazione

Dopo aver rivisto i suggerimenti e selezionato le pagine dei prodotti da ottimizzare, fai clic su **Distribuisci ottimizzazioni** per pubblicare l&#39;arricchimento nel server Edge CDN. Una finestra di dialogo di conferma della **Distribuzione ad Edge** mostra gli URL del prodotto selezionati, il tipo di ottimizzazione e l&#39;arricchimento applicati. Dopo la distribuzione, una schermata di conferma conferma conferma quali pagine di prodotto sono state ottimizzate correttamente.

L’ottimizzazione viene fornita esclusivamente agli agenti utente AI tramite il livello Edge della rete CDN. I visitatori continuano a vedere la tua esperienza nella vetrina esistente esattamente come prima, senza modifiche alla progettazione PDP, alle prestazioni della pagina o all&#39;esperienza del marchio.

>[!NOTE]
>
>La distribuzione delle ottimizzazioni richiede (1) la connessione di LLM Optimizer ad Adobe Commerce e (2) il completamento del processo di onboarding Ottimizza in Edge.

Se l’istanza Commerce non è ancora connessa a LLM Optimizer, prima di poter applicare gli arricchimenti verrai indirizzato alla configurazione della connessione.

Se non hai ancora effettuato l’onboarding, facendo clic su **Implementa ottimizzazioni** ti consentirà di passare al processo di onboarding. Per informazioni complete sul funzionamento di Ottimizza su Edge, sui provider CDN supportati e sul processo di onboarding, consulta la pagina [Ottimizza su Edge](https://experienceleague.adobe.com/it/docs/llm-optimizer/using/resources/optimize-at-edge/overview#what-is-optimize-at-edge).

![Finestra di dialogo Ottimizza su Edge](/help/dashboards/opportunities/assets/enrich-product-detail-pages-deploy.png)

## Prova nella demo

Scopri l’opportunità di arricchire le pagine dei dettagli del prodotto in azione utilizzando l’ambiente demo Frescopa.

[Visualizzare le pagine dei dettagli dei prodotti nella demo di Frescopa](https://play.llmo.now/org/demo-org/opportunities/commerce-product-page-enrichment/4e8b0428-0893-4864-a00e-fc1d77fb3372?siteId=9ae8877a-bbf3-407d-9adb-d6a72ce3c5e3)

## Domande frequenti

**Perché i dati del catalogo prodotti sono nascosti dagli agenti di IA?**

I punti vendita Commerce sono costruiti per gli acquirenti umani. Caratteristiche del prodotto, varianti, opzioni di dimensione, dettagli del materiale e altre specifiche tecniche vengono spesso presentate tramite interazioni guidate da JavaScript come schede, pannelli comprimibili, modali pop-up, collegamenti e procedure guidate per gli acquisti. Gli agenti di intelligenza artificiale non analizzano le profondità della pagina dei dettagli del prodotto, pertanto tutti questi dati sono invisibili ai crawler LLM anche quando sono completamente presenti nel catalogo dei prodotti. Il risultato è che gli agenti di intelligenza artificiale fanno raccomandazioni sul prodotto in base a una frazione delle informazioni effettive disponibili sul prodotto.

**Quali tipi di dati di prodotto recupera questa ottimizzazione?**

L’agente catalogo recupera tutte le informazioni sui prodotti disponibili nel catalogo Adobe Commerce che non sono attualmente accessibili nella vetrina per gli agenti di intelligenza artificiale. Ciò include caratteri del prodotto, relazioni, varianti (dimensioni, colori, configurazioni), specifiche tecniche e attributi, dettagli di compatibilità, metadati di categoria e valori di facet.

**Questa ottimizzazione influirà sulle prestazioni dei visitatori umani, dei bot SEO o della vetrina?**

No. Ottimizza su Edge è mirato solo agli user agent di IA. I visitatori umani e i bot SEO ricevono la pagina di prodotto originale esattamente come prima, senza modifiche alla loro esperienza, alle prestazioni di caricamento della pagina o alla progettazione della vetrina.

**È necessario modificare il catalogo Commerce, CMS o coinvolgere sviluppatori?**

No. L’ottimizzazione viene applicata al livello Edge della rete CDN e non richiede modifiche al catalogo Adobe Commerce, distribuzioni del codice e coinvolgimento degli sviluppatori. Una volta effettuato l’onboarding per ottimizzare in Edge, puoi distribuire e ripristinare gli arricchimenti in pochi minuti direttamente dall’interfaccia di LLM Optimizer.

**Cosa succede se i dati del prodotto cambiano dopo la distribuzione?**

Per l’opportunità di arricchire le pagine dei dettagli del prodotto, LLM Optimizer utilizza impostazioni TTL di cache ridotta in modo che qualsiasi aggiornamento del prodotto nel catalogo Commerce attivi un aggiornamento in pochi minuti. Gli agenti di intelligenza artificiale riceveranno sempre i dati di prodotto più aggiornati disponibili.
