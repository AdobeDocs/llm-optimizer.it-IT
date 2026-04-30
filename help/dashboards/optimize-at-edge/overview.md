---
title: Ottimizzazione nella rete Edge
description: Scopri come applicare le ottimizzazioni in LLM Optimizer direttamente a livello di CDN senza la necessità di apportare modifiche di authoring.
feature: Opportunities
product_v2:
  - id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2:
  - id: a0b5a505-2fd7-4c3d-b61c-b557fb6f0558
subfeature_v2:
  - id: e1b649f0-0a61-46e4-9082-64d5cb2576c6
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
  - id: e9001ce2-5245-4a8e-8601-dd958009072f
autotag-review: '2026-04-30T18:15:36.189Z'
source-git-commit: b286358b901575290ace70b0eb47dcb82061559f
workflow-type: tm+mt
source-wordcount: 3108
ht-degree: 57%

---


# Ottimizzazione nella rete Edge

Questa pagina fornisce una panoramica dettagliata su come applicare le ottimizzazioni a livello di CDN senza alcuna modifica all’authoring. Descrive il processo di onboarding, le opportunità di ottimizzazione disponibili e la procedura di ottimizzazione automatica nella rete Edge.

## Che cos’è l’ottimizzazione nella rete Edge?

L’ottimizzazione nella rete Edge è una funzionalità di implementazione basata su Edge in LLM Optimizer che fornisce modifiche AI descrittive agli agenti utente degli LLM. Nel contesto corrente, “Edge” indica che l’ottimizzazione viene applicata a livello della CDN. Poiché distribuisce le ottimizzazioni a livello della CDN, non sono necessarie modifiche di authoring nel Sistema di gestione dei contenuti (CMS), lasciando invariato il CMS di origine. Questa separazione ti consente di migliorare la visibilità degli LLM senza modificare i flussi di lavoro di pubblicazione esistenti. Si rivolge solo al traffico da IA agentica e non influisce né sugli utenti né sui bot SEO. Quando LLM Optimizer rileva opportunità per ottimizzare una pagina, gli utenti possono implementare correzioni direttamente a livello della CDN.

L’ottimizzazione nella rete Edge rappresenta un’alternativa più veloce e più snella alle correzioni tradizionali che richiedono attività tecniche complesse. Come accennato, una volta completata la configurazione una tantum, non dovrai apportare modifiche alle piattaforme né eseguire lunghi cicli di sviluppo per applicare i cambiamenti. Puoi pubblicare miglioramenti in pochi minuti senza richiedere il coinvolgimento degli sviluppatori. È una soluzione senza codice per ottimizzare il tuo sito web per gli agenti IA.

L’ottimizzazione nella rete Edge è progettata per gli utenti business nei team di marketing e responsabili della SEO, dei contenuti e delle strategie digitali. Consente agli utenti business di completare l’intero percorso in LLM Optimizer: identificando le opportunità, comprendendo i suggerimenti e implementando facilmente le correzioni. Con l’ottimizzazione nella rete Edge, gli utenti possono visualizzare in anteprima le modifiche, implentarle rapidamente a livello di CDN e verificare che le ottimizzazioni siano live. Le prestazioni possono essere tracciate nell’ecosistema di LLM Optimizer.

### Vantaggi principali

* **Distribuzione solo con IA:** fornisce HTML ottimizzato solo agli agenti IA, senza alcun impatto sui visitatori o sui bot SEO.
* **Cicli più veloci:** pubblica le modifiche in pochi minuti anziché settimane. Non sono necessarie modifiche alla piattaforma o lunghi cicli di progettazione.
* **Reversibile:** supportata da una funzionalità di rollback con un solo clic in grado di ripristinare la pagina in pochi minuti.
* **Nessun impatto sulle prestazioni:** le ottimizzazioni basate su Edge e la memorizzazione in cache non influiscono sulla latenza del sito.
* **Indipendente da CDN e CMS:** funziona con qualsiasi configurazione CDN e front-end indipendentemente dal sistema di gestione dei contenuti.

### Quali opportunità sono supportate con l’ottimizzazione nella rete Edge?

Con l’ottimizzazione nella rete Edge, sono supportate le opportunità che possono migliorare l’esperienza da IA agentica sul web. Ulteriori informazioni su ciascuna opportunità sono disponibili sia nella pagina della [Dashboard Opportunità](/help/dashboards/opportunities-overview.md) che nella sezione Opportunità della pagina corrente.

