---
title: Opportunità di ottimizzazione
description: Scopri come utilizzare la dashboard Opportunità per rilevare automaticamente come migliorare il tuo sito per aumentare la visibilità del brand.
feature: Opportunities
source-git-commit: 34e90bc95aa1d2ffabe8fd06c2c548491dd5c5b7
workflow-type: tm+mt
source-wordcount: '780'
ht-degree: 58%

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
| Consigliare contenuti strutturati | Contenuto (nel sito) | Rileva l’assenza di voci di tipo “Domande frequenti” necessarie per rispondere ai prompt più diffusi. Mostra i prompt correlati, le categorie e gli URL interessati. | Aggiungi blocchi di schema per sezioni “Domande frequenti” con risposte concise, in linea con le richieste più comuni. |
| [Traffico bloccato da robots.txt](/help/dashboards/opportunities/traffic-blocked-by-robots.md) | GEO tecnica | Analizza il file robots.txt per individuare le regole che bloccano selettivamente gli agenti di intelligenza artificiale da contenuti altrimenti accessibili pubblicamente. Segnala gli URL interessati e gli agenti bloccati. | Se necessario, aggiorna il file robots.txt per consentire l’accesso ai crawler di intelligenza artificiale supportati. |
| [Errori di traffico agente](/help/dashboards/opportunities/agentic-traffic-errors.md) | GEO tecnica | Monitora i registri CDN per le risposte di errore 404, 403 e 5xx restituite agli agenti AI. I rapporti sugli URL interessati e sugli hit totali sono stati persi. | Correggi i collegamenti interrotti, aggiorna le autorizzazioni e risolvi i problemi lato server in modo che il contenuto chiave restituisca 200 risposte. |
| Semplifica contenuti complessi | Contenuto (nel sito) | Identifica paragrafi lunghi e complessi che superano le soglie di leggibilità che possono ridurre la comprensione dell’intelligenza artificiale. | Esegui il pre-rendering delle pagine in modo che sia disponibile più contenuto per gli agenti IA senza l’esecuzione di JavaScript. |
| [Ripristina Visibilità dei contenuti](/help/dashboards/opportunities/recover-content-visibility.md) | GEO tecnica | Contrassegna le pagine in cui il contenuto critico è nascosto dagli agenti IA. Mostra gli URL interessati e i contenuti previsti che possono essere recuperati. | Esegui il pre-rendering delle pagine a livello di CDN utilizzando Ottimizza in Edge, in modo che sia disponibile più contenuto per gli agenti di IA senza esecuzione di JavaScript. |
| [Analisi Wikipedia](/help/dashboards/opportunities/wikipedia-analysis.md) | Fuori sede | Analizza la pagina di Wikipedia della tua azienda rispetto ai concorrenti del settore per riferimenti, sezioni, lunghezza dei contenuti, immagini e completezza della Infobox. Identifica lacune specifiche quando la pagina è inferiore ai benchmark di settore. | Rivedi le raccomandazioni strategiche generate dall’intelligenza artificiale per migliorare la presenza su Wikipedia, inclusi l’aggiunta di riferimenti, l’arricchimento della tua infobox, l’espansione delle sezioni e il miglioramento della qualità degli articoli. |
| [Analisi Sentiment YouTube (Beta)](/help/dashboards/opportunities/youtube-sentiment-analysis.md) | Fuori sede, social network e community | Analizza i video YouTube citati per il prompt di Presenza dei brand impostato per menzione del brand, sentiment, share of voice e argomenti ricorrenti. Viene visualizzato solo quando i video di YouTube vengono rilevati come citazioni per il set di prompt. | Rivedi i consigli con priorità per migliorare la percezione del brand in tutti i contenuti di YouTube, incluse le azioni suggerite e i team responsabili della loro implementazione. |
| [Analisi Sentiment Reddit (Beta)](/help/dashboards/opportunities/reddit-sentiment-analysis.md) | Fuori sede, social network e community | Analizza i thread Reddit citati per il prompt di Presenza dei brand impostato per gli argomenti menzione del brand, sentiment, share of voice e ricorrenti. Viene visualizzato solo quando i thread di Reddit vengono rilevati come citazioni per il set di prompt. | Rivedi le raccomandazioni prioritarie per migliorare la percezione del brand in tutti i contenuti Reddit, incluse le azioni suggerite e i team responsabili della loro implementazione. |
| [Analisi Sentiment Citato (Beta)](/help/dashboards/opportunities/cited-sentiment-analysis.md) | Fuori sede, social network e community | Analizza gli URL più citati rilevati per il set di prompt Presenza dei brand per menzioni dei brand, sentiment, share of voice e argomenti ricorrenti. | Rivedi i consigli con priorità per migliorare la percezione del brand nelle pagine che i sistemi di intelligenza artificiale citano di più quando rispondono alle richieste sul tuo brand. |

## Ottimizzazione automatica {#auto-optimization}

L’ottimizzazione automatica consente la distribuzione con un solo clic delle ottimizzazioni consigliate, riducendo le attività manuali e il TTV (Time-To-Value). Puoi applicare le ottimizzazioni all’origine del contenuto o sul lato CDN. L’ottimizzazione automatica basata su Edge è attualmente disponibile in Accesso anticipato per alcune opportunità. Per ulteriori dettagli, consulta la pagina [Ottimizzazione nella rete Edge](/help/dashboards/optimize-at-edge/overview.md).

<!--
### Recover Content Visibility Opportunity {#recover-contet}

As stated above, the content visibility opportunity, flags pages where key content is lost for AI agents due to client-side rendering. For each identified page, it shows you exactly which content is missing from the AI agent view, helping you pinpoint visibility gaps. It's also supported by an edge-based pre-rendering capability that can serve more HTML content to agentic traffic without requiring Content Management System (CMS) changes. This functionality is currently in Early Access and requires setup from the LLM Optimizer team. Please contact `llmo-at-edge@adobe.com` to activate the content visibility opportunity.
-->

### Strumenti aggiuntivi

Il [controllo di visibilità degli LLM](https://chromewebstore.google.com/detail/is-your-webpage-citable/jbjngahjjdgonbeinjlepfamjdmdcbcc) è un’estensione di Chrome che consente di visualizzare esattamente la quantità di contenuto della pagina web a cui gli LLM possono accedere e ciò che rimane nascosto. Progettato come strumento diagnostico indipendente e gratuito, non richiede alcuna licenza o configurazione del prodotto. Con un solo clic, gli utenti possono valutare la leggibilità automatica di qualsiasi sito, visualizzando un confronto affiancato tra ciò che gli agenti IA visualizzano e ciò che gli utenti vedono. Inoltre, stima la quantità di contenuto che può essere recuperata utilizzando LLM Optimizer.

<!--
| Detect Missing Hreflang | Content (Onsite)| Flags pages missing hreflang attributes. Provides affected URLs and expected coverage by language/region.| Implement hreflang tags to indicate correct localized versions. |
| Detect Missing Canonicals | Content (Onsite) | Scans for pages without canonical tags or with conflicting tags. Lists affected URLs and duplicates. | Add canonical tags pointing to the preferred version of each page. Ensure consistent usage across variants. |
-->
