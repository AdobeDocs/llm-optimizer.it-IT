---
title: Arricchimento del catalogo prodotti
description: Scopri come LLM Optimizer identifica i prodotti con descrizioni generiche o tecnicamente dense e come migliorarle utilizzando arricchimenti narrativi generati dall’intelligenza artificiale basati su Adobe Commerce.
feature: Opportunities
autotag-review: '2026-05-15T17:45:51.619Z'
TQID: 'https://experienceleague.adobe.com/5ihGQ8L-37uWsZSDo4TVCUPBPqsqqQ5waGbH3VKPIig'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: c0713b97-4af8-4c41-b742-5afcc6ced468
subfeature_v2: id: e1b649f0-0a61-46e4-9082-64d5cb2576c6
topic_v2: id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
source-git-commit: 564171851fdccee43afd233da143d66182464889
workflow-type: tm+mt
source-wordcount: 1266
ht-degree: 0%

---


# Arricchisci catalogo prodotti

I moduli LLM tentano di collegare gli attributi del prodotto al valore reale, ai casi d’uso e alle intenzioni dell’acquirente. Quando i nomi e le descrizioni dei prodotti non comunicano chiaramente tale valore, è meno probabile che i prodotti vengano citati, consigliati o visualizzati nel discovery basato sull’intelligenza artificiale. Questo perché, gli agenti di intelligenza artificiale ragionano attraverso le relazioni, non campi di dati non elaborati. Un elenco di prodotti con un nome come &quot;Coffee Grinder X200&quot; e una descrizione che elenca le specifiche tecniche (potenza del motore, impostazioni di macinazione, ecc.) dà un LLM molto poco per lavorare quando un acquirente chiede &quot;il miglior tritacarne per espresso per un barista di casa&quot;.

L’opportunità di arricchimento del catalogo prodotti identifica i prodotti nel catalogo Commerce in cui i nomi e le descrizioni sono troppo generici, tecnicamente densi o troppo ambigui per consentire un’interpretazione accurata da parte dei moduli LLM. Basato su Adobe Commerce, genera arricchimenti basati su narrazioni e ricchi di intenti per i nomi e le descrizioni dei prodotti e li applica direttamente al catalogo Commerce con un solo clic.

Mostra due metriche chiave a colpo d’occhio:

- **URL**: elenco di pagine di dettagli prodotto (prodotti nel catalogo) valutate per la qualità dell&#39;arricchimento.
- **Traffico agente**: il totale delle visite e delle interazioni in un sito avviate e guidate da agenti di intelligenza artificiale autonomi (come assistenti o bot basati su LLM) che agiscono per conto degli utenti per scoprire, recuperare o interagire con i contenuti.

![Arricchisci dashboard catalogo prodotti](/help/dashboards/opportunities/assets/enrich-product-catalog-overview.png)

>[!NOTE]
>
>Questa opportunità è attualmente in Beta e può essere attivata dai clienti Adobe Commerce. Per accedere alla versione beta, rivolgiti al tuo Account Manager.

## Come funziona

Adobe Commerce Catalog Agent legge i dati del catalogo dei prodotti e analizza ogni SKU di prodotto, inclusi tutti gli attributi tecnici, il contesto della categoria, le varianti e il nome e la descrizione esistenti. Identifica i prodotti in cui il nome o la descrizione corrente non sono in grado di comunicare il valore relativo all’acquirente e genera un’alternativa arricchita che traduce i dettagli tecnici in un linguaggio chiaro e allineato alle finalità.

Ad esempio, un prodotto denominato *&quot;Coffee Grinder X200&quot;* con una descrizione che elenca &quot;18 impostazioni di macinazione, motore 450W&quot; può essere arricchito per spiegare che &quot;X200 offre la coerenza dell&#39;espresso a livello di caffè perché il suo sistema di macinazione a 18 fasi è abbinato a un motore ad alta coppia per risultati ripetibili a casa&quot;. Attributi come prezzo e inventario sono intenzionalmente esclusi dall’arricchimento: Catalog Agent si concentra sugli attributi che stimolano il valore e spiegano cos’è il prodotto, come viene utilizzato e perché è importante per un acquirente.

I prodotti con suggerimenti di arricchimento vengono visualizzati nella tabella **URL con suggerimenti**, con priorità in base all&#39;impatto dell&#39;arricchimento. Per ogni prodotto identificato, LLM Optimizer fornisce:

- **Nome corrente**: il nome del prodotto esistente visualizzato nel catalogo Adobe Commerce.
- **Nome aggiornato**: il nome di prodotto generato dall&#39;intelligenza artificiale e basato su valori che comunica il contesto e l&#39;intento rilevanti per gli acquirenti ai moduli LLM.
- **Descrizione corrente**: la descrizione del prodotto esistente visualizzata nel catalogo Adobe Commerce.
- **Descrizione suggerita**: la descrizione generata dall&#39;intelligenza artificiale che traduce gli attributi tecnici del prodotto in una narrazione che aiuta gli operatori LLM a capire cos&#39;è il prodotto, il suo valore narrativo e perché è importante.

![Tabella dei prodotti con suggerimenti](/help/dashboards/opportunities/assets/enrich-product-catalog-suggestions.png)

## Prodotti con suggerimenti

Nella tabella **URL con suggerimenti** sono elencati tutti i prodotti con opportunità di arricchimento. Per ogni prodotto è possibile:

- **Espandere la riga** per visualizzare l&#39;analisi di IA e l&#39;arricchimento proposto.
- **Modifica** il nome o la descrizione del prodotto proposto prima di fare domanda, per allinearli alle linee guida per la voce e il merchandising del tuo marchio.
- **Distribuisci l&#39;ottimizzazione** per i prodotti che desideri arricchire e pubblicarla direttamente nel tuo catalogo Adobe Commerce.
- **Contrassegna come Fisso** dopo aver rivisto e applicato l&#39;arricchimento.
- **Ignora** suggerimenti non rilevanti per la strategia del catalogo.