## Onboarding

<!--You should reach out to either your Adobe account team or the FDE team to start the onboarding process. Your IT or CDN team is also required to complete the pre-requisites and setup process. Additionally, you can also contact `llmo-at-edge@adobe.com` for further onboarding assistance.-->

Avvia il processo di onboarding nel tuo account LLM Optimizer:

1. Nel dashboard **Configurazione cliente** selezionare la scheda **Configurazione rete CDN**.
1. Fai clic su **CDN integrato**.
   ![Scheda Configurazione CDN](/help/overview/assets/cc-cdn.png)
1. Per i clienti Fastly gestiti da AEM Cloud Service, la configurazione dell’indirizzamento è self-service e può essere completata direttamente nell’interfaccia utente di LLM Optimizer. Per i clienti che utilizzano altri provider CDN, il team IT/CDN deve completare la configurazione e i prerequisiti richiesti. Per ulteriori informazioni, consulta anche le guide CDN di esempio fornite di seguito.

>[!NOTE]
>Fai riferimento alle guide dettagliate riportate di seguito che descrivono l’intero flusso di onboarding. Per i problemi non risolti dalle guide, puoi contattare `llmo-at-edge@adobe.com`.

Requisiti per il team IT/CDN:

* Aggiungi l’agente utente `*AdobeEdgeOptimize/1.0*` all’elenco Consentiti nel file robots.txt del sito o nelle regole di gestione del traffico da bot.
* Assicurati che le pagine non siano bloccate a livello di dominio o CDN.
* Aggiungere le regole di indirizzamento per l’ottimizzazione della rete Edge nella CDN.
* Se la rete CDN dispone di regole di WAF o Bot Manager, inserire nell&#39;elenco Consentiti l&#39;agente utente `*AdobeEdgeOptimize/1.0*`. Se è necessaria una verifica aggiuntiva, configurare l&#39;intestazione `x-edgeoptimize-fetcher-key`. Ogni guida BYOCDN riportata di seguito include i passaggi necessari.
* Confermare l’indirizzamento dell’ottimizzazione della rete Edge nell’interfaccia di LLM Optimizer.

Il diagramma seguente illustra il flusso delle richieste in una configurazione BYOCDN con Ottimizza in Edge:

![Flusso di richieste BYOCDN](/help/assets/optimize-at-edge/byocdn-request-flow.png)

>[!IMPORTANT]
>Il routing deve essere configurato nel CDN esterno (il CDN più vicino al client). Se disponi di più CDN, l’indirizzamento può essere eseguito solo sul CDN esterno.

Per una guida al processo di configurazione, seleziona il tuo provider CDN e segui la guida alla configurazione corrispondente. Tieni presente che questi esempi devono essere adattati alla tua configurazione live effettiva. È consigliabile applicare prima le modifiche negli ambienti inferiori.

### Guide per la configurazione della CDN

| Fornitore CDN | Tipo | Guida |
|---|---|---|
| CDN gestita da AEM Cloud Service (Fastly) | Gestito da Adobe | [Vedi guida alla configurazione](/help/dashboards/optimize-at-edge/aemcs-managed-cdn.md) |
| Fastly (BYOCDN) | CDN propria (BYOCDN) | [Vedi guida alla configurazione](/help/dashboards/optimize-at-edge/fastly-byocdn.md) |
| Akamai (BYOCDN) | CDN propria (BYOCDN) | [Vedi guida alla configurazione](/help/dashboards/optimize-at-edge/akamai-byocdn.md) |
| Cloudflare (BYOCDN) | CDN propria (BYOCDN) | [Vedi guida alla configurazione](/help/dashboards/optimize-at-edge/cloudflare-byocdn.md) |
| CloudFront (BYOCDN) | CDN propria (BYOCDN) | [Vedi guida alla configurazione](/help/dashboards/optimize-at-edge/cloudfront-byocdn.md) |

>[!NOTE]
>
>Se il tuo provider CDN non è tra quelli qui elencati o se il tuo dominio o e-mail non sono presenti nell’interfaccia di LLM Optimizer, contatta `llmo-at-edge@adobe.com` per richiedere assistenza nell’onboarding. Una volta completate le configurazioni, puoi implementare i suggerimenti per le opportunità di ottimizzazione nella rete Edge in LLM Optimizer.

