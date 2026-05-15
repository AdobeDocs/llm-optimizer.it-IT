---
title: Semplifica contenuti complessi
description: Scopri come LLM Optimizer identifica le pagine a traffico elevato con copia densa, difficile da interpretare per gli agenti AI, e come rivedere e distribuire il testo semplificato con Ottimizza in Edge.
feature: Opportunities
autotag-review: '2026-05-15T17:58:39.879Z'
TQID: 'https://experienceleague.adobe.com/wO3ZY-fEgOi7cD4dq0kCltk-YJSD431bkA6-9PW42Lo'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: c0713b97-4af8-4c41-b742-5afcc6ced468
subfeature_v2: id: e1b649f0-0a61-46e4-9082-64d5cb2576c6
topic_v2: id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
source-git-commit: 564171851fdccee43afd233da143d66182464889
workflow-type: tm+mt
source-wordcount: 785
ht-degree: 0%

---


# Semplifica contenuti complessi

L’opportunità Semplifica contenuti complessi identifica pagine a traffico elevato in cui testo denso o complesso che rende più difficile per gli agenti AI l’interpretazione delle informazioni chiave. Introduce versioni più chiare e facili da scansionare della copia esistente, mantenendo il significato originale. In questo modo gli agenti possono analizzare, riepilogare ed estrarre informazioni importanti in modo più affidabile.

Per ogni URL interessato, puoi rivedere **Testo migliorato** suggerimenti, confrontarli con **Anteprima**, quindi distribuirli con [Ottimizza in Edge](/help/dashboards/optimize-at-edge/overview.md) in modo che il traffico agente riceva HTML più chiaro senza la necessità di modifiche al sistema di gestione dei contenuti (CMS).

## Come risolve il problema

Le correzioni vengono applicate utilizzando [Ottimizza in Edge](/help/dashboards/optimize-at-edge/overview.md), che:

- Fornisce agli agenti di intelligenza artificiale uno snapshot HTML pre-renderizzato.
- Aggiorna la pagina visibile all&#39;agente in modo che i passaggi complessi vengano sostituiti o incrementati con **Testo migliorato** allineato alla pagina live.
- Funziona a livello CDN (nessuna modifica di CMS).
- È solo IA — nessun impatto sui visitatori umani o sui bot SEO (Search Engine Optimization).
- Distribuisce in pochi minuti ed è **completamente reversibile** dall&#39;interfaccia di LLM Optimizer.

## Come funziona

LLM Optimizer identifica le pagine che ricevono un traffico agente elevato e in cui i punteggi di contenuto sono inferiori alle soglie di leggibilità, quindi suggerisce di riscrivere la copia. Per ogni pagina sono disponibili:

**Testo migliorato** - contenuto semplificato basato su ciò che è già presente nella pagina.
**Anteprima** - un confronto prima e dopo per il traffico agente.

Gli URL interessati vengono visualizzati nella tabella **URL con suggerimenti** della scheda **Suggerimenti correnti**, in cui è possibile espandere una riga per esaminare ogni consiglio.

![URL con suggerimenti correnti, riga espansa con testo migliorato e anteprima](/help/dashboards/opportunities/assets/simplify-complex-content-expand.png)

Nella tabella **URL con suggerimenti** sono elencate le pagine in cui il contenuto semplificato facilita la comprensione da parte degli agenti. I suggerimenti sono organizzati in **Suggerimenti correnti**, **Suggerimenti corretti** e **Suggerimenti ignorati**. Per ogni URL è possibile:

- **Espandere la riga** per visualizzare **Testo migliorato** suggerimenti per la pagina.
- **Anteprima** del confronto prima e dopo per il traffico agente.
- **Contrassegna come fisso** se l&#39;opportunità è stata gestita al di fuori di LLM Optimizer.
- **Ignora** suggerimenti non rilevanti.

**Le visualizzazioni** includono **Suggerimenti correnti**, **Suggerimenti corretti** (stato **Ottimizzati** quando distribuiti) e **Suggerimenti ignorati**. Puoi verificare la distribuzione live utilizzando **Visualizza live** su **Suggerimenti corretti** e ripristinarla in qualsiasi momento.

