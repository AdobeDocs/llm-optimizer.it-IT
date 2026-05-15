---
title: Aggiungi riepiloghi di trascrizioni multimediali
description: Scopri come LLM Optimizer identifica le pagine in cui le informazioni chiave sono incorporate nel video senza testo leggibile dal computer e come rivedere e distribuire i riepiloghi delle trascrizioni generati dall’intelligenza artificiale con l’opzione Ottimizza in Edge.
feature: Opportunities
autotag-review: '2026-05-15T17:28:28.569Z'
TQID: 'https://experienceleague.adobe.com/LiXMsMq6D08ciXR85aQBNDpmR5Csiv-5b9kv3lfTpDc'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: c0713b97-4af8-4c41-b742-5afcc6ced468
subfeature_v2: id: e1b649f0-0a61-46e4-9082-64d5cb2576c6
topic_v2: id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
source-git-commit: 7a92587197cf6a9eec6b01bd4eaeeaf1194d3088
workflow-type: tm+mt
source-wordcount: 775
ht-degree: 0%

---


# Aggiungi riepiloghi di trascrizioni multimediali

>[!NOTE]
>
> **Accesso anticipato** — Aggiungi riepiloghi di trascrizioni multimediali è disponibile in Accesso anticipato. La disponibilità, l’idoneità e parti del flusso di lavoro possono cambiare con la maturazione della funzionalità. Se hai domande sull’accesso, contatta il team del tuo account di Adobe.

L’opportunità Add Multimedia Transcript Summaries identifica le pagine in cui risiedono informazioni importanti in video o altri supporti senza trascrizioni o brevi riepiloghi testuali che gli agenti di intelligenza artificiale possono leggere. Introduce **riepiloghi di trascrizioni generati dall&#39;intelligenza artificiale** inseriti nel contesto dei contenuti multimediali e della pagina circostante. Consente di recuperare informazioni chiave sul marchio che altrimenti verrebbero perse rendendo i contenuti multimediali comprensibili agli agenti di intelligenza artificiale.