Tutte le guida alla configurazione della CDN riportate qui sopra includono i passaggi dettagliati per la verifica finale, che dovrai seguire per accertarti che il traffico da IA agentica sia indirizzato correttamente e che il traffico da persone non sia interessato da alcuna modifica.

## Opportunità

Nella tabella seguente sono presentate le opportunità che possono migliorare l’esperienza web agentica e che sono supportate dall’ottimizzazione nella rete Edge.

| Opportunità | Tipo | Identificazione automatica | Suggerimento automatico | Ottimizzazione automatica |
|---------|----------|----------|----------|----------|
| [Ripristina Visibilità dei contenuti](/help/dashboards/opportunities/recover-content-visibility.md) | GEO tecnica | Rileva le pagine in cui i contenuti critici sono nascosti dagli agenti IA. Mostra gli URL interessati e i contenuti previsti che possono essere recuperati. | Evidenzia i contenuti che possono essere resi disponibili per gli agenti IA e consiglia di abilitare il pre-rendering per le pagine. | Fornisce al traffico da IA agentica un’istantanea HTML completamente sottoposta a rendering e ottimizzata per l’IA che recupera i contenuti precedentemente nascosti. |
| [Arricchisci pagine dettagli prodotto](/help/dashboards/opportunities/enrich-product-detail-pages.md) | GEO tecnica | Per le vetrine di Adobe Commerce, confronta i dati del catalogo completo con quelli a cui gli agenti AI possono accedere in ogni pagina dei dettagli del prodotto; mette in evidenza delle PDP in cui varianti, specifiche, attributi e campi catalogo correlati non sono presenti nel HTML visibile dall’agente, con priorità per il traffico agente. | Evidenzia le informazioni del catalogo recuperabili mancanti dalla vista agente e il motivo per cui sono importanti per l&#39;individuazione dei prodotti basata su LLM. | Distribuisce un’istantanea di HTML completamente pre-renderizzata e compatibile con l’intelligenza artificiale al traffico agente sul server Edge CDN, in modo che gli agenti ricevano un contesto di prodotto avanzato dal catalogo senza modifiche a CMS o al catalogo. |
| [Aggiungi riepiloghi descrittivi LLM](/help/dashboards/opportunities/add-llm-friendly-summaries.md) | Ottimizzazione dei contenuti | Identifica pagine a traffico elevato che non dispongono di riepiloghi concisi e punti chiave strutturati a livello di pagina o di sezione, rendendo più difficile la scansione e l’interpretazione da parte degli agenti di intelligenza artificiale. | Consiglia brevi riepiloghi e punti chiave generati dall’intelligenza artificiale basati sul contenuto esistente. | Inserisce riepiloghi e punti chiave nelle sezioni pertinenti di HTML, migliorando il modo in cui i modelli interpretano e descrivono il contenuto della pagina. |
| [Aggiungi domande frequenti pertinenti](/help/dashboards/opportunities/add-relevant-faqs.md) | Ottimizzazione dei contenuti | Identifica le pagine a traffico elevato prive di contenuti Q&amp;A strutturati allineati al set di prompt, rendendo più difficile per gli agenti AI far corrispondere le domande degli utenti alla pagina. | Suggerisce contenuti FAQ generati dall’intelligenza artificiale in linea con le intenzioni dell’utente e gli argomenti della pagina esistenti. | Inserisce i contenuti delle domande frequenti nell’HTML, rendendo le pagine più individuabili e pertinenti nelle risposte basate sull’IA. |
| [Semplifica contenuti complessi](/help/dashboards/opportunities/simplify-complex-content.md) | Ottimizzazione dei contenuti | Contrassegna le pagine con testi complessi che possono ostacolare la comprensione da parte dell’IA. | Fornisce versioni semplificate generate dall’IA di testi complessi mantenendone il significato originale. | Riscrive sezioni complesse della pagina, migliorando la leggibilità per l’IA. |
| [Aggiungi sommario](/help/dashboards/opportunities/add-table-of-contents.md) | GEO tecnica | Rileva le pagine prive di chiare intestazioni strutturali di organizzazione o navigazione, rendendo difficile per gli agenti AI analizzare e mappare il contenuto alle query degli utenti. | Suggerisce un sommario strutturato con intestazioni collegate ad ancoraggio che riflettano le sezioni principali della pagina. | Inserisce un sommario in HTML, migliorando la struttura della pagina in modo che i modelli AI possano estrarre, mappare e citare più facilmente le sezioni pertinenti. |
| [Aggiungi riepiloghi di trascrizioni multimediali](/help/dashboards/opportunities/add-multimedia-transcript-summaries.md) | Ottimizzazione dei contenuti | Identifica le pagine in cui le informazioni chiave sono incorporate in video o altri supporti senza trascrizioni o riepiloghi leggibili automaticamente, rendendo difficile l’utilizzo di tali contenuti per gli agenti di intelligenza artificiale. Mostra gli URL interessati e il testo consigliato. | Raccomanda riepiloghi di trascrizioni generati dall’intelligenza artificiale basati sui media e sulla pagina. | Inserisce i riepiloghi delle trascrizioni in HTML in modo che il traffico agente riceva testo leggibile da un computer (ad esempio, vicino al video rilevante). |