I suggerimenti sono organizzati in tre visualizzazioni: **Suggerimenti correnti**, **Suggerimenti corretti** e **Suggerimenti ignorati**. Dopo aver applicato un arricchimento, questo viene spostato su Fixed Suggestions con uno stato di **Applied** e un&#39;azione **View in Catalog** per verificare l&#39;aggiornamento in Adobe Commerce. Gli arricchimenti applicati possono essere ripristinati in qualsiasi momento, ripristinando il nome e la descrizione del prodotto originali.

<!--[Fixed suggestions with Applied status](/help/dashboards/opportunities/assets/enrich-product-catalog-fixed.png)-->

## Distribuzione dell’ottimizzazione

Dopo aver rivisto e modificato facoltativamente i suggerimenti per i prodotti selezionati, fai clic su **Distribuisci ottimizzazioni** per pubblicare il nome e la descrizione del prodotto aggiornati nel catalogo Adobe Commerce. Una finestra di dialogo di conferma mostra i prodotti selezionati e le modifiche applicate. Dopo la conferma, una schermata dei risultati conferma quali prodotti sono stati aggiornati correttamente.

Poiché gli arricchimenti vengono applicati direttamente al catalogo di Adobe Commerce, i nomi e le descrizioni dei prodotti aggiornati sono immediatamente disponibili su tutti i canali che utilizzano il catalogo, inclusi i punti vendita, i feed pubblicitari e tutte le integrazioni di prodotti LLM dirette. In questo modo, ogni superficie in cui appare il prodotto comunica informazioni coerenti e di alta qualità.

>[!NOTE]
>
>L’arricchimento del catalogo richiede la connessione di LLM Optimizer ad Adobe Commerce. Se l’istanza Commerce non è ancora connessa a LLM Optimizer, prima di poter applicare gli arricchimenti verrai indirizzato alla configurazione della connessione.

![Finestra di dialogo Applica arricchimenti](/help/dashboards/opportunities/assets/enrich-product-catalog-deploy.png)

## Prova la demo

Scopri l’opportunità di arricchire il catalogo dei prodotti in azione utilizzando l’ambiente demo Frescopa.

[Scopri come arricchire il catalogo dei prodotti nella demo di Frescopa](https://play.llmo.now/org/demo-org/opportunities/commerce-product-catalog-enrichment/e5f2a854-7477-421c-820f-74d5dd595647?siteId=9ae8877a-bbf3-407d-9adb-d6a72ce3c5e3)

## Domande frequenti

**Perché i nomi e le descrizioni dei prodotti generici impediscono il rilevamento di IA?**

I moduli LLM non confrontano i prodotti con le query dell’acquirente cercando la sovrapposizione delle parole chiave. Ragionano sulle relazioni, sul collegare ciò che un acquirente intende trovare con ciò che un prodotto fa realmente, per chi è e come si confronta con le alternative. Un nome di prodotto o una descrizione che elenca le specifiche tecniche senza comunicare valore reale offre un LLM molto poco contesto per lavorare con. Il risultato è che è meno probabile che il tuo prodotto venga citato quando un acquirente fa una domanda rilevante, anche se il tuo prodotto è la migliore corrispondenza per le sue esigenze.

**Quali attributi di prodotto utilizza l&#39;agente catalogo per generare arricchimenti?**

L’agente del catalogo utilizza attributi che stimolano il valore nel catalogo Commerce per aiutare gli operatori del settore a capire cos’è un prodotto, come viene utilizzato e perché è importante. Attributi che stimolano il valore come le caratteristiche del prodotto, i casi d’uso, le proprietà del materiale, il contesto della categoria e i dettagli di compatibilità. Attributi come prezzi e livelli di inventario sono intenzionalmente esclusi, in quanto non contribuiscono alla comprensione semantica dei prodotti e possono rendere le descrizioni meno durature con il cambiare delle condizioni.

**Posso modificare l&#39;arricchimento generato da IA prima di applicarlo?**

Sì. Ogni suggerimento include un’anteprima modificabile del nome e della descrizione del prodotto proposti. Puoi modificare l’arricchimento per allinearlo alla voce del tuo marchio, correggere eventuali imprecisioni o incorporare un contesto aggiuntivo prima di applicarlo al catalogo.

**L&#39;arricchimento cambierà ciò che i visitatori umani vedranno nella mia vetrina?**

Sì, i visitatori vedranno il nome e la descrizione del prodotto aggiornati nella vetrina, insieme a tutti gli altri canali che provengono dal catalogo Commerce. Questo è intenzionale: l’obiettivo è migliorare il modo in cui il prodotto viene compreso ovunque, non solo dagli agenti di intelligenza artificiale, ma anche evitare rischi di mascheramento.

**Cosa succede negli altri canali di vendita quando applico un arricchimento?**

Poiché l’arricchimento viene scritto direttamente nel catalogo Adobe Commerce, si propaga automaticamente a tutti i canali che utilizzano il catalogo commerce come fonte di verità, inclusi più vetrine, pipeline pubblicitarie e qualsiasi feed di prodotto LLM diretto. Questo garantisce la coerenza del marchio e informazioni coerenti sui prodotti per i moduli LLM che scansionano Internet per i prodotti.

**È possibile eseguire il rollback di un arricchimento se non si è soddisfatti del risultato?**

Sì. Gli arricchimenti applicati possono essere ripristinati in qualsiasi momento dalla vista Suggerimenti fissi, ripristinando il nome e la descrizione del prodotto originali nel catalogo Adobe Commerce.
