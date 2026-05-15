---
title: Errori di traffico agente
description: Scopri come LLM Optimizer rileva gli errori HTTP rilevati dagli agenti AI che scansionano il sito e come correggerli per migliorare l’accessibilità dei contenuti e la visibilità AI.
feature: Opportunities
autotag-review: '2026-05-15T17:32:31.900Z'
TQID: 'https://experienceleague.adobe.com/9Gbva-14SNt8A0G0B2Qu26OOp34L5NaM0z6lCv4yrTg'
product_v2:
  - id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2:
  - id: e0828736-236a-487b-a478-5a635455eadc
subfeature_v2:
  - id: e06fae5f-830b-4222-a469-b5e148d36465
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 7a92587197cf6a9eec6b01bd4eaeeaf1194d3088
workflow-type: tm+mt
source-wordcount: 1045
ht-degree: 0%

---


# Errori di traffico agente

Gli agenti di intelligenza artificiale che scansionano il sito riscontrano gli stessi errori HTTP dei browser umani, ma le conseguenze sono diverse. Quando un agente di intelligenza artificiale arriva a un errore 404, 403 o 5xx, non può accedere a tali contenuti o citarli, riducendo direttamente la visibilità del brand nelle risposte generate dall’intelligenza artificiale.

L’opportunità Errori di traffico agenti monitora i registri CDN per individuare eventuali errori HTTP restituiti agli agenti AI e fa emergere gli URL interessati insieme ai relativi volumi di hit e suggerimenti per la correzione. Vengono descritti tre tipi di errore, ognuno con le proprie opportunità nel dashboard:

- **404 Non trovato** — Collegamenti interrotti che impediscono agli agenti di IA di accedere a contenuto che non esiste più nell&#39;URL previsto.
- **403 Non consentito**: restrizioni di accesso che impediscono ai crawler di IA di accedere al contenuto che dovrebbero essere in grado di raggiungere.
- **5xx Errori server**: instabilità lato server che rende il contenuto temporaneamente o persistentemente non disponibile agli agenti di IA.

Ogni tipo di errore può apparire come un’opportunità separata nel dashboard a seconda degli errori rilevati per il sito.

Nell’opportunità vengono inoltre evidenziate due metriche chiave per ogni tipo di errore:

- **URL totali** — Numero di URL univoci che restituiscono errori agli agenti di IA.
- **Risultati totali** — Numero totale di risposte di errore registrate in tutte le richieste degli agenti di IA.

![Dashboard degli errori di traffico agente con metriche di riepilogo e dettagli degli errori](/help/dashboards/opportunities/assets/agentic-traffic-errors-overview.png)

## Come funziona

LLM Optimizer esegue una query sui registri CDN tramite Athena per identificare gli URL che restituiscono codici di stato 404, 403 o 5xx agli agenti di intelligenza artificiale. Gli agenti utente includono ChatGPT, Claude, Perplexity e Gemini. Vengono analizzati e classificati per volume di traffico fino a 500 URL per controllo di audit. Per impostazione predefinita, il controllo di audit viene eseguito settimanalmente.

Gli URL vengono convalidati prima di essere visualizzati per filtrare i falsi positivi e i dati non aggiornati. LLM Optimizer esegue un nuovo test di ogni URL per confermarne lo stato corrente e confronta le risposte dell’agente di intelligenza artificiale con le risposte del browser umano per identificare i problemi specifici del crawler.

Per **404 errori**, i suggerimenti sono basati su IA. Di conseguenza, LLM Optimizer analizza la struttura e il contenuto dell’URL danneggiato per consigliare URL alternativi che preservino le intenzioni dell’utente, insieme a un punteggio di affidabilità e una motivazione che spieghi il consiglio.

Per gli errori **403 e 5xx**, i suggerimenti sono basati su modelli e forniscono indicazioni mirate per ogni tipo di errore.

## Tabella dettagli errore

La tabella dei dettagli dell&#39;errore elenca tutti gli URL interessati, filtrati da **Agente utente**, **Codice paese** e **Categoria**. Per ogni URL viene visualizzato quanto segue:

- **URL** — La pagina interessata.
- **Totale** - Numero totale di riscontri di errore dagli agenti di IA.
- Il conteggio settimanale degli hit per le ultime settimane consente di verificare se il problema persiste o migliora.