### Strumenti aggiuntivi

L&#39;estensione del browser [AI Visibilità dei contenuti Checker](https://chromewebstore.google.com/detail/ai-content-visibility-che/jbjngahjjdgonbeinjlepfamjdmdcbcc) mostra la quantità di contenuti della pagina Web a cui i moduli LLM possono accedere e ciò che rimane nascosto. Progettata come strumento diagnostico indipendente e gratuito, non richiede alcuna licenza né configurazione del prodotto.

Con un solo clic, puoi valutare la leggibilità automatica di qualsiasi sito. Puoi visualizzare un confronto affiancato tra ciò che vedono gli agenti IA rispetto a ciò che vedono gli utenti, e stimare quanto contenuto potrebbe essere recuperato utilizzando LLM Optimizer. Consulta la pagina [L’IA può leggere il tuo sito web?](https://business.adobe.com/blog/introducing-the-llm-optimizer-chrome-extension) per ulteriori informazioni.

## Opportunità dettagliate

Nelle sezioni seguenti, puoi visualizzare ulteriori dettagli per ogni opportunità supportata dalla funzione Ottimizzazione nella rete Edge.

### Recupera visibilità dei contenuti

Questa opportunità segnala le pagine in cui il contenuto chiave risulta nascosto per gli agenti IA a causa del rendering lato client. Per ogni pagina identificata, vengono mostrati mostri esattamente i contenuti che l’agente IA non può “vedere”, evidenzia le lacune di visibilità e consente di applicare direttamente le modifiche necessarie per recuperare i contenuti nascosti. Quando implementi questa opportunità con Ottimizzazione nella rete Edge, agli agenti utente LLM viene presentata una versione della pagina pre-renderizzata e ottimizzata per l’IA, affinché possano accedere all’intero contesto senza eseguire alcun codice Javascript.
In questo modo la pagina sarà completamente visibile agli agenti IA. Ulteriori miglioramenti vengono poi applicati all’HTML pre-renderizzato.

>[!IMPORTANT]
>Questa funzionalità di pre-rendering si applica in automatico a tutte le opportunità presentate di seguito quando vengono implementate con la funzione Ottimizzazione nella rete Edge, affinché la pagina sia completamente visibile agli agenti IA.

Per una procedura dettagliata, i passaggi di distribuzione e le domande frequenti relative al dashboard, vedere [Recupera Visibilità dei contenuti](/help/dashboards/opportunities/recover-content-visibility.md).

### Arricchisci pagine dettagli prodotto

Questa opportunità è rivolta alle pagine dei dettagli dei prodotti Adobe Commerce in cui gli acquirenti vedono il contesto completo del prodotto attraverso esperienze di vetrina interattive, ma gli agenti di intelligenza artificiale ricevono solo un’istantanea superficiale di HTML. L’agente catalogo confronta il catalogo Commerce autorevole con il PDP visibile dall’agente, elenca ogni lacuna significativa (ad esempio varianti o specifiche che non vengono mai visualizzate in HTML statico) e consente di distribuire una risposta Edge di solo bot che ripristina la parità per i crawler LLM senza modificare i record del catalogo o l’interfaccia utente umana.

Per informazioni dettagliate sulla dashboard, passaggi di distribuzione e domande frequenti, vedere [Arricchire le pagine dei dettagli del prodotto](/help/dashboards/opportunities/enrich-product-detail-pages.md).

### Aggiungi riepiloghi ottimizzati per gli LLM

Questa opportunità identifica pagine con traffico elevato che possono trarre vantaggio da riepiloghi concisi e punti chiave strutturati in modo che i moduli LLM possano comprendere rapidamente le attestazioni sulla pagina. Per ogni pagina, rileva dove è più necessario un riepilogo e propone riepiloghi generati dall’intelligenza artificiale (e punti chiave, se pertinenti) a livello di pagina o di sezione, basati sul contenuto esistente. Quando distribuisci con Ottimizza in Edge, tale contenuto viene inserito in HTML che gli agenti di intelligenza artificiale recuperano, migliorando la precisione con cui il brand viene rappresentato nelle risposte di intelligenza artificiale.

Per ulteriori dettagli su questa opportunità, consulta [Aggiungi riepiloghi compatibili con LLM](/help/dashboards/opportunities/add-llm-friendly-summaries.md).

### Aggiungi domande frequenti pertinenti

Questa opportunità contrassegna le pagine a traffico elevato in cui contenuti aggiuntivi di domande e risposte potrebbero corrispondere meglio alle intenzioni degli utenti e alle richieste nell’individuazione basata sull’intelligenza artificiale. Per ogni pagina, propone blocchi di domande frequenti generati dall’intelligenza artificiale associati al set di prompt e al contenuto della pagina. Con Ottimizza in Edge, queste domande frequenti vengono inserite in HTML, rendendo la pagina più intuitiva e aumentando la probabilità che le risposte di IA riflettano direttamente la tua guida.

Per una procedura dettagliata, i passaggi di distribuzione e le domande frequenti relative a un dashboard, vedere [Aggiungi domande frequenti rilevanti](/help/dashboards/opportunities/add-relevant-faqs.md).

### Semplifica contenuti complessi

Questa opportunità trova le pagine con paragrafi lunghi e complessi che potrebbero non essere compresi correttamente dall’IA. Per ogni pagina che supera le soglie di leggibilità, vengono creati contenuti generati dall’IA più semplici e facili da analizzare, mantenendo il significato originale. Quando viene implementata sulla rete Edge, il contenuto semplificato viene presentato al traffico da IA agentica e consente agli LLM di interpretare e riepilogare i contenuti in modo più fedele.

Per informazioni dettagliate, passaggi di distribuzione e domande frequenti, vedere [Semplificare contenuti complessi](/help/dashboards/opportunities/simplify-complex-content.md).

### Aggiungi sommario

Questa opportunità rileva pagine difficili da navigare per gli agenti di intelligenza artificiale perché le intestazioni e la struttura della sezione non sono chiare o mancanti. Per ogni pagina interessata, propone un sommario strutturato con voci collegate a un ancoraggio allineate alle sezioni principali. Quando distribuisci con Ottimizza in Edge, tale sommario viene inserito in HTML, in modo che i modelli possano mappare in modo più affidabile le query dell’utente nelle parti giuste della pagina e citarle.

Per una procedura dettagliata, i passaggi di distribuzione e le linee guida per l&#39;accesso anticipato, vedere [Aggiungi sommario](/help/dashboards/opportunities/add-table-of-contents.md).

### Aggiungi riepiloghi di trascrizioni multimediali

Questa opportunità esegue il targeting delle pagine in cui le informazioni importanti risiedono solo all’interno della riproduzione video, senza trascrizioni o riepiloghi di testo che gli agenti di intelligenza artificiale possono leggere. Per ogni pagina, consiglia le trascrizioni generate dall’intelligenza artificiale e brevi riassunti dei punti chiave dei media. Con Ottimizza in Edge, quei riepiloghi vengono aggiunti al HTML come testo leggibile al computer, in modo che gli agenti possano utilizzare la stessa sostanza che i visitatori umani ottengono guardando il video.

Per informazioni dettagliate sulla dashboard, i passaggi di distribuzione e le domande frequenti, vedere [Aggiungi riepilogo delle trascrizioni multimediali](/help/dashboards/opportunities/add-multimedia-transcript-summaries.md).

## Ottimizzazione automatica sulla rete Edge

Per ogni opportunità, puoi visualizzare in anteprima e live, modificare e implementare, le ottimizzazioni sulla rete Edge, nonché ripristinare la versione precedente.

>[!VIDEO](https://video.tv.adobe.com/v/3477992/?captions=ita&learn=on&enablevpops)

### Anteprima

**Anteprima** consente di visualizzare l’impatto di un suggerimento prima che venga pubblicato. Presenta in modalità affiancata le differenze tra la pagina corrente e la versione risultante dall’ottimizzazione IA, una volta applicato il suggerimento. Questa vista si basa sulla stessa logica utilizzata da Ottimizzazione sulla rete Edge per il traffico live, ma applicata in modalità di anteprima isolata. Non influisce sul traffico live, in quanto si tratta di una simulazione di sola lettura a scopo di revisione.

![Anteprima](/help/assets/optimize-at-edge/preview.png)

### Modifica

**Modifica** consente di perfezionare o riscrivere completamente il suggerimento generato in automatico prima di implementarlo. Invece di accettare il suggerimento, puoi mantenere il controllo completo tramite il flusso di lavoro di modifica. Questa vista mostra le modifiche proposte in un editor strutturato, dove puoi modificare il testo per soddisfare meglio l’intento originale. Una volta implementata, la versione modificata verrà quindi trasmessa agli agenti IA.

![Modifica](/help/assets/optimize-at-edge/edit.png)

### Implementa

**Implementa** pubblica i suggerimenti selezionati in modo che le esperienze ottimizzate possano essere trasmesse dalla rete Edge agli agenti IA. Se la CDN è completamente indirizzata, in genere tutte le pagine del dominio vengono pubblicate con le nuove modifiche in pochi minuti. Se l’indirizzamento è stato configurato solo per alcuni percorsi, solo le pagine inserite nell’elenco consentiti vengono pubblicate con le ottimizzazioni.

![Implementazione](/help/assets/optimize-at-edge/deploy.png)

### Visualizza live

**Visualizza live** ti consente di verificare che l’ottimizzazione sia live e funzioni come previsto per il traffico da IA agentica, offrendo una visualizzazione a cui altrimenti sarebbe difficile accedere. Puoi visualizzare la pagina live in Suggerimenti risolti, che esegue il rendering della pagina come mostrato agli agenti IA.

![Visualizza live](/help/assets/optimize-at-edge/view-live.png)

### Rollback

Il rollback ripristina in modo sicuro un’ottimizzazione implementata in precedenza. In genere, la versione della pagina solo per l’IA viene ripristinata allo stato precedente in pochi minuti, rendendo sicuro testare diverse ottimizzazioni in caso di necessità.

![Rollback](/help/assets/optimize-at-edge/rollback.png)

## Risorse aggiuntive

Per ulteriori dettagli sulla funzionalità Ottimizza in Edge, vedi la seguente playlist [LLM Optimizer — Ottimizza in Edge](https://www.youtube.com/playlist?list=PLzbVcr6JHocVSMWBCaCw4xxjQ_VFVvFh0).

## Domande frequenti

D: I clienti di prova possono provare a ottimizzare in Edge?

Sì, i clienti di prova possono accedere a un’opportunità di ottimizzazione e distribuirla per un massimo di 10 pagine. Per impostazione predefinita, l’opportunità è Recover Visibilità dei contenuti, che consente agli agenti di intelligenza artificiale di accedere alla versione completa del contenuto della pagina.

D. Per quali tipi di LLM viene eseguito il targeting con l’ottimizzazione nella rete Edge?

Puoi definire l’elenco degli agenti utente di cui eseguire il targeting durante il processo di onboarding.

<!--
Q. What does "Edge" in Optimize at Edge mean?

In our context, "Edge" means that the optimization is applied at the CDN layer and not inside your CMS.

Q. Why does this optimization require a CDN?

The CDN is where the optimized version of the page is assembled and delivered to AI agents. We leverage the CDN to ensure your origin CMS remains unchanged. This separation lets you improve LLM visibility without altering your existing publishing workflows.
-->

D. Cosa succede se non ho ancora effettuato l’onboarding per l’otttimizzazione nella rete Edge?

Se fai clic su **Implementa ottimizzazioni** prima aver completato la configurazione richiesta, non verrà applicata alcuna modifica al tuo sito. Viene invece visualizzata una finestra di dialogo a comparsa in cui ti verrà richiesto di contattare il nostro team all’indirizzo `llmo-at-edge@adobe.com` per ricevere assistenza sull’onboarding. Fino a quando l’onboarding non è completato, puoi ancora esplorare le opportunità e i suggerimenti rilevati, ma il flusso di lavoro di implementazione con un solo clic rimarrà inattivo.

D. Cosa succede quando i contenuti vengono aggiornati all’origine?

La versione ottimizzata della pagina viene fornita dalla cache, a meno che la pagina di origine sottostante non sia cambiata. Tuttavia, quando l’origine cambia per **Recupera visibilità dei contenuti**, il sistema si aggiorna automaticamente in modo che gli agenti IA ricevano sempre i contenuti più aggiornati. Questo perché vengono utilizzate impostazioni TTL (Time To Live) ridotte per la cache, nell’ordine di pochi minuti, in modo che ogni aggiornamento dei contenuti sul tuo sito attivi una nuova ottimizzazione all’interno di tale intervallo. Per opportunità di contenuto come **Aggiungi riepiloghi ottimizzati per gli LLM**, LLM Optimizer monitora la pagina di origine per rilevare eventuali modifiche. Se viene rilevata una modifica, l’ottimizzazione viene sospesa e contrassegnata per la revisione umana per evitare la deviazione del contenuto tra la pagina visibile dall’agente e la pagina visibile dall’uomo.
<!--As there is no universal TTL that fits every site, we can configure this TTL based on your cache invalidation rules to ensure both systems stay in sync.-->

D. L’ottimizzazione nella rete Edge è valida solo per i siti che utilizzano il servizio Adobe Edge Delivery (EDS)?

No. L’ottimizzazione nella rete Edge è indipendente dalla CDN e funziona con qualsiasi architettura front-end, non solo quelle implementate sullo Stack EDS di Adobe.

D. In che modo il pre-rendering dell’ottimizzazione nella rete Edge è diverso dal rendering lato server tradizionale (SSR)?

Entrambi risolvono problemi diversi e possono essere utilizzati insieme. Il rendering SSR tradizionale esegue il rendering dei contenuti lato server, ma non include i contenuti caricati successivamente nel browser. Il pre-rendering dell’ottimizzazione nella rete Edge acquisisce la pagina dopo il caricamento di JavaScript e dei dati lato client, generando la versione completamente assemblata sul lato della CDN. Il rendering SSR si concentra sul miglioramento dell’esperienza utente, mentre l’ottimizzazione nella rete Edge migliora l’esperienza web per gli LLM.

D. Recover Visibilità dei contenuti (pre-rendering) è un cloaking? Sembra che agli agenti di intelligenza artificiale venga distribuita una versione diversa della pagina.

No. Il pre-rendering assicura che gli agenti AI possano visualizzare gli stessi contenuti già visualizzati dai visitatori e dai bot SEO. Molti siti caricano contenuti significativi con JavaScript, che i tipici agenti di intelligenza artificiale non eseguono, pertanto gli agenti possono perdere parti importanti della pagina. Il pre-rendering produce un’istantanea statica che acquisisce il testo completo, in modo che gli agenti ricevano le stesse informazioni degli esseri umani e dei motori di ricerca. **ripristina** la parità del contenuto per i moduli LLM; non aggiunge né modifica il contenuto effettivo.

D. E per quanto riguarda altre opportunità di contenuto, come l’aggiunta di riepiloghi compatibili con LLM, dove viene visualizzata una nuova copia nella pagina fornita agli agenti? È un cloaking?

No. L’ottimizzazione in Edge non introduce informazioni a cui gli utenti umani e i crawler SEO non possono accedere. Il servizio riorganizza o riepiloga i contenuti già esistenti nella pagina in modo che gli agenti di intelligenza artificiale possano interpretarli più facilmente. Quando qualcuno segue un collegamento da una risposta AI al tuo sito, può comunque trovare le stesse informazioni sottostanti sulla pagina live.

D. Cosa succede se vengono implementate ottimizzazioni per alcuni URL nel dominio ma non per tutti?

Vengono modificati solo gli URL esplicitamente ottimizzati. Per gli URL per i quali sono state implementate le opportunità, gli agenti IA ricevono la versione ottimizzata. Per gli URL per i quali non sono state implementate opportunità, il servizio effettua semplicemente il proxy della pagina originale così com’è, senza applicare modifiche o senza memorizzarla nel livello della cache di ottimizzazione. In questo modo puoi implementare selettivamente specifiche ottimizzazioni senza alcun impatto sul resto del sito.
