---
title: Aggiungi riepiloghi compatibili con LLM
description: Scopri come LLM Optimizer identifica le pagine a traffico elevato prive di riepiloghi concisi e punti chiave per gli agenti di intelligenza artificiale, e come rivederle e distribuirle con Optimize at Edge.
feature: Opportunities
autotag-review: '2026-05-15T17:27:51.631Z'
TQID: 'https://experienceleague.adobe.com/QpBdx3B-qg41ZWtPU2R4CNq-POrSs31UIb0kms1H3GU'
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
source-wordcount: 793
ht-degree: 0%

---


# Aggiungi riepiloghi compatibili con LLM

L’opportunità Add LLM-friendly Summaries identifica le pagine a traffico elevato prive di riepiloghi strutturati concisi, rendendo più difficile per gli agenti AI comprendere rapidamente le informazioni chiave sulla pagina. Presenta riepiloghi chiari e punti chiave basati sul contenuto della pagina esistente. Questo consente agli agenti di interpretare e acquisire in modo più efficiente importanti brand claim e aumenta la probabilità che il contenuto venga incluso in modo accurato nelle risposte AI.

Per ogni URL interessato, puoi rivedere i suggerimenti generati dall&#39;intelligenza artificiale, quindi distribuirli con [Ottimizza in Edge](/help/dashboards/optimize-at-edge/overview.md) in modo che il traffico agente diventi più chiaro e analizzabile in un contesto in cui non sono necessarie modifiche al sistema di gestione dei contenuti (CMS).

## Come risolve il problema

Le correzioni vengono applicate utilizzando [Ottimizza in Edge](/help/dashboards/optimize-at-edge/overview.md), che:

- Fornisce agli agenti di intelligenza artificiale uno snapshot HTML pre-renderizzato.
- Arricchisce la pagina con riepiloghi e/o punti chiave nel HTML che recupera.
- Funziona a livello CDN (nessuna modifica di CMS).
- È solo IA — nessun impatto sui visitatori umani o sui bot SEO (Search Engine Optimization).
- Distribuisce in pochi minuti ed è **completamente reversibile** dall&#39;interfaccia di LLM Optimizer.

## Come funziona

LLM Optimizer identifica le pagine a traffico elevato in cui i **riepiloghi** e i **punti chiave** a livello di pagina o di sezione aiutano la comprensione IA. Gli URL interessati vengono visualizzati nella tabella **URL con suggerimenti** della scheda **Suggerimenti correnti**, in cui è possibile espandere una riga per esaminare ogni consiglio.

![URL con suggerimenti correnti, riga espansa con suggerimenti di riepilogo pagine e sezioni](/help/dashboards/opportunities/assets/add-llm-friendly-summaries-expand.png)

Nella tabella **URL con suggerimenti** sono elencate le pagine in cui i riepiloghi potrebbero facilitare l&#39;individuazione degli agenti. I suggerimenti sono organizzati in **Suggerimenti correnti**, **Suggerimenti corretti** e **Suggerimenti ignorati**. Per ogni URL è possibile:

- **Espandere la riga** per visualizzare l&#39;analisi e il testo di riepilogo proposto (e i punti chiave se inclusi).
- **Anteprima** del confronto prima e dopo per il traffico agente.
- **Contrassegna come fisso** se l&#39;opportunità è stata gestita al di fuori di LLM Optimizer.
- **Ignora** suggerimenti non rilevanti.

Ogni voce espansa mostra istruzioni di riepilogo a livello di pagina e di sezione, **copia generata da IA**, controlli di modifica e contesto associati alla pagina live.

Fai clic su **Anteprima** nella colonna **Azioni** per aprire l&#39;anteprima di ottimizzazione. Viene confrontato il modo in cui la pagina cerca ora il traffico agente con la vista di post-ottimizzazione (ad esempio, sono stati inseriti **riepilogo** e **contenuto punto chiave** allineati ai posizionamenti suggeriti). Puoi aprire o chiudere l’anteprima in qualsiasi momento prima di distribuire.

Quando sei pronto per la pubblicazione, seleziona le voci di riepilogo e dei punti chiave utilizzando le caselle di controllo. Il piè di pagina mostra quanti sono selezionati e fornisce **Contrassegna come Fisso**, **Ignora suggerimenti** e **Distribuisci ottimizzazioni**.

