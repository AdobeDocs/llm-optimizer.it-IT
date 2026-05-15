---
title: Aggiungi sommario
description: Scopri come LLM Optimizer identifica le pagine a traffico elevato prive di una chiara struttura di navigazione per gli agenti di intelligenza artificiale e come rivedere e distribuire un sommario con Ottimizza in Edge.
feature: Opportunities
autotag-review: '2026-05-15T17:29:21.334Z'
TQID: 'https://experienceleague.adobe.com/A-Oxmmn-Cb4l9-iVx1TAKxvBTEOxRIAnRe1w1PqF6OI'
product_v2:
  - id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2:
  - id: c0713b97-4af8-4c41-b742-5afcc6ced468
subfeature_v2:
  - id: e1b649f0-0a61-46e4-9082-64d5cb2576c6
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
source-git-commit: 7a92587197cf6a9eec6b01bd4eaeeaf1194d3088
workflow-type: tm+mt
source-wordcount: 655
ht-degree: 0%

---


# Aggiungi sommario

>[!NOTE]
>
> **Accesso anticipato** — questa funzionalità è disponibile in Accesso anticipato. La disponibilità, l’idoneità e parti del flusso di lavoro possono cambiare con la maturazione della funzionalità. Se hai domande sull’accesso, contatta il team del tuo account di Adobe.

L&#39;opportunità Aggiungi sommario identifica le pagine a traffico elevato prive di un **sommario** chiaro e di una guida strutturale, rendendo più difficile per gli agenti di IA analizzare la pagina e mappare le query utente alle sezioni giuste. Introduce un sommario strutturato con **intestazioni collegate ad ancoraggio** che riflettono le sezioni principali della pagina. Questa struttura aiuta gli agenti a estrarre, mappare e citare in modo più affidabile i passaggi rilevanti.

Per ogni URL interessato, puoi rivedere le voci del sommario suggerite, quindi distribuirle con [Ottimizza in Edge](/help/dashboards/optimize-at-edge/overview.md) in modo che il traffico agente riceva un contesto di navigazione più chiaro senza che siano necessarie modifiche al sistema di gestione dei contenuti (CMS).

## Come risolve il problema

Le correzioni vengono applicate utilizzando [Ottimizza in Edge](/help/dashboards/optimize-at-edge/overview.md), che:

- Fornisce agli agenti di intelligenza artificiale uno snapshot HTML pre-renderizzato.
- Aggiunge un sommario alla pagina.
- Funziona a livello CDN (nessuna modifica di CMS).
- È solo IA — nessun impatto sui visitatori umani o sui bot SEO (Search Engine Optimization).
- Distribuisce in pochi minuti ed è **completamente reversibile** dall&#39;interfaccia di LLM Optimizer.

## Come funziona

LLM Optimizer identifica pagine con traffico elevato in cui un **sommario** migliorerebbe il modo in cui gli agenti di intelligenza artificiale navigano nelle intestazioni e nelle sezioni. Per ogni pagina, i suggerimenti vengono inseriti a partire dai titoli già presenti nella pagina, in modo che il sommario rifletta la struttura della pagina.

Gli URL interessati vengono visualizzati nella tabella **URL con suggerimenti** della scheda **Suggerimenti correnti**.

In **Suggerimenti correnti**, per ogni URL è possibile:

- **Espandere la riga** per esaminare il sommario proposto (analizzato dalle intestazioni di pagina e presentato come voci collegate ad ancoraggio).
- **Anteprima** a prima e dopo il confronto.
- **Contrassegna come fisso** se l&#39;opportunità è stata gestita al di fuori di LLM Optimizer.
- **Ignora** suggerimenti non rilevanti.

I suggerimenti sono organizzati in **Suggerimenti correnti**, **Suggerimenti corretti** e **Suggerimenti ignorati**, in linea con gli altri suggerimenti Ottimizza in opportunità Edge.

### Distribuzione dell’ottimizzazione

Quando sei pronto per la pubblicazione sul server Edge di, seleziona i suggerimenti del sommario che desideri distribuire. Il piè di pagina riepiloga il numero di elementi selezionati e in genere offre **Contrassegna come Fisso**, **Ignora suggerimenti** e **Ottimizzazioni distribuzione**.

Fare clic su **Distribuisci ottimizzazioni**. In una finestra di dialogo **Distribuisci in Edge** sono elencati gli URL selezionati e i dettagli di ottimizzazione. Rivedi l&#39;elenco, quindi scegli **Distribuisci** o **Annulla**.

Dopo una distribuzione riuscita, **Distribuzione completata** conferma il numero di ottimizzazioni eseguite. Chiudi la finestra di dialogo e apri **Suggerimenti corretti** per verificare lo stato.

>[!NOTE]
>
>La distribuzione delle ottimizzazioni richiede il completamento del processo di onboarding Ottimizza in Edge. Se non hai ancora effettuato l&#39;onboarding, fai clic su **Distribuisci ottimizzazioni** per passare al processo di onboarding. Per informazioni complete sul funzionamento di Ottimizza in Edge, sui provider CDN supportati e sul processo di onboarding, visita la pagina [Ottimizza in Edge](/help/dashboards/optimize-at-edge/overview.md).

### Suggerimenti corretti e visualizzazione live

Su **suggerimenti corretti**, gli URL distribuiti mostrano **Ottimizzati** nella colonna dello stato. Espandere una riga per esaminare il sommario distribuito, utilizzare **Dettagli** per Analytics, se disponibile, oppure fare clic su **Visualizza Live** per aprire una visualizzazione di sola lettura del **contenuto della pagina corrente** utilizzato per la verifica (incluso il **Sommario** inserito).

Quando devi ripristinare le modifiche edge in blocco, seleziona le righe ottimizzate utilizzando le caselle di controllo, quindi utilizza **Rollback** nell&#39;intestazione.

## Rollback

Se cambi idea, puoi ripristinare un’ottimizzazione implementata. Dalla visualizzazione **Suggerimenti corretti**, seleziona le righe ottimizzate da ripristinare, quindi fai clic su **Rollback** nell&#39;intestazione.

Nella finestra di dialogo **Rollback** sono elencati i suggerimenti di cui verrà eseguito il rollback, con un breve avviso che informa che le ottimizzazioni distribuite verranno ripristinate. Confermare l&#39;elenco, quindi fare clic su **Rollback** o **Annulla**.

Al termine dell&#39;operazione verrà visualizzato un riepilogo di **Rollback completato**. Chiuderlo per tornare al dashboard.
