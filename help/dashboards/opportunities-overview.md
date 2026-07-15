---
title: Opportunità di ottimizzazione
description: Scopri come utilizzare la dashboard Opportunità per rilevare automaticamente come migliorare il tuo sito per aumentare la visibilità del brand.
feature: Opportunities
autotag-review: '2026-07-15T18:08:26.657Z'
TQID: 'https://experienceleague.adobe.com/nEVOXJiQZIqfs2Q-tpA3DeiBNwpZAjhMSyIVuNlACdM'
product_v2:
  - id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2:
  - id: e1b649f0-0a61-46e4-9082-64d5cb2576c6
  - id: ef4e63f5-cb4d-462d-bf9a-1f617edf2a3a
subfeature_v2:
  - id: bbfc1b77-44c5-4fe8-b65f-ec160fe0d021
  - id: a6256a78-8814-462c-9627-86699b39cee1
  - id: e0ec491f-fe51-42b6-801c-1c0dfcc0e64f
  - id: fe92ae96-fc87-4fea-96a0-adc06310d4f4
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
source-git-commit: 2705cf26faea9c09817bbdcec4b4c531552df7ba
workflow-type: tm+mt
source-wordcount: 1225
ht-degree: 56%

---


# Opportunità di ottimizzazione

Le opportunità di ottimizzazione vengono rilevate automaticamente e forniscono insight che mostrano dove è possibile migliorare la presenza sul sito e quella esterna, per aumentare la visibilità del brand nelle ricerche IA.

Le ottimizzazioni includono correzioni nella pagina (aggiunta di contenuti strutturati, canonici o riepiloghi); adeguamenti tecnici (sblocco di crawler IA o risoluzione di errori); e influenza dei contenuti su siti autorevoli di terze parti. Intervenendo sulla base di queste opportunità di ottimizzazione, potrai assicurarti che il tuo brand sia rappresentato accuratamente e aumentare le probabilità che venga citato nelle risposte generative.

<!--![Optimization opportunities](/help/dashboards/assets/oport.png)-->

## Dashboard Opportunità

Nella dashboard, le opportunità di ottimizzazione sono ordinate per priorità in base a lacune rispetto alla concorrenza, argomenti di tendenza e dati sulle prestazioni; quindi vengono presentate sotto forma di elenco. Utilizzando il campo di ricerca puoi ricercare un’opportunità specifica. Inoltre, le opportunità sono raggruppate per tag: fai clic direttamente su un tag per mostrare tutte le opportunità raggruppate sotto tale tag.

Facendo clic su **Dettagli** si apre una finestra separata contente informazioni e indicazioni aggiuntive.

## Opportunità supportate

Di seguito è riportata una tabella delle opportunità attualmente supportate:

