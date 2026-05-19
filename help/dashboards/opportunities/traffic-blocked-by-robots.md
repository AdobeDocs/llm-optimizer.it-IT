---
title: Traffico bloccato da robots.txt
description: Scopri come LLM Optimizer rileva quando il file robots.txt impedisce agli agenti IA di accedere ai tuoi contenuti, e come correggerlo.
feature: Opportunities
autotag-review: '2026-05-15T18:00:25.453Z'
TQID: 'https://experienceleague.adobe.com/9LGbxeIbWYZp-MN5Zww6g-dQ6BZT0IWzlA7XB-2Xlho'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: d1956731-2adb-4bb7-8301-2b239254ac72id: c0713b97-4af8-4c41-b742-5afcc6ced468
subfeature_v2: id: e1b649f0-0a61-46e4-9082-64d5cb2576c6
topic_v2: id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 564171851fdccee43afd233da143d66182464889
workflow-type: tm+mt
source-wordcount: 817
ht-degree: 100%

---


# Traffico bloccato da robots.txt

Il tuo file `robots.txt` controlla quali crawler possono accedere al sito. Quando ad alcuni agenti IA viene impedito di accedere a contenuti che sono invece accessibili a crawler generici, tali agenti non possono indicizzare né citare direttamente tali contenuti, e questo riduce la visibilità del brand nelle risposte generate dall’IA.

L’opportunità Traffico bloccato da robots.txt analizza il file `robots.txt` rispetto alle tue pagine più visitate e individua le regole che impediscono agli agenti IA di accedere a contenuti che dovrebbero invece essere in grado di raggiungere. I risultati sono presentati a livello di singola riga in `robots.txt`, così puoi esaminare e aggiornare specifiche direttive anziché controllare manualmente l’intero file.

Mette subito in evidenza due metriche chiave:

- **URL totali**: numero di URL interessati dalle regole di blocco del tuo `robots.txt`.
- **Agenti bloccati**: numero di agenti IA il cui accesso a tali URL è stato bloccato.

![Dashboard Traffico bloccato da robots.txt](/help/dashboards/opportunities/assets/traffic-blocked-by-robots-overview.png)

## Come funziona

LLM Optimizer recupera il file `robots.txt` e controlla le tue prime pagine rispetto a sei maggiori user agent dell’agente IA:

- ClaudeBot
- GPTBot
- OAI-SearchBot
- OAI-User
- PerplexityBot
- Perplexity-User

Un URL è contrassegnato solo quando è **consentito per l’user agent (`*`) con caratteri jolly ma non per un agente IA specifico**. Il blocco generalizzato, in cui tutti i crawler sono soggetti a restrizioni nella stessa misura, non viene segnalato. L’audit è mirato specificamente all’esclusione selettiva dell’agente IA, che rappresenta il risultato più actionable per la GEO.

>[!NOTE]
>Questa opportunità non utilizza l’IA per sviluppare o consegnare suggerimenti. I risultati si basano interamente sull’analisi diretta del file `robots.txt`.

I risultati sono visualizzati in due schede: **robots.txt** e **Dettagli traffico bloccato dall’agente**.

## robots.txt

In questa scheda viene visualizzato il file `robots.txt` completo, con le direttive di blocco evidenziate in rosso. Ogni riga evidenziata rappresenta una regola che blocca l’accesso, selettivamente per uno o più agenti IA, a un URL altrimenti accessibile al pubblico.

![vista robots.txt con direttive di blocco evidenziate](/help/dashboards/opportunities/assets/traffic-blocked-by-robots-robotstxt.png)

Facendo clic su una direttiva evidenziata vengono visualizzate ulteriori informazioni sul suo impatto e sulla correzione suggerita.

## Dettagli del traffico bloccato per agente

Questa scheda fornisce un raggruppamento del traffico bloccato organizzato per agente IA. Per ogni agente bloccato, la scheda riporta:

- **La descrizione del problema**: spiegazione dell’agente bloccato e del motivo della sua rilevanza.
- **La risoluzione**: indicazioni per aprire il file `robots.txt` e rivedere il numero di riga specifico elencato accanto a ogni URL interessato.
- Una tabella degli URL interessati con la **riga**, il **ranking** e l’**URL** di ciascuna pagina bloccata.

Ogni agente (ad esempio, OAI-User, GPTBot, OAI-SearchBot) dispone di una propria sottoscheda che consente di risolvere i blocchi per agente.

## Risoluzione

Per risolvere il problema di un agente bloccato trovato, apri il file `robots.txt` e individua il numero di riga riportato accanto a ciascun URL interessato nella scheda Dettagli traffico bloccato per agente. Aggiorna o rimuovi la direttiva di esclusione per l’agente IA pertinente per consentire l’accesso all’URL interessato.

Ad esempio, per sbloccare GPTBot da una pagina specifica, rimuovi o aggiorna la direttiva:

```
User-agent: GPTBot
Disallow: /blog/cold-brewing-101
```

Una volta aggiornato e ripubblicato il file `robots.txt`, LLM Optimizer rileverà il cambiamento alla successiva esecuzione dell’audit e contrassegnerà il suggerimento come risolto.

## Prova nella demo

Guarda in azione l’opportunità Traffico bloccato da robots.txt utilizzando l’ambiente demo di Frescopa.

[Visualizza il traffico bloccato da robots.txt nella demo di Frescopa](https://play.llmo.now/org/demo-org/opportunities/blocked-urls-llm-agents)

## Domande frequenti

**Perché il blocco degli agenti IA è importante per la GEO?**

La Generative Engine Optimization richiede che i crawler IA possano accedere e indicizzare il contenuto del sito. Il blocco diretto degli agenti IA impedisce la visualizzazione delle tue pagine nelle risposte generate dall’IA, riducendo citazioni, menzioni del brand e visibilità IA complessiva. Anche una singola pagina con traffico elevato bloccata può rappresentare una notevole perdita di esposizione del brand basata sull’IA.

**Qual è la differenza tra il blocco generalizzato e il blocco selettivo?**

Con il blocco generalizzato viene impedito l’accesso a una pagina per tutti i crawler, inclusi i crawler web generali. Il blocco selettivo consente ai crawler generali di accedere alla pagina, ma non ad agenti IA specifici. Questa opportunità segnala solo il blocco selettivo perché rappresenta un’esclusione intenzionale o accidentale degli agenti IA da contenuti altrimenti pubblici, il che è il risultato più actionable.

**Quali agenti IA controlla LLM Optimizer?**

LLM Optimizer verifica la presenza di ClaudeBot, GPTBot, OAI-SearchBot, OAI-User, PerplexityBot e Perplexity-User.

**E se volessi bloccare intenzionalmente determinati agenti IA?**

Puoi rivedere ciascuna direttiva segnalata e scegliere se mantenere il blocco intenzionalmente. I suggerimenti ignorati sono conservati nelle varie esecuzioni di audit e non saranno riproposti a meno che il file `robots.txt` non venga modificato e la regola non ricompaia.

**Come fa LLM Optimizer a tenere traccia delle modifiche apportate al mio file robots.txt nel tempo?**

LLM Optimizer utilizza l’hashing per tenere traccia del contenuto di `robots.txt` nelle varie esecuzioni. Se una regola di blocco precedentemente risolta ricompare, ad esempio dopo un aggiornamento di `robots.txt`, verrà riproposta come nuovo suggerimento.

**Come vengono determinate le prime pagine?**

Le pagine sono reperite combinando le tue pagine SEO con il maggior traffico, gli URL più visitati dagli agenti IA dai registri CDN ed eventuali URL personalizzati specificati nella configurazione del tuo sito.