![Tabella dei dettagli dell&#39;errore con filtri e colonne hit settimanali](/help/dashboards/opportunities/assets/agentic-traffic-errors-table.png)

## Dettagli dei suggerimenti

Facendo clic su un suggerimento si apre un pannello **Dettagli suggerimento** che mostra:

- L’URL interessato e l’azione consigliata, ad esempio &quot;Deve essere un URL valido o un reindirizzamento a un URL alternativo&quot;.
- Un grafico **Statistiche** che mostra il totale degli hit per settimana da parte dell&#39;agente utente dell&#39;agente di intelligenza artificiale, in modo da comprendere l&#39;impatto sul traffico e se il problema persiste o migliora.
- **Condividi** e **Elimina** azioni per gestire il suggerimento.

![Pannello Dettagli suggerimenti per un grafico con statistiche 404](/help/dashboards/opportunities/assets/agentic-traffic-errors-suggestion.png)

Per alcuni casi **5xx** (e simili), il pannello può notare quando non sono disponibili URL alternativi dello stesso dominio e spiegare come i consigli seguono le regole del dominio e dell&#39;elenco. Ad esempio, suggerendo all’URL del dominio di base di mantenere il valore SEO (Search Engine Optimization) quando non è possibile offrire una corrispondenza più stretta.

![Pannello Dettagli suggerimenti per un errore del server con messaggi esplicativi](/help/dashboards/opportunities/assets/agentic-traffic-errors-suggestion-503.png)

## Risoluzione

La correzione dipende dal tipo di errore:

**404 errori** — il suggerimento include uno o più URL alternativi consigliati da AI, in base alla struttura e al contenuto dell&#39;URL interrotto, oltre a un punteggio di affidabilità e a una motivazione. Implementa un reindirizzamento lato server dall’URL interrotto all’alternativa suggerita per ripristinare l’accesso agli agenti di intelligenza artificiale e preservare il reperimento dei contenuti.

**403 errori** — Rivedi le autorizzazioni di accesso per verificare che i crawler di IA non siano bloccati dal contenuto a cui dovrebbero poter accedere. In particolare:
- Autorizzazioni di accesso alla revisione - crawler di IA bloccato.
- Verificare che le impostazioni di protezione non blocchino i crawler legittimi.

**5xx errori**: verifica i problemi lato server che interessano le pagine contrassegnate. In particolare:
- Esamina la stabilità del server per le pagine a traffico elevato.
- Verificare la presenza di errori ricorrenti nei registri applicazioni.
- Monitorare lo stato e la capacità dell&#39;infrastruttura.

## Prova la demo

Visualizza l’opportunità Errori di traffico agente in azione utilizzando l’ambiente demo Frescopa.

- [Visualizza gli errori 404 nella demo Frescopa](https://play.llmo.now/org/demo-org/opportunities/agentic-traffic-4xxs)
- [Visualizza gli errori 5xx nella demo di Frescopa](https://play.llmo.now/org/demo-org/opportunities/agentic-traffic-5xxs)

## Domande frequenti

**Perché gli errori HTTP sono importanti per la visibilità AI?**

Nei sistemi con recupero ottimizzato, i crawler di intelligenza artificiale scoprono i collegamenti e tentano di recuperare il contenuto della pagina da includere nelle risposte. Se una pagina non è presente, restituisce un errore o è inaccessibile, non è possibile recuperarne o citarne il contenuto. La correzione diretta di questi errori tecnici migliora la probabilità che il contenuto venga indicizzato e citato correttamente dai sistemi di intelligenza artificiale.

**Qual è la differenza tra un errore 404 e un errore 403?**

Un errore 404 indica che la pagina non esiste nell’URL richiesto: è stata eliminata o spostata senza un reindirizzamento. Un errore 403 indica che la pagina esiste ma l’accesso viene negato, a tutti i crawler o in modo specifico agli agenti di intelligenza artificiale. Entrambi impediscono agli agenti di intelligenza artificiale di accedere al contenuto, ma la correzione è diversa per ciascuno di essi.

**Perché un errore 403 potrebbe interessare solo gli agenti di IA e non i visitatori umani?**

Alcune configurazioni di sicurezza o impostazioni di controllo degli accessi possono bloccare gli agenti utente dell’agente di intelligenza artificiale dal contenuto a cui i visitatori umani possono accedere normalmente. LLM Optimizer contrassegna specificamente questi casi confrontando le risposte dell’agente di intelligenza artificiale con le risposte del browser umano.

**In che modo i falsi positivi vengono esclusi?**

LLM Optimizer verifica nuovamente gli URL per confermarne lo stato corrente prima di visualizzarli come suggerimenti e confronta le risposte dell’agente di intelligenza artificiale con le risposte del browser umano per identificare i problemi specifici del crawler. Gli URL che non restituiscono più errori non vengono visualizzati.

**Con quale frequenza viene aggiornata l&#39;analisi?**

Il controllo di audit viene eseguito settimanalmente per impostazione predefinita, estraendo i dati di errore dai registri CDN della settimana precedente. La tabella dei dettagli dell’errore mostra i conteggi degli hit settimanali per poter tracciare le tendenze nel tempo.

**Quali agenti di IA sono monitorati?**

LLM Optimizer monitora le risposte di errore da tutti i pattern degli agenti utente degli agenti di intelligenza artificiale rilevati, inclusi: ChatGPT, Claude, Perplessità e crawler Gemini.
