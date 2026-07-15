---
title: Aggiungi domande frequenti pertinenti
description: Scopri come LLM Optimizer identifica le pagine a traffico elevato prive di contenuti Q&A strutturati per gli agenti AI e come rivedere e distribuire le domande frequenti generate dall’intelligenza artificiale con Optimize at Edge.
feature: Opportunities
autotag-review: '2026-07-15T16:47:24.291Z'
TQID: 'https://experienceleague.adobe.com/ObmJKEvR9-ovzugCtAsRkcUBemcsMw6cNwizkuKYPcc'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: e1b649f0-0a61-46e4-9082-64d5cb2576c6id: ef4e63f5-cb4d-462d-bf9a-1f617edf2a3a
subfeature_v2: id: bbfc1b77-44c5-4fe8-b65f-ec160fe0d021
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1id: e1e0219c-f879-479f-8427-888ed2a6e9c2
source-git-commit: 2705cf26faea9c09817bbdcec4b4c531552df7ba
workflow-type: tm+mt
source-wordcount: 742
ht-degree: 10%

---


# Aggiungi domande frequenti pertinenti

L’opportunità di aggiunta di domande frequenti rilevanti identifica pagine con traffico elevato prive di contenuti Q&amp;A strutturati su cui gli agenti di IA spesso si basano per generare le risposte. Presenta contenuti rilevanti, **domande frequenti allineate alle finalità**, basati sul materiale della pagina esistente. Questo consente agli agenti di abbinare più direttamente le domande degli utenti al contenuto.

Per ogni URL interessato, puoi rivedere i suggerimenti delle domande frequenti generate dall&#39;intelligenza artificiale, quindi distribuirli con [Ottimizza in Edge](/help/dashboards/optimize-at-edge/overview.md) in modo che il traffico agente riceva un contesto di domande e risposte più chiaro senza la necessità di apportare modifiche al sistema di gestione dei contenuti (CMS).

## Come risolve il problema

Le correzioni vengono applicate utilizzando [Ottimizza in Edge](/help/dashboards/optimize-at-edge/overview.md), che:

- Fornisce agli agenti di intelligenza artificiale uno snapshot HTML pre-renderizzato.
- Arricchisce la pagina con il contenuto delle domande frequenti nel HTML che recupera.
- Funziona a livello CDN (nessuna modifica di CMS).
- È solo IA: nessun impatto sui visitatori umani o sui bot SEO (Search Engine Optimization).
- Distribuisce in pochi minuti ed è **completamente reversibile** dall&#39;interfaccia di LLM Optimizer.

## Come funziona

LLM Optimizer identifica le pagine con traffico elevato in cui il contenuto delle domande e risposte è assente o sottile, in base al set di prompt del tuo marchio. Gli URL interessati vengono visualizzati nella tabella **URL con suggerimenti** della scheda **Suggerimenti correnti**, in cui è possibile espandere una riga per esaminare ogni consiglio.

![URL con suggerimenti correnti, riga espansa con richieste di domande frequenti e risposte generate da IA](/help/dashboards/opportunities/assets/add-relevant-faqs-expand.png)

Nella tabella **URL con suggerimenti** sono elencate le pagine in cui le domande frequenti facilitano l&#39;individuazione basata su IA. I suggerimenti sono organizzati in **Suggerimenti correnti**, **Suggerimenti corretti** e **Suggerimenti ignorati**. Per ciascun URL puoi:

- **Espandere la riga** per visualizzare il contenuto delle domande frequenti proposte per la pagina.
- **Anteprima** del confronto prima e dopo per il traffico agente.
- **Contrassegna come fisso** se l&#39;opportunità è stata gestita al di fuori di LLM Optimizer.
- **Ignorare** i suggerimenti non pertinenti.

Ogni voce espansa elenca le domande frequenti **prompt**, **risposte suggerite generate da IA**, brevi **ragionamenti** e **origini** associate alla pagina. La tabella mostra anche quante domande frequenti vengono suggerite per URL e **Traffico agente (4 settimane)** per aiutarti a definire le priorità.

Fai clic su **Anteprima** su una riga per aprire l&#39;anteprima di ottimizzazione. Viene confrontato il modo in cui la pagina cerca ora il traffico agente con la vista di post-ottimizzazione (ad esempio, il nuovo blocco **FAQs**).

