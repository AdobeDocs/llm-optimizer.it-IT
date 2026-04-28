---
title: Traffico bloccato da robots.txt
description: Scopri come LLM Optimizer rileva quando il file robots.txt impedisce agli agenti di IA di accedere al contenuto e come correggerlo.
feature: Opportunities
source-git-commit: fa8b994aa55869cf7f2607e792acc4e8abc213e7
workflow-type: tm+mt
source-wordcount: '817'
ht-degree: 1%

---


# Traffico bloccato da robots.txt

Il file `robots.txt` controlla quali crawler possono accedere al sito. Quando gli agenti di intelligenza artificiale sono bloccati selettivamente dal contenuto altrimenti accessibile ai crawler generici, non possono indicizzare o citare tale contenuto riducendo direttamente la visibilità del brand nelle risposte generate dall’intelligenza artificiale.

L&#39;opportunità Traffic Blocked by robots.txt analizza il file `robots.txt` rispetto alle pagine principali e identifica le regole che impediscono agli agenti di intelligenza artificiale di accedere al contenuto che dovrebbero essere in grado di raggiungere. Mette in evidenza i risultati a livello di singola riga `robots.txt` in modo da poter esaminare e aggiornare direttive specifiche anziché controllare manualmente l&#39;intero file.

Mostra due metriche chiave a colpo d’occhio:

- **URL totali** — numero di URL interessati dalle regole di blocco in `robots.txt`.
- **Agenti bloccati** — Numero di agenti di IA bloccati per l&#39;accesso a tali URL.

![Traffico bloccato dal dashboard robots.txt](/help/dashboards/opportunities/assets/traffic-blocked-by-robots-overview.png)

## Come funziona

LLM Optimizer recupera il file `robots.txt` e verifica le pagine principali rispetto a sei agenti utente principali dell&#39;agente di intelligenza artificiale:

- ClaudeBot
- GPTBot
- OAI-SearchBot
- Utente OAI
- PerplexityBot
- Perplessità-Utente

Un URL viene contrassegnato solo quando è **consentito per l&#39;agente utente con caratteri jolly (`*`) ma non consentito per un agente di IA specifico**. Il blocco totale, in cui tutti i crawler sono soggetti a restrizioni uguali, non è segnalato. L’audit è specificamente incentrato sull’esclusione selettiva dell’agente di IA, che rappresenta il risultato più actionable per GEO.

>[!NOTE]
>Questa opportunità non utilizza l’intelligenza artificiale per lo sviluppo o la distribuzione di suggerimenti. I risultati si basano interamente sull&#39;analisi diretta del file `robots.txt`.

I risultati vengono visualizzati in due schede: **robots.txt** e **Dettagli traffico bloccato dall&#39;agente**.

## robots.txt

In questa scheda viene visualizzato l&#39;intero file `robots.txt` con le direttive di blocco evidenziate in rosso. Ogni riga evidenziata rappresenta una regola che impedisce selettivamente a uno o più agenti di IA di accedere a un URL altrimenti accessibile al pubblico.

![vista robots.txt con direttive di blocco evidenziate](/help/dashboards/opportunities/assets/traffic-blocked-by-robots-robotstxt.png)

Facendo clic su una direttiva evidenziata vengono visualizzate ulteriori informazioni sul suo impatto e sulla correzione suggerita.

## Dettagli del traffico bloccato per agente

Questa scheda fornisce un raggruppamento del traffico bloccato organizzato dall’agente di IA. Per ogni agente bloccato viene visualizzato quanto segue:

- **Descrizione problema** — Spiegazione dell&#39;agente bloccato e del motivo della sua rilevanza.
- **Risoluzione**: istruzioni per aprire il file `robots.txt` e rivedere il numero di riga specifico elencato accanto a ogni URL interessato.
- Tabella degli URL interessati con **Riga**, **Classifica** e **URL** per ogni pagina bloccata.

Ogni agente (ad esempio, OAI-User, GPTBot, OAI-SearchBot) dispone di una propria scheda secondaria che consente di indirizzare i blocchi per agente.

## Risoluzione

Per risolvere il problema di un agente bloccato trovato, aprire il file `robots.txt` e individuare il numero di riga visualizzato accanto a ogni URL interessato nella scheda Dettagli traffico bloccato per agente. Aggiorna o rimuovi la direttiva di esclusione per l’agente di IA pertinente per consentire l’accesso all’URL interessato.

Ad esempio, per sbloccare GPTBot da una pagina specifica, rimuovi o aggiorna la direttiva:

```
User-agent: GPTBot
Disallow: /blog/cold-brewing-101
```

Una volta aggiornato e ripubblicato il file `robots.txt`, LLM Optimizer rileverà la modifica alla successiva esecuzione del controllo e contrassegnerà il suggerimento come risolto.

## Prova la demo

Guarda l’opportunità Traffico bloccato da robots.txt in azione utilizzando l’ambiente demo Frescopa.

[Visualizza il traffico bloccato da robots.txt nella demo di Frescopa](https://play.llmo.now/org/demo-org/opportunities/blocked-urls-llm-agents)

## Domande frequenti

**Perché il blocco degli agenti di IA è importante per GEO?**

Generative Engine Optimization richiede che i crawler di intelligenza artificiale possano accedere e indicizzare il contenuto del sito. Il blocco diretto degli agenti di intelligenza artificiale impedisce la visualizzazione delle pagine nelle risposte generate dall’intelligenza artificiale, riducendo citazioni, menzioni dei brand e la visibilità complessiva dell’intelligenza artificiale. Anche una singola pagina bloccata a traffico elevato può rappresentare una perdita significativa di esposizione del brand basata sull’intelligenza artificiale.

**Qual è la differenza tra il blocco aperto e il blocco selettivo?**

Blocco aperto indica che tutti i crawler, inclusi i crawler Web generali, sono limitati da una pagina. Il blocco selettivo consente ai crawler generali di accedere alla pagina, ma non agli agenti di IA specifici. Questa opportunità contrassegna solo il blocco selettivo perché rappresenta un’esclusione intenzionale o accidentale degli agenti di intelligenza artificiale da contenuti altrimenti pubblici, che è il risultato più actionable.

**Quali agenti di IA controllano LLM Optimizer?**

LLM Optimizer verifica la presenza di ClaudeBot, GPTBot, OAI-SearchBot, OAI-User, PerplexityBot e Perplexity-User.

**Cosa succede se si desidera bloccare intenzionalmente alcuni agenti di IA?**

Puoi rivedere ogni direttiva segnalata e scegliere di mantenere il blocco intenzionalmente. I suggerimenti ignorati vengono mantenuti in tutte le esecuzioni di controllo e non verranno rivisualizzati a meno che il file `robots.txt` non venga modificato e la regola non venga rivisualizzata.

**In che modo LLM Optimizer tiene traccia delle modifiche apportate al file robots.txt nel tempo?**

LLM Optimizer utilizza l&#39;hashing per tenere traccia del contenuto di `robots.txt` in più esecuzioni. Se una regola di blocco risolta in precedenza viene visualizzata di nuovo, ad esempio dopo un aggiornamento di `robots.txt`, verrà visualizzata di nuovo come nuovo suggerimento.

**Come vengono determinate le pagine principali?**

Le pagine provengono da una combinazione delle pagine SEO con traffico più elevato, degli URL visitati dall’agente AI principali dai registri CDN e di qualsiasi URL personalizzato specificato nella configurazione del sito.