Seleziona gli URL o gli elementi riga con **Testo migliorato** che desideri spedire utilizzando le caselle di controllo, quindi utilizza **Contrassegna come Fisso**, **Ignora suggerimenti** o **Distribuisci ottimizzazioni** nell&#39;intestazione **Piano opportunità**. L’interfaccia utente demo mostra anche un conteggio di selezioni e le azioni correlate con l’elenco.

![Piano opportunità, Suggerimenti correnti, riga espansa e Ottimizzazioni distribuzione nell&#39;intestazione piano](/help/dashboards/opportunities/assets/simplify-complex-content-select.png)

### Distribuzione dell’ottimizzazione

Quando sei pronto per pubblicare al server Edge, fai clic su **Distribuisci ottimizzazioni**. In una finestra di dialogo **Distribuisci in Edge** sono elencati gli URL selezionati e i dettagli di ottimizzazione. Rivedi l&#39;elenco, quindi scegli **Distribuisci** o **Annulla**.

![Finestra di dialogo Distribuisci in Edge](/help/dashboards/opportunities/assets/simplify-complex-content-deploy-dialog.png)

Dopo una distribuzione riuscita, **Distribuzione completata** conferma il numero di ottimizzazioni eseguite e rileva che gli agenti di intelligenza artificiale potrebbero impiegare del tempo per indicizzare l&#39;aggiornamento. Chiudi la finestra di dialogo e apri **Suggerimenti corretti** per verificare lo stato.

![Conferma completamento distribuzione](/help/dashboards/opportunities/assets/simplify-complex-content-deploy-confirm.png)

>[!NOTE]
>
>La distribuzione delle ottimizzazioni richiede il completamento del processo di onboarding Ottimizza in Edge. Se non hai ancora effettuato l&#39;onboarding, fai clic su **Distribuisci ottimizzazioni** per passare al processo di onboarding. Per informazioni complete sul funzionamento di Ottimizza in Edge, sui provider CDN supportati e sul processo di onboarding, visita la pagina [Ottimizza in Edge](/help/dashboards/optimize-at-edge/overview.md).

### Suggerimenti corretti e visualizzazione live

Su **suggerimenti corretti**, gli URL distribuiti mostrano **Ottimizzati** nella colonna dello stato. Espandere una riga per rivedere **Testo migliorato** distribuito e istruzioni.

![Scheda Suggerimenti corretti con stato Ottimizzato, copia semplificata espansa, Visualizza in tempo reale e Dettagli](/help/dashboards/opportunities/assets/simplify-complex-content-fixed.png)

Fai clic su **Visualizza Live** nella riga per aprire una visualizzazione di sola lettura del **contenuto della pagina corrente**, utilizzato per la verifica (inclusi i passaggi semplificati, se applicati). Utilizza **Dettagli** per Analytics.

![Visualizza in tempo reale: contenuto della pagina corrente incluso testo semplificato per gli agenti](/help/dashboards/opportunities/assets/simplify-complex-content-view-live.png)

Quando devi ripristinare le modifiche edge in blocco, seleziona le righe ottimizzate utilizzando le caselle di controllo, quindi utilizza **Rollback** nell&#39;intestazione.

![Sono stati corretti alcuni suggerimenti con la riga distribuita espansa, lo stato Ottimizzato e il rollback nell&#39;intestazione](/help/dashboards/opportunities/assets/simplify-complex-content-rollback.png)

## Rollback

Se cambi idea, puoi ripristinare qualsiasi ottimizzazione implementata. Dalla visualizzazione **Suggerimenti corretti**, seleziona le righe ottimizzate da ripristinare, quindi fai clic su **Rollback** nell&#39;intestazione.

Nella finestra di dialogo **Rollback** sono elencati i suggerimenti di cui verrà eseguito il rollback, con un breve avviso che informa che le ottimizzazioni distribuite verranno ripristinate. Confermare l&#39;elenco, quindi fare clic su **Rollback** o **Annulla**.

![Finestra di dialogo di ripristino contenente suggerimenti da ripristinare](/help/dashboards/opportunities/assets/simplify-complex-content-rollback-dialog.png)

Al termine dell&#39;operazione verrà visualizzato un riepilogo di **Rollback completato**. Chiuderlo per tornare al dashboard.

![Rollback completato. Rollback Completato](/help/dashboards/opportunities/assets/simplify-complex-content-rollback-confirm.png)

## Prova la demo

Esplora il flusso di lavoro Semplifica contenuti complessi nella [demo Frescopa](https://play.llmo.now/org/demo-org).
