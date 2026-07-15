---
title: Semplifica contenuti complessi
description: Scopri come LLM Optimizer identifica le pagine a traffico elevato con copia densa, difficile da interpretare per gli agenti AI, e come rivedere e distribuire il testo semplificato con Ottimizza in Edge.
feature: Opportunities
autotag-review: '2026-07-15T18:04:55.581Z'
TQID: 'https://experienceleague.adobe.com/uMK9qeAGMNrtvR0TYbeg8SIOKlwKf4L5NIE9ZgsJaUw'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: e1b649f0-0a61-46e4-9082-64d5cb2576c6id: ef4e63f5-cb4d-462d-bf9a-1f617edf2a3a
subfeature_v2: id: bbfc1b77-44c5-4fe8-b65f-ec160fe0d021
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1id: e1e0219c-f879-479f-8427-888ed2a6e9c2
source-git-commit: 2705cf26faea9c09817bbdcec4b4c531552df7ba
workflow-type: tm+mt
source-wordcount: 785
ht-degree: 10%

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

Nella tabella **URL con suggerimenti** sono elencate le pagine in cui il contenuto semplificato facilita la comprensione da parte degli agenti. I suggerimenti sono organizzati in **Suggerimenti correnti**, **Suggerimenti corretti** e **Suggerimenti ignorati**. Per ciascun URL puoi:

- **Espandere la riga** per visualizzare **Testo migliorato** suggerimenti per la pagina.
- **Anteprima** del confronto prima e dopo per il traffico agente.
- **Contrassegna come fisso** se l&#39;opportunità è stata gestita al di fuori di LLM Optimizer.
- **Ignorare** i suggerimenti non pertinenti.

**Le visualizzazioni** includono **Suggerimenti correnti**, **Suggerimenti corretti** (stato **Ottimizzati** quando distribuiti) e **Suggerimenti ignorati**. Puoi verificare la distribuzione live utilizzando **Visualizza live** su **Suggerimenti corretti** e ripristinarla in qualsiasi momento.

Seleziona gli URL o gli elementi riga con **Testo migliorato** che desideri spedire utilizzando le caselle di controllo, quindi utilizza **Contrassegna come Fisso**, **Ignora suggerimenti** o **Distribuisci ottimizzazioni** nell&#39;intestazione **Piano opportunità**. L’interfaccia utente demo mostra anche un conteggio di selezioni e le azioni correlate con l’elenco.

![Piano opportunità, Suggerimenti correnti, riga espansa e Ottimizzazioni distribuzione nell&#39;intestazione piano](/help/dashboards/opportunities/assets/simplify-complex-content-select.png)

### Implementazione dell’ottimizzazione

Quando sei pronto per pubblicare al server Edge, fai clic su **Distribuisci ottimizzazioni**. In una finestra di dialogo **Distribuisci in Edge** sono elencati gli URL selezionati e i dettagli di ottimizzazione. Rivedi l&#39;elenco, quindi scegli **Distribuisci** o **Annulla**.

![Finestra di dialogo Ottimizza su Edge](/help/dashboards/opportunities/assets/simplify-complex-content-deploy-dialog.png)

Dopo una distribuzione riuscita, **Distribuzione completata** conferma il numero di ottimizzazioni eseguite e rileva che gli agenti di intelligenza artificiale potrebbero impiegare del tempo per indicizzare l&#39;aggiornamento. Chiudi la finestra di dialogo e apri **Suggerimenti corretti** per verificare lo stato.

![Conferma completamento distribuzione](/help/dashboards/opportunities/assets/simplify-complex-content-deploy-confirm.png)

>[!NOTE]
>
>L’implementazione delle ottimizzazioni richiede il completamento del processo di onboarding Ottimizza su Edge. Se non hai ancora effettuato l’onboarding, facendo clic su **Implementa ottimizzazioni** ti consentirà di passare al processo di onboarding. Per informazioni complete sul funzionamento di Ottimizza su Edge, sui provider CDN supportati e sul processo di onboarding, consulta la pagina [Ottimizza su Edge](/help/dashboards/optimize-at-edge/overview.md).

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

## Prova nella demo

Esplora il flusso di lavoro Semplifica contenuti complessi nella [demo Frescopa](https://play.llmo.now/org/demo-org).
