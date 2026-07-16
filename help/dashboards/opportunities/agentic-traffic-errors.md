---
title: Errori relativi al traffico da IA agentica
description: Scopri come LLM Optimizer rileva gli errori HTTP riscontrati dagli agenti IA durante la scansione del tuo sito e come correggerli per migliorare l’accessibilità ai contenuti e la loro visibilità per l’IA.
feature: Opportunities
autotag-review: '2026-07-15T17:28:13.287Z'
TQID: 'https://experienceleague.adobe.com/PWMllnv-p7VBlmv6bZ8jUQtLPSGW3jMH3RuikgyRKKw'
product_v2:
  - id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2:
  - id: e0828736-236a-487b-a478-5a635455eadc
  - id: e1b649f0-0a61-46e4-9082-64d5cb2576c6
subfeature_v2:
  - id: e06fae5f-830b-4222-a469-b5e148d36465
  - id: e0ec491f-fe51-42b6-801c-1c0dfcc0e64f
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: cc72dcf1-72e1-48cc-b434-e7c27d62d67c
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 2705cf26faea9c09817bbdcec4b4c531552df7ba
workflow-type: tm+mt
source-wordcount: 1045
ht-degree: 100%

---


# Errori relativi al traffico da IA agentica

Gli agenti IA che eseguono la scansione del tuo sito riscontrano gli stessi errori HTTP dei browser utilizzati dagli utenti, ma con conseguenze diverse. Quando un agente IA riscontra un errore 404, 403 o 5xx, non può accedere ai contenuti né citarli, e questo riduce direttamente la visibilità del tuo brand nelle risposte generate dall’IA.

L’opportunità Errori relativi al traffico da IA agentica monitora i tuoi registri CDN alla ricerca di errori HTTP restituiti agli agenti IA e fa emergere gli URL interessati, insieme al volume di hit e a suggerimenti di correzione. Tratta tre tipologie di errori, ognuna con la propria opportunità nella dashboard:

- **404 - Non trovato**: collegamenti interrotti che impediscono agli agenti IA di accedere ai contenuti che non si trovano più all’URL previsto.
- **403 - Non consentito**: restrizioni di accesso a causa delle quali i crawler IA non possono accedere a contenuti che dovrebbero essere in grado di trovare.
- **Errori del server 5xx**: instabilità lato server che rende non disponibili i contenuti agli agenti IA, in modo temporaneo o permanente.

In funzione degli errori rilevati per il tuo sito, nella dashboard ciascun tipo di errore può apparire come un’opportunità distinta.

L’opportunità mette inoltre in evidenza due metriche chiave per ciascun tipo di errore:

- **URL totali**: numero di URL univoci che restituiscono errori agli agenti IA.
- **Hit totali**: numero totale di risposte di errore registrate in tutte le richieste dell’agente IA.

![Dashboard degli errori del traffico da IA agentica che mostra metriche di riepilogo e dettagli degli errori](/help/dashboards/opportunities/assets/agentic-traffic-errors-overview.png)

## Come funziona

LLM Optimizer interroga i tuoi registri CDN tramite Athena per identificare gli URL che restituiscono codici di stato 404, 403 o 5xx agli user agent dell’agente IA. Tra gli user agent figurano ChatGPT, Claude, Perplexity e Gemini. Per ogni audit vengono analizzati fino a 500 URL, classificati in base al volume di traffico. L’audit viene eseguito settimanalmente per impostazione predefinita.

Gli URL sono convalidati prima di essere messi in evidenza al fine di filtrare falsi positivi e dati obsoleti. LLM Optimizer verifica di nuovo gli URL per confermarne lo stato attuale e confronta le risposte dell’agente IA con le risposte dei browser umani per identificare problemi specifici del crawler.

Per gli **errori 404**, i suggerimenti sono basati sull’IA. Pertanto, LLM Optimizer analizza la struttura e il contenuto dell’URL danneggiato per consigliare URL alternativi che preservino le intenzioni dell’utente, insieme a un punteggio di affidabilità e a una motivazione che spiega il consiglio.

Per gli **errori 403 e 5xx**, i suggerimenti sono basati su modelli e forniscono indicazioni mirate per ciascun tipo di errore.

## Tabella dei dettagli dell’errore

La tabella dei dettagli dell’errore elenca tutti gli URL interessati, filtrati per **User Agent**,**Codice paese** e **Categoria**. Per ciascun URL riporta:

- **URL**: la pagina interessata.
- **Totale**: numero totale di hit di errore dagli agenti IA.
- I conteggi settimanali degli hit delle ultime settimane, affinché tu possa monitorare se il problema persiste o migliora.

![Tabella dei dettagli dell’errore con filtri e colonne degli hit settimanali](/help/dashboards/opportunities/assets/agentic-traffic-errors-table.png)

## Dettagli dei suggerimenti

Facendo clic su qualsiasi suggerimento si apre un pannello **Dettagli suggerimento** che riporta:

- L’URL interessato e l’azione consigliata, ad esempio “Deve essere un URL valido o reindirizzare a un URL alternativo”.
- Un grafico **Statistiche** con il totale di hit per settimana da parte dell’user agent dell’agente IA, affinché tu possa capire l’impatto sul traffico e se il problema persiste o migliora.
- Le azioni **Condividi** e **Ignora** per gestire il suggerimento.

![Pannello dei Dettagli suggerimenti di un grafico dell’errore 404 con statistiche](/help/dashboards/opportunities/assets/agentic-traffic-errors-suggestion.png)

In alcuni casi **5xx** (e simili), il pannello può rilevare quando non sono disponibili URL alternativi dello stesso dominio e spiegare in che modo i consigli seguono le regole del dominio e dell’elenco, suggerendo per esempio all’URL del dominio di base di mantenere il valore SEO quando non è possibile offrire una corrispondenza più stretta.

![Pannello dei Dettagli suggerimenti per un errore del server con messaggi esplicativi](/help/dashboards/opportunities/assets/agentic-traffic-errors-suggestion-503.png)

## Risoluzione

La correzione dipende dal tipo di errore:

**Errori 404**: il suggerimento include uno o più URL alternativi consigliati dall’AI, in base alla struttura e al contenuto dell’URL danneggiato, oltre a un punteggio di affidabilità e a una motivazione. Implementa un reindirizzamento lato server dall’URL danneggiato all’alternativa suggerita, per ripristinare l’accesso agli agenti IA e mantenere la reperibilità dei contenuti.

**Errori 403**: rivedere le autorizzazioni di accesso per verificare che per i crawler IA non siano bloccati contenuti a cui dovrebbero essere in grado di accedere. In particolare:
- Rivedere le autorizzazioni di accesso: crawler IA bloccato.
- Verificare che le impostazioni di sicurezza non blocchino i crawler legittimi.

**Errori 5xx**: esaminare i problemi lato server che interessano le pagine segnalate. In particolare:
- Esaminare la stabilità del server per le pagine con traffico elevato.
- Controllare la presenza di errori ricorrenti nei registri dell’applicazione.
- Monitorare lo stato e la capacità dell’infrastruttura.

## Prova nella demo

Guarda in azione l’opportunità Errori di traffico da IA agentica utilizzando l’ambiente demo di Frescopa.

- [Visualizza gli errori 404 nella demo di Frescopa](https://play.llmo.now/org/demo-org/opportunities/agentic-traffic-4xxs)
- [Visualizza gli errori 5xx nella demo di Frescopa](https://play.llmo.now/org/demo-org/opportunities/agentic-traffic-5xxs)

## Domande frequenti

**Perché gli errori HTTP sono importanti per la visibilità IA?**

Nei sistemi retrieval-augmented, i crawler IA individuano i collegamenti e tentano di recuperare il contenuto della pagina da includere nelle risposte. Se una pagina non è presente, restituisce un errore o è inaccessibile, non è possibile recuperarne o citarne il contenuto. La correzione diretta di questi errori tecnici migliora la probabilità che il tuo contenuto venga indicizzato e citato correttamente dai sistemi IA.

**Qual è la differenza tra un errore 404 e un errore 403?**

Un errore 404 indica che la pagina non esiste nell’URL richiesto: è stata eliminata o spostata senza un reindirizzamento. Un errore 403 indica che la pagina esiste ma l’accesso viene negato a tutti i crawler o in modo specifico agli agenti IA. Entrambi impediscono agli agenti IA di accedere al tuo contenuto, ma la correzione è diversa per ciascuno di essi.

**Perché un errore 403 potrebbe interessare solo gli agenti IA e non i visitatori umani?**

Alcune configurazioni di sicurezza o impostazioni di controllo degli accessi possono bloccare per gli user agent dell’agente IA contenuti a cui i visitatori umani possono accedere normalmente. LLM Optimizer contrassegna in modo specifico questi casi confrontando le risposte dell’agente IA con le risposte del browser umano.

**Come vengono esclusi i falsi positivi?**

LLM Optimizer verifica di nuovo gli URL per confermarne lo stato attuale prima di metterli in evidenza come suggerimenti e confronta le risposte dell’agente IA con le risposte dei browser umani per identificare problemi specifici del crawler. Gli URL che non restituiscono più errori non vengono visualizzati.

**Con quale frequenza viene aggiornata l’analisi?**

Il controllo di audit viene eseguito settimanalmente per impostazione predefinita, estraendo i dati di errore dai registri CDN della settimana precedente. La tabella dei dettagli dell’errore mostra i conteggi degli hit settimanali per poter monitorare le tendenze nel tempo.

**Quali agenti IA sono monitorati?**

LLM Optimizer monitora le risposte di errore di tutti i pattern degli user agent degli agenti IA rilevati, compresi: crawler ChatGPT, Claude, Perplexity e Gemini.