![Suggerimenti correnti con elementi di riga di riepilogo selezionati e distribuire ottimizzazioni nel piè di pagina](/help/dashboards/opportunities/assets/add-llm-friendly-summaries-select-url.png)

### Distribuzione dell’ottimizzazione

Quando sei pronto per pubblicare al server Edge, fai clic su **Distribuisci ottimizzazioni**. In una finestra di dialogo **Distribuisci in Edge** sono elencati gli URL selezionati e i dettagli di ottimizzazione. Rivedi l&#39;elenco, quindi scegli **Distribuisci** o **Annulla**.

![Finestra di dialogo Distribuisci in Edge](/help/dashboards/opportunities/assets/add-llm-friendly-summaries-deploy-dialog.png)

Dopo una distribuzione riuscita, **Distribuzione completata** conferma il numero di ottimizzazioni eseguite e rileva che gli agenti di intelligenza artificiale potrebbero impiegare del tempo per indicizzare l&#39;aggiornamento. Chiudi la finestra di dialogo e apri **Suggerimenti corretti** per verificare lo stato.

![Conferma completamento distribuzione](/help/dashboards/opportunities/assets/add-llm-friendly-summaries-deploy-confirm.png)

>[!NOTE]
>
>La distribuzione delle ottimizzazioni richiede il completamento del processo di onboarding Ottimizza in Edge. Se non hai ancora effettuato l&#39;onboarding, fai clic su **Distribuisci ottimizzazioni** per passare al processo di onboarding. Per informazioni complete sul funzionamento di Ottimizza in Edge, sui provider CDN supportati e sul processo di onboarding, visita la pagina [Ottimizza in Edge](/help/dashboards/optimize-at-edge/overview.md).

### Suggerimenti corretti e visualizzazione live

Su **suggerimenti corretti**, gli URL distribuiti mostrano **Ottimizzati** nella colonna dello stato. Espandere una riga per esaminare la copia di riepilogo distribuita e le istruzioni.

![Scheda Suggerimenti corretti con stato Ottimizzato, riepiloghi distribuiti espansi, Visualizza in tempo reale e Dettagli](/help/dashboards/opportunities/assets/add-llm-friendly-summaries-fixed.png)

Fai clic su **Visualizza Live** nella riga per aprire una visualizzazione di sola lettura del **contenuto della pagina corrente** utilizzato per la verifica (inclusi **summary** e **blocchi del punto chiave** inseriti, se applicati). Utilizza **Dettagli** per Analytics. Quando devi ripristinare le modifiche edge in blocco, seleziona le righe ottimizzate utilizzando le caselle di controllo, quindi utilizza **Rollback** nell&#39;intestazione.

![Suggerimenti corretti con caselle di controllo per la selezione in blocco prima del rollback](/help/dashboards/opportunities/assets/add-llm-friendly-summaries-select-in-fixed.png)

## Rollback

Se cambi idea, puoi ripristinare qualsiasi ottimizzazione implementata. Dalla visualizzazione **Suggerimenti corretti**, seleziona le righe ottimizzate da ripristinare, quindi fai clic su **Rollback** nell&#39;intestazione.

Nella finestra di dialogo **Rollback** sono elencati i suggerimenti di cui verrà eseguito il rollback, con un breve avviso che informa che le ottimizzazioni distribuite verranno ripristinate. Confermare l&#39;elenco, quindi fare clic su **Rollback** o **Annulla**.

![Finestra di dialogo di ripristino contenente suggerimenti da ripristinare](/help/dashboards/opportunities/assets/add-llm-friendly-summaries-rollback-dialog.png)

Al termine dell&#39;operazione verrà visualizzato un riepilogo di **Rollback completato**. Chiuderlo per tornare al dashboard.

![Rollback completato. Rollback Completato](/help/dashboards/opportunities/assets/add-llm-friendly-summaries-rollback-confirm.png)

## Prova la demo

Esplora il flusso di lavoro Aggiungi riepiloghi compatibili con LLM nella [demo Frescopa](https://play.llmo.now/org/demo-org).