Per ogni URL interessato, puoi rivedere la **patch contenuto**, i dettagli **implementazione** proposti (ad esempio, il selettore CSS di destinazione e l&#39;operazione) e **razionale**, quindi distribuire con [Ottimizza in Edge](/help/dashboards/optimize-at-edge/overview.md) in modo che il traffico agente riceva il HTML arricchito senza la necessità di modifiche al sistema di gestione dei contenuti (CMS).

## Come risolve il problema

Le correzioni vengono applicate utilizzando [Ottimizza in Edge](/help/dashboards/optimize-at-edge/overview.md), che:

- Fornisce agli agenti di intelligenza artificiale uno snapshot HTML pre-renderizzato.
- Arricchisce la pagina con il testo di riepilogo delle trascrizioni nel HTML che recupera (ad esempio, vicino al video in linea pertinente).
- Funziona a livello CDN (nessuna modifica di CMS).
- È solo IA — nessun impatto sui visitatori umani o sui bot SEO (Search Engine Optimization).
- Distribuisce in pochi minuti ed è **completamente reversibile** dall&#39;interfaccia di LLM Optimizer.

## Come funziona

LLM Optimizer contrassegna le pagine a traffico elevato in cui manca testo leggibile al computer per i contenuti multimediali incorporati, in base alla configurazione e alla struttura della pagina. Gli URL interessati vengono visualizzati nella tabella **URL con suggerimenti** della scheda **Suggerimenti correnti**, in cui è possibile espandere una riga per esaminare ogni **patch di contenuto**, la relativa modalità di applicazione e il motivo per cui è consigliabile.

Per ogni pagina, sono disponibili:

**Riepilogo multimediale** - Riepiloghi strutturati derivati dal contenuto video.
**Anteprima** - Prima e dopo il confronto delle pagine.

![URL con suggerimenti sui suggerimenti correnti, riga espansa con patch di contenuto, dettagli di implementazione e motivazione](/help/dashboards/opportunities/assets/add-multimedia-transcript-summaries-expand.png)

Nella tabella **URL con suggerimenti** sono elencate le pagine in cui la trascrizione o il testo di riepilogo faciliterebbero l&#39;individuazione dell&#39;agente. I suggerimenti sono organizzati in **Suggerimenti correnti**, **Suggerimenti corretti** e **Suggerimenti ignorati**. Per ogni URL è possibile:

- **Espandere la riga** per visualizzare il testo **Patch contenuto**, i dettagli **Implementazione** (inclusa l&#39;operazione DOM pianificata e il selettore CSS) e **Motivo** della modifica.
- **Anteprima** del confronto prima e dopo per il traffico agente.
- **Contrassegna come fisso** se l&#39;opportunità è stata gestita al di fuori di LLM Optimizer.
- **Ignora** suggerimenti non rilevanti.

È possibile modificare il testo della patch dalla riga se supportato (controllo matita), quindi utilizzare le caselle di controllo riga per selezionare l’elemento da distribuire. Il piè di pagina mostra quanti sono selezionati e fornisce **Contrassegna come Fisso**, **Ignora suggerimenti** e **Distribuisci ottimizzazioni**.

### Distribuzione dell’ottimizzazione

Quando sei pronto per pubblicare al server Edge, fai clic su **Distribuisci ottimizzazioni**. In una finestra di dialogo **Distribuisci in Edge** sono elencati gli URL, i selettori e le operazioni che si stanno per eseguire. Rivedi l&#39;elenco, quindi scegli **Distribuisci** o **Annulla**.

![Finestra di dialogo Distribuisci su Edge per patch del contenuto di riepilogo delle trascrizioni multimediali](/help/dashboards/opportunities/assets/add-multimedia-transcript-summaries-deploy-dialog.png)

Dopo una distribuzione riuscita, **Distribuzione completata** conferma il numero di ottimizzazioni eseguite. Chiudi la finestra di dialogo e apri **Suggerimenti corretti** per verificare lo stato.

![Conferma completamento distribuzione](/help/dashboards/opportunities/assets/add-multimedia-transcript-summaries-deploy-confirm.png)

>[!NOTE]
>
> La distribuzione delle ottimizzazioni richiede il completamento del processo di onboarding Ottimizza in Edge. Se non hai ancora effettuato l&#39;onboarding, fai clic su **Distribuisci ottimizzazioni** per passare al processo di onboarding. Per informazioni complete sul funzionamento di Ottimizza in Edge, sui provider CDN supportati e sul processo di onboarding, visita la pagina [Ottimizza in Edge](/help/dashboards/optimize-at-edge/overview.md).

### Suggerimenti corretti e visualizzazione live

Su **suggerimenti corretti**, gli URL distribuiti mostrano **Ottimizzati** nella colonna dello stato. Espandi una riga per rivedere la **Patch di contenuti** attiva, i dettagli dell&#39;**Implementazione** e la **Motivazione**. Puoi inoltre utilizzare **Dettagli** per Analytics o **Visualizza Live**, se disponibile, per confermare il traffico agente ricevuto.

![Sono stati corretti suggerimenti con stato Ottimizzato, patch contenuto espanso e rollback](/help/dashboards/opportunities/assets/add-multimedia-transcript-summaries-fixed.png)

Per eseguire il rollback in blocco, seleziona le righe ottimizzate utilizzando le caselle di controllo, quindi utilizza **Rollback** nell&#39;intestazione.

![Sono stati corretti alcuni suggerimenti con righe selezionate prima del rollback](/help/dashboards/opportunities/assets/add-multimedia-transcript-summaries-select-in-fixed.png)

## Rollback

Se cambi idea, puoi ripristinare un’ottimizzazione implementata. Da **suggerimenti corretti**, selezionare le righe da ripristinare, quindi fare clic su **Rollback**.

Nella finestra di dialogo **Rollback** sono elencati i suggerimenti di cui verrà eseguito il rollback e viene visualizzato un avviso che informa che le ottimizzazioni distribuite verranno rimosse dal percorso live per il traffico agente. Conferma, quindi fai clic su **Rollback** o **Annulla**.

![Finestra di dialogo di ripristino contenente suggerimenti da ripristinare](/help/dashboards/opportunities/assets/add-multimedia-transcript-summaries-rollback-dialog.png)

Al termine dell&#39;operazione verrà visualizzato un riepilogo di **Rollback completato**. Chiuderlo per tornare al dashboard.

![Rollback completato. Rollback Completato](/help/dashboards/opportunities/assets/add-multimedia-transcript-summaries-rollback-confirm.png)

## Prova la demo

Esplora il flusso di lavoro Aggiungi riepiloghi di trascrizioni multimediali nella [demo Frescopa](https://play.llmo.now/org/demo-org).