| Opportunità | Tipo | Problemi identificati | Suggerimenti per la correzione |
|---------|----------|----------|----------|
| [Aggiungi riepiloghi compatibili con LLM](/help/dashboards/opportunities/add-llm-friendly-summaries.md) | Contenuto (nel sito) | Identifica pagine a traffico elevato prive di riepiloghi concisi e di punti chiave strutturati a livello di pagina o di sezione, rendendo più difficile agli agenti di intelligenza artificiale analizzare e interpretare le dichiarazioni del brand. Mostra gli URL interessati e dove sono consigliati i riepiloghi. | Rivedi i riepiloghi e i punti chiave generati dall’intelligenza artificiale basati sul contenuto esistente, quindi distribuiscili al limite della CDN con Ottimizza in Edge in modo che gli agenti ricevano un contesto più chiaro e riconoscibile. |
| [Aggiungi domande frequenti pertinenti](/help/dashboards/opportunities/add-relevant-faqs.md) | Contenuto (nel sito) | Identifica le pagine a traffico elevato prive di contenuti Q&amp;A strutturati allineati al set di prompt, rendendo più difficile per gli agenti AI far corrispondere le domande degli utenti alla pagina. Mostra gli URL interessati e dove sono consigliate le domande frequenti. | Rivedi i contenuti delle domande frequenti generate dall’intelligenza artificiale e allineate alle finalità, fondati sul materiale della pagina esistente, quindi distribuiscili al limite della CDN con Ottimizza in Edge in modo che gli agenti ricevano un contesto Q&amp;A più chiaro. |
| [Aggiungi riepiloghi di trascrizioni multimediali](/help/dashboards/opportunities/add-multimedia-transcript-summaries.md) | Contenuto (nel sito) | Identifica le pagine in cui le informazioni chiave sono incorporate in video o altri supporti senza trascrizioni o riepiloghi leggibili automaticamente, rendendo difficile l’utilizzo di tali contenuti per gli agenti di intelligenza artificiale. Mostra gli URL interessati e il testo consigliato. | Rivedi i riepiloghi delle trascrizioni generati dall’intelligenza artificiale nei contenuti multimediali e nella pagina, quindi distribuiscili al limite della CDN con Ottimizza in Edge in modo che gli agenti ricevano testo leggibile al computer (ad esempio, vicino al video rilevante). |
| [Traffico bloccato da robots.txt](/help/dashboards/opportunities/traffic-blocked-by-robots.md) | GEO tecnica | Analizza il file robots.txt per individuare le regole che bloccano selettivamente per gli agenti IA contenuti altrimenti accessibili pubblicamente. Segnala gli URL interessati e gli agenti bloccati. | Se necessario, aggiorna il file robots.txt per consentire l’accesso ai crawler IA supportati. |
| [Errori del traffico da IA agentica](/help/dashboards/opportunities/agentic-traffic-errors.md) | GEO tecnica | Monitora i registri CDN per le risposte di errori 404, 403 e 5xx restituite agli agenti IA. Segnala gli URL interessati e gli hit totali persi. | Correggi i collegamenti interrotti, aggiorna le autorizzazioni e risolvi i problemi lato server in modo che il contenuto chiave restituisca 200 risposte. |
| [Semplifica contenuti complessi](/help/dashboards/opportunities/simplify-complex-content.md) | Contenuto (nel sito) | Identifica le pagine a traffico elevato in cui la copia densa o complessa si trova al di sotto delle soglie di leggibilità, rendendo più difficile per gli agenti di intelligenza artificiale interpretare le informazioni chiave. Mostra gli URL interessati e dove si consiglia di usare testo semplificato. | Rivedi il testo migliorato generato dall’intelligenza artificiale basato sul contenuto della pagina esistente, quindi distribuiscilo al limite della CDN con Ottimizza in Edge in modo che gli agenti ricevano passaggi più chiari e facili da scansionare. |
| [Recuperare la visibilità dei contenuti](/help/dashboards/opportunities/recover-content-visibility.md) | GEO tecnica | Contrassegna le pagine in cui il contenuto critico è nascosto dagli agenti IA. Mostra gli URL interessati e i contenuti previsti che possono essere recuperati. | Esegui il pre-rendering delle pagine al livello CDN utilizzando Ottimizza su rete Edge affinché per gli agenti IA siano disponibili più contenuti senza l’esecuzione di JavaScript. |
| [Aggiungi sommario](/help/dashboards/opportunities/add-table-of-contents.md) | GEO tecnica | Rileva le pagine prive di chiare intestazioni strutturali di organizzazione o navigazione, rendendo difficile per gli agenti AI analizzare e mappare il contenuto alle query degli utenti. Mostra gli URL interessati e il punto in cui si consiglia un sommario strutturato. | Rivedi il sommario strutturato suggerito con intestazioni collegate a un ancoraggio che riflettono le sezioni principali della pagina, quindi distribuiscilo sul lato CDN con Ottimizza in Edge in modo da inserire un sommario in HTML, migliorando la struttura della pagina in modo che i modelli possano estrarre, mappare e citare più facilmente le sezioni rilevanti. |
| [Analisi Wikipedia](/help/dashboards/opportunities/wikipedia-analysis.md) | Siti esterni | Analizza la pagina Wikipedia della tua azienda rispetto ai concorrenti del settore in termini di riferimenti, sezioni, lunghezza dei contenuti, immagini e completezza dell’Infobox. Identifica lacune specifiche quando la pagina è inferiore ai benchmark di settore. | Rivedi i consigli strategici generati dall’IA per migliorare la presenza su Wikipedia, tra cui l’aggiunta di riferimenti, l’arricchimento dell’infobox, l’espansione delle sezioni e il miglioramento della qualità degli articoli. |
| [Analisi del sentiment YouTube (Beta)](/help/dashboards/opportunities/youtube-sentiment-analysis.md) | Siti esterni, social e community | Analizza i video di YouTube citati per il set di prompt relativi alla presenza del brand per individuare menzioni del brand, sentiment, share of voice e argomenti ricorrenti. Viene visualizzata solo quando i video di YouTube sono rilevati come citazioni per il set di prompt. | Rivedi i consigli prioritari per migliorare la percezione del brand in tutti i contenuti di YouTube, tra cui le azioni suggerite e i team responsabili della loro implementazione. |
| [Analisi del sentiment Reddit (Beta)](/help/dashboards/opportunities/reddit-sentiment-analysis.md) | Siti esterni, social e community | Analizza i thread di Reddit citati per il set di prompt relativi alla presenza del brand per individuare menzioni del brand, sentiment, share of voice e argomenti ricorrenti. Viene visualizzata solo quando i thread di Reddit sono rilevati come citazioni per il set di prompt. | Rivedi i consigli prioritari per migliorare la percezione del brand in tutti i contenuti di Reddit, tra cui le azioni suggerite e i team responsabili della loro implementazione. |
| [Analisi del sentiment delle citazioni (Beta)](/help/dashboards/opportunities/cited-sentiment-analysis.md) | Siti esterni, social e community | Analizza gli URL più citati per il set di prompt relativi alla presenza del brand per individuare menzioni del brand, sentiment, share of voice e argomenti ricorrenti. | Rivedi i consigli prioritari per migliorare la percezione del brand in tutte le pagine citate di più dai sistemi di IA quando rispondono a prompt relativi al tuo brand. |
| [Arricchisci catalogo prodotti (Beta)](/help/dashboards/opportunities/enrich-product-catalog.md) | Contenuto (nel sito), Adobe Commerce | Identifica i prodotti del catalogo Commerce i cui nomi o descrizioni sono troppo generici, tecnicamente densi o ambigui per consentire l&#39;interpretazione da parte dei moduli LLM. Mostra PDP valutati, contesto del traffico agente e arricchimenti narrativi generati dall’intelligenza artificiale. | Rivedi e modifica i nomi e le descrizioni dei prodotti proposti, quindi distribuisci le ottimizzazioni per pubblicare gli aggiornamenti direttamente nel catalogo Adobe Commerce (con rollback da Suggerimenti fissi). |
| [Arricchisci pagine dettagli prodotto](/help/dashboards/opportunities/enrich-product-detail-pages.md) | Area geografica tecnica, Adobe Commerce | Per le vetrine di Adobe Commerce, confronta i dati del catalogo completo con quelli a cui gli agenti AI possono accedere in ogni pagina dei dettagli del prodotto; mette in evidenza delle PDP in cui varianti, specifiche, attributi e campi catalogo correlati non sono presenti nel HTML visibile dall’agente, con priorità per il traffico agente. | Evidenzia le informazioni del catalogo recuperabili mancanti dalla vista dell’agente e il motivo per cui sono importanti per l’individuazione dei prodotti basata su LLM; implementa con Ottimizza in Edge per fornire un’istantanea di HTML completamente pre-renderizzata e compatibile con l’intelligenza artificiale al traffico agentico all’edge della CDN, in modo che gli agenti ricevano un contesto di prodotto avanzato dal catalogo senza modifiche a CMS o al catalogo. |

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
