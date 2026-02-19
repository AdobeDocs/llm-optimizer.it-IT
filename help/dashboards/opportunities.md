---
title: Opportunità di ottimizzazione
description: Scopri come utilizzare la dashboard Opportunità per rilevare automaticamente come migliorare il tuo sito per aumentare la visibilità del brand.
feature: Opportunities
source-git-commit: 3204d46106b4ae1645df19138cabd55bf153eb42
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 97%

---


# Opportunità di ottimizzazione

Le opportunità di ottimizzazione vengono rilevate automaticamente e forniscono insight che mostrano dove è possibile migliorare la presenza sul sito e quella esterna, per aumentare la visibilità del brand nelle ricerche IA.

Le ottimizzazioni includono correzioni nella pagina (aggiunta di contenuti strutturati, canonici o riepiloghi); adeguamenti tecnici (sblocco di crawler IA o risoluzione di errori); e influenza dei contenuti su siti autorevoli di terze parti. Intervenendo sulla base di queste opportunità di ottimizzazione, potrai assicurarti che il tuo brand sia rappresentato accuratamente e aumentare le probabilità che venga citato nelle risposte generative.

![Opportunità di ottimizzazione](/help/dashboards/assets/oport.png)

## Dashboard Opportunità

Nella dashboard, le opportunità di ottimizzazione sono ordinate per priorità in base a lacune rispetto alla concorrenza, argomenti di tendenza e dati sulle prestazioni; quindi vengono presentate sotto forma di elenco. Utilizzando il campo di ricerca puoi ricercare un’opportunità specifica. Inoltre, le opportunità sono raggruppate per tag: fai clic direttamente su un tag per mostrare tutte le opportunità raggruppate sotto tale tag.

Facendo clic su **Dettagli** si apre una finestra separata contente informazioni e indicazioni aggiuntive.

## Opportunità supportate

Di seguito è riportata una tabella delle opportunità attualmente supportate:

| Opportunità | Tipo | Problemi identificati | Suggerimenti per la correzione |
|---------|----------|----------|----------|
| Riepiloga paragrafi lunghi | Contenuto (nel sito) | Rileva i paragrafi che superano le soglie di lunghezza consigliate. Mostra gli URL interessati e snippet del testo tropo lungo. | Crea sunti o dividi i testi lunghi in sezioni più brevi e più facili da analizzare. |
| Consiglia contenuti strutturati (domande frequenti) | Contenuto (nel sito) | Rileva l’assenza di voci di tipo “Domande frequenti” necessarie per rispondere ai prompt più diffusi. Mostra i prompt correlati, le categorie e gli URL interessati. | Aggiungi blocchi di schema per sezioni “Domande frequenti” con risposte concise, in linea con le richieste più comuni. |
| Rileva traffico da IA agentica bloccato | GEO tecnica | Analizza i registri CDN per le richieste bloccate da agenti IA noti, ad esempio, GPTBot, PerplexityBot. Segnala gli URL e gli agenti interessati. | Se necessario, aggiorna il file robots.txt o le configurazioni server per consentire l’accesso ai crawler IA supportati. |
| Rileva problemi 404s / 403s / 5xx | GEO tecnica | Esegue il monitoraggio dei registri CDN per le risposte di errore. Segnala la frequenza, gli URL interessati e gli hit persi stimati. | Correggi i collegamenti interrotti, aggiorna le autorizzazioni e risolvi i problemi lato server in modo che il contenuto chiave restituisca 200 risposte. |
| Semplifica contenuti complessi | Contenuto (nel sito) | Identifica paragrafi lunghi e complessi che superano le soglie di leggibilità che possono ridurre la comprensione dell’intelligenza artificiale. | Esegui il pre-rendering delle pagine in modo che sia disponibile più contenuto per gli agenti IA senza l’esecuzione di JavaScript. |
| Recupera visibilità dei contenuti (accesso anticipato) | GEO tecnica | Contrassegna le pagine in cui il contenuto critico è nascosto dagli agenti IA. Mostra gli URL interessati e i contenuti previsti che possono essere recuperati. | Esegui il pre-rendering delle pagine in modo che sia disponibile più contenuto per gli agenti IA senza l’esecuzione di JavaScript. |

## Ottimizzazione automatica {#auto-optimization}

L’ottimizzazione automatica consente la distribuzione con un solo clic delle ottimizzazioni consigliate, riducendo le attività manuali e il TTV (Time-To-Value). Puoi applicare le ottimizzazioni all’origine del contenuto o sul lato CDN. L’ottimizzazione automatica basata su Edge è attualmente disponibile in Accesso anticipato per alcune opportunità. Per ulteriori dettagli, consulta la pagina [Ottimizzazione nella rete Edge](/help/dashboards/optimize-at-edge/overview.md).

<!--### Recover Content Visibility Opportunity {#recover-contet}

As stated above, the content visibility opportunity, flags pages where key content is lost for AI agents due to client-side rendering. For each identified page, it shows you exactly which content is missing from the AI agent view, helping you pinpoint visibility gaps. It's also supported by an edge-based pre-rendering capability that can serve more HTML content to agentic traffic without requiring Content Management System (CMS) changes. This functionality is currently in Early Access and requires setup from the LLM Optimizer team. Please contact `llmo-at-edge@adobe.com` to activate the content visibility opportunity.-->

### Strumenti aggiuntivi

Il [controllo di visibilità degli LLM](https://chromewebstore.google.com/detail/is-your-webpage-citable/jbjngahjjdgonbeinjlepfamjdmdcbcc) è un’estensione di Chrome che consente di visualizzare esattamente la quantità di contenuto della pagina web a cui gli LLM possono accedere e ciò che rimane nascosto. Progettato come strumento diagnostico indipendente e gratuito, non richiede alcuna licenza o configurazione del prodotto. Con un solo clic, gli utenti possono valutare la leggibilità automatica di qualsiasi sito, visualizzando un confronto affiancato tra ciò che gli agenti IA visualizzano e ciò che gli utenti vedono. Inoltre, stima la quantità di contenuto che può essere recuperata utilizzando LLM Optimizer.

<!--| Detect Missing Hreflang | Content (Onsite)| Flags pages missing hreflang attributes. Provides affected URLs and expected coverage by language/region.| Implement hreflang tags to indicate correct localized versions. |
| Detect Missing Canonicals | Content (Onsite) | Scans for pages without canonical tags or with conflicting tags. Lists affected URLs and duplicates. | Add canonical tags pointing to the preferred version of each page. Ensure consistent usage across variants. |-->