![Anteprima delle ottimizzazioni confrontando la visualizzazione dell&#39;agente corrente con quella dell&#39;agente di post-ottimizzazione con le domande frequenti](/help/dashboards/opportunities/assets/add-relevant-faqs-ui-01.png)

Seleziona le domande frequenti che desideri spedire utilizzando le caselle di controllo delle righe. Il piè di pagina mostra quanti sono selezionati e fornisce **Contrassegna come Fisso**, **Ignora suggerimenti** e **Distribuisci ottimizzazioni**.

![Domande frequenti selezionate sui suggerimenti correnti con ottimizzazioni di distribuzione](/help/dashboards/opportunities/assets/add-relevant-faqs-ui-02.png)

### Implementazione dell’ottimizzazione

Quando sei pronto per pubblicare al server Edge, fai clic su **Distribuisci ottimizzazioni**. In una finestra di dialogo **Distribuisci in Edge** sono elencati gli URL, le domande e le risposte che stai per inviare. Rivedi l&#39;elenco, quindi scegli **Distribuisci** o **Annulla**.

![Finestra di dialogo Ottimizza su Edge](/help/dashboards/opportunities/assets/add-relevant-faqs-ui-03.png)

Dopo una distribuzione riuscita, **Distribuzione completata** conferma il numero di ottimizzazioni eseguite. Chiudi la finestra di dialogo e apri **Suggerimenti corretti** per verificare lo stato.

![Conferma completamento distribuzione](/help/dashboards/opportunities/assets/add-relevant-faqs-ui-04.png)

>[!NOTE]
>
>L’implementazione delle ottimizzazioni richiede il completamento del processo di onboarding Ottimizza su Edge. Se non hai ancora effettuato l’onboarding, facendo clic su **Implementa ottimizzazioni** ti consentirà di passare al processo di onboarding. Per informazioni complete sul funzionamento di Ottimizza su Edge, sui provider CDN supportati e sul processo di onboarding, consulta la pagina [Ottimizza su Edge](/help/dashboards/optimize-at-edge/overview.md).

### Suggerimenti corretti e visualizzazione live

Su **suggerimenti corretti**, gli URL distribuiti mostrano **Ottimizzati** nella colonna dello stato. Espandi una riga per rivedere il contenuto delle domande frequenti live, utilizza **Dettagli** per Analytics oppure fai clic su **Visualizza Live** per aprire una visualizzazione di sola lettura del **contenuto della pagina corrente**, utilizzato per la verifica (inclusa la sezione **Domande frequenti** inserita).

![Sono stati corretti alcuni suggerimenti con stato Ottimizzato, Visualizza Live e Rollback](/help/dashboards/opportunities/assets/add-relevant-faqs-fixed.png)

La finestra **Visualizza Live** mostra la struttura della pagina e la copia delle domande frequenti presentate in tale verifica.

![Visualizza in tempo reale: contenuto della pagina corrente, incluse le domande frequenti](/help/dashboards/opportunities/assets/add-relevant-faqs-ui-05.png)

## Rollback

Se cambi idea, puoi ripristinare qualsiasi ottimizzazione implementata. Dalla visualizzazione **Suggerimenti corretti**, è possibile selezionare le righe ottimizzate da ripristinare, quindi fare clic su **Rollback** nell&#39;intestazione.

Nella finestra di dialogo **Rollback** sono elencati i suggerimenti di cui verrà eseguito il rollback, con un breve avviso che informa che le ottimizzazioni distribuite verranno ripristinate. Confermare l&#39;elenco, quindi fare clic su **Rollback** o **Annulla**.

![Finestra di dialogo di ripristino contenente suggerimenti da ripristinare](/help/dashboards/opportunities/assets/add-relevant-faqs-ui-07.png)

Al termine dell&#39;operazione verrà visualizzato un riepilogo di **Rollback completato**. Chiuderlo per tornare al dashboard.

![Rollback completato. Rollback Completato](/help/dashboards/opportunities/assets/add-relevant-faqs-ui-08.png)

## Prova nella demo

Esplora il flusso di lavoro Aggiungi domande frequenti pertinenti nella [demo Frescopa](https://play.llmo.now/org/demo-org).
