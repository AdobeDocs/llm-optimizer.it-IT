---
title: Ottimizzazione nella rete Edge
description: Scopri come applicare le ottimizzazioni in LLM Optimizer direttamente a livello di CDN senza la necessità di apportare modifiche di authoring.
feature: Opportunities
source-git-commit: 23752b30294c3d467ca477b085aa521cad0f72ca
workflow-type: tm+mt
source-wordcount: '2172'
ht-degree: 85%

---


# Ottimizzazione nella rete Edge

Questa pagina fornisce una panoramica dettagliata su come applicare le ottimizzazioni a livello di CDN senza alcuna modifica all’authoring. Descrive il processo di onboarding, le opportunità di ottimizzazione disponibili e la procedura di ottimizzazione automatica nella rete Edge.

>[!NOTE]
>Questa funzionalità è attualmente in fase di accesso anticipato. Ulteriori informazioni su i programmi di accesso anticipato sono disponibili [qui](https://experienceleague.adobe.com/it/docs/experience-manager-cloud-service/content/release-notes/release-notes/release-notes-current#aem-beta-programs).

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

Con l’ottimizzazione nella rete Edge, sono supportate le opportunità che possono migliorare l’esperienza da IA agentica sul web. Ulteriori informazioni su ciascuna opportunità sono disponibili sia nella pagina della [Dashboard Opportunità](/help/dashboards/opportunities.md) che nella sezione Opportunità della pagina corrente.

## Onboarding

Per iniziare il processo di onboarding, contatta il team Adobe Account o il team FDE. Il tuo team IT o responsabile della CDN deve inoltre completare i prerequisiti e il processo di configurazione. Inoltre, puoi inviare un’e-mal all’indirizzo `llmo-at-edge@adobe.com` per ricevere ulteriore assistenza sull’onboarding.

Prerequisiti per l’onboarding per l’ottimizzazione nella rete Edge:

* Completamento del processo di onboarding in LLM Optimizer.
* Completamento del processo di inoltro dei registri per i registri della CDN.

Requisiti per il team IT/CDN:
* Aggiungi l&#39;agente utente `*AdobeEdgeOptimize/1.0*` al Inserisco nell&#39;elenco Consentiti di gestione del traffico da bot nel file robots.txt del sito o alle regole di gestione del traffico da bot.
* Assicurati che le pagine non siano bloccate a livello di dominio o CDN.
* Aggiungere le regole di indirizzamento per l’ottimizzazione della rete Edge nella CDN.
* Confermare l’indirizzamento dell’ottimizzazione della rete Edge nell’interfaccia di LLM Optimizer.

Per guidare il processo di configurazione, seleziona il provider CDN e segui la guida alla configurazione corrispondente. Tieni presente che questi esempi devono essere adattati alla tua configurazione live effettiva. È consigliabile applicare prima le modifiche negli ambienti inferiori.

### Guide alla configurazione CDN

| Fornitore CDN | Tipo | Guida |
|---|---|---|
| CDN gestito da AEM Cloud Service (Fastly) | Gestito da Adobe | [Visualizza guida all&#39;installazione](/help/dashboards/optimize-at-edge-aem-managed-cdn.md) |
| Fastly (BIOCDN) | Porta il tuo CDN | [Visualizza guida all&#39;installazione](/help/dashboards/optimize-at-edge-fastly-byocdn.md) |
| Akamai (BYOCDN) | Porta il tuo CDN | [Visualizza guida all&#39;installazione](/help/dashboards/optimize-at-edge-akamai-byocdn.md) |
| Cloudflare (BYOCDN) | Porta il tuo CDN | [Visualizza guida all&#39;installazione](/help/dashboards/optimize-at-edge-cloudflare-byocdn.md) |

>[!NOTE]
>Se il provider CDN non è elencato in precedenza o se il dominio o l&#39;e-mail non sono presenti nell&#39;interfaccia utente di LLM Optimizer, contatta `llmo-at-edge@adobe.com` per assistenza sull&#39;onboarding. Una volta completate le configurazioni, puoi implementare i suggerimenti per le opportunità di ottimizzazione nella rete Edge in LLM Optimizer.

Ogni guida alla configurazione della rete CDN riportata sopra include passaggi di verifica dettagliati alla fine per verificare che il traffico agenziale sia instradato correttamente e che il traffico umano non venga interessato.

## Opportunità

Nella tabella seguente sono presentate le opportunità che possono migliorare l’esperienza web agentica e che sono supportate dall’ottimizzazione nella rete Edge.

| Opportunità | Tipo | Identificazione automatica | Suggerimento automatico | Ottimizzazione automatica |
|---------|----------|----------|----------|----------|
| Recupera visibilità dei contenuti | GEO tecnica | Rileva le pagine in cui i contenuti critici sono nascosti dagli agenti IA. Mostra gli URL interessati e i contenuti previsti che possono essere recuperati. | Evidenzia i contenuti che possono essere resi disponibili per gli agenti IA e consiglia di abilitare il pre-rendering per le pagine. | Fornisce al traffico da IA agentica un’istantanea HTML completamente sottoposta a rendering e ottimizzata per l’IA che recupera i contenuti precedentemente nascosti. |
| Aggiungi riepiloghi ottimizzati per gli LLM | Ottimizzazione dei contenuti | Identifica pagine lunghe o complesse prive di riepiloghi concisi a livello di pagina o di sezione che risultano più difficili da scansionare e comprendere rapidamente per l’IA. | Consiglia brevi riepiloghi generati dall’IA a livello di pagina e di sezione, per l’acquisizione di contenuti chiave. | Inserisce i riepiloghi nelle sezioni HTML pertinenti, migliorando il modo in cui i modelli interpretano e descrivono i contenuti della pagina. |
| Aggiungi domande frequenti pertinenti | Ottimizzazione dei contenuti | Rileva le lacune nell’intento dei contenuti della pagina esistente che potrebbero trarre vantaggio dalle domande frequenti. | Suggerisce contenuti per le domande frequenti generati dall’IA in linea con l’intento utente e gli argomenti esistenti. | Inserisce i contenuti delle domande frequenti nell’HTML, rendendo le pagine più individuabili e pertinenti nelle risposte basate sull’IA. |
| Semplifica contenuti complessi | Ottimizzazione dei contenuti | Contrassegna le pagine con testi complessi che possono ostacolare la comprensione da parte dell’IA. | Fornisce versioni semplificate generate dall’IA di testi complessi mantenendone il significato originale. | Riscrive sezioni complesse della pagina, migliorando la leggibilità per l’IA. |

### Strumenti aggiuntivi

[Adobe LLM Optimizer: la tua pagina Web è citabile?](https://chromewebstore.google.com/detail/adobe-llm-optimizer-is-yo/jbjngahjjdgonbeinjlepfamjdmdcbcc) L’estensione Chrome mostra la quantità di contenuti della tua pagina web a cui gli LLM possono accedere e ciò che invece rimane nascosto. Progettata come strumento diagnostico indipendente e gratuito, non richiede alcuna licenza né configurazione del prodotto.

Con un solo clic, puoi valutare la leggibilità automatica di qualsiasi sito. Puoi visualizzare un confronto affiancato tra ciò che vedono gli agenti IA rispetto a ciò che vedono gli utenti, e stimare quanto contenuto potrebbe essere recuperato utilizzando LLM Optimizer. Consulta la pagina [L’IA può leggere il tuo sito web?](https://business.adobe.com/blog/introducing-the-llm-optimizer-chrome-extension) per ulteriori informazioni.

## Opportunità dettagliate

Nelle sezioni seguenti, puoi visualizzare ulteriori dettagli per ogni opportunità supportata dalla funzione Ottimizzazione nella rete Edge.

### Recupera visibilità dei contenuti

Questa opportunità segnala le pagine in cui il contenuto chiave risulta nascosto per gli agenti IA a causa del rendering lato client. Per ogni pagina identificata, vengono mostrati mostri esattamente i contenuti che l’agente IA non può “vedere”, evidenzia le lacune di visibilità e consente di applicare direttamente le modifiche necessarie per recuperare i contenuti nascosti. Quando implementi questa opportunità con Ottimizzazione nella rete Edge, agli agenti utente LLM viene presentata una versione della pagina pre-renderizzata e ottimizzata per l’IA, affinché possano accedere all’intero contesto senza eseguire alcun codice Javascript.
In questo modo la pagina sarà completamente visibile agli agenti IA. Ulteriori miglioramenti vengono poi applicati all’HTML pre-renderizzato.

>[!IMPORTANT]
>Questa funzionalità di pre-rendering si applica in automatico a tutte le opportunità presentate di seguito quando vengono implementate con la funzione Ottimizzazione nella rete Edge, affinché la pagina sia completamente visibile agli agenti IA.

### Aggiungi riepiloghi ottimizzati per gli LLM

Questa opportunità identifica le pagine che possono trarre vantaggio da riepiloghi concisi per aiutare gli LLM a comprendere rapidamente il contenuto della pagina. Per ogni pagina, l’opportunità rileva dove è più necessario un riepilogo e crea riepiloghi generati dall’IA a livello di pagina o di sezione. Quando vengono implementati con Ottimizzazione nella rete Edge, questi riepiloghi vengono inseriti nell’HTML recuperato dagli agenti IA, in modo da migliorare le probabilità di una descrizione più accurata del tuo contenuto.

### Aggiungi domande frequenti pertinenti

Questa opportunità segnala le pagine in cui contenuti aggiuntivi composti da domande e risposte potrebbero rispondere meglio all’intento degli utenti e ai prompt utilizzati nella ricerca basata sull’IA. Per ogni pagina, propone blocchi di domande frequenti generati dall’IA associati all’intento degli utenti e al contenuto della pagina. Con Ottimizzazione nella rete Edge, le domande frequenti vengono inserite nell’HTML, in modo da rendere la pagina maggiormente compatibile con l’IA e aumentare la probabilità che le risposte fornite dall’IA siano in linea con le tue indicazioni.

### Semplifica contenuti complessi

Questa opportunità trova le pagine con paragrafi lunghi e complessi che potrebbero non essere compresi correttamente dall’IA. Per ogni pagina che supera le soglie di leggibilità, vengono creati contenuti generati dall’IA più semplici e facili da analizzare, mantenendo il significato originale. Quando viene implementata sulla rete Edge, il contenuto semplificato viene presentato al traffico da IA agentica e consente agli LLM di interpretare e riepilogare i contenuti in modo più fedele.

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

## Domande frequenti

D. Per quali tipi di LLM viene eseguito il targeting con l’ottimizzazione nella rete Edge?

Puoi definire l’elenco degli agenti utente di cui eseguire il targeting durante il processo di onboarding.

<!--Q. What does "Edge" in Optimize at Edge mean?

In our context, "Edge" means that the optimization is applied at the CDN layer and not inside your CMS.

Q. Why does this optimization require a CDN?

The CDN is where the optimized version of the page is assembled and delivered to AI agents. We leverage the CDN to ensure your origin CMS remains unchanged. This separation lets you improve LLM visibility without altering your existing publishing workflows.-->

D. Cosa succede se non ho ancora effettuato l’onboarding per l’otttimizzazione nella rete Edge?

Se fai clic su **Implementa ottimizzazioni** prima aver completato la configurazione richiesta, non verrà applicata alcuna modifica al tuo sito. Viene invece visualizzata una finestra di dialogo a comparsa in cui ti verrà richiesto di contattare il nostro team all’indirizzo `llmo-at-edge@adobe.com` per ricevere assistenza sull’onboarding. Fino a quando l’onboarding non è completato, puoi ancora esplorare le opportunità e i suggerimenti rilevati, ma il flusso di lavoro di implementazione con un solo clic rimarrà inattivo.

D. Cosa succede quando i contenuti vengono aggiornati all’origine?

Distribuiamo la versione ottimizzata della pagina dalla cache, purché la pagina sorgente sottostante non sia cambiata. Tuttavia, quando l&#39;origine cambia per **Recupera Visibilità dei contenuti**, il sistema si aggiorna automaticamente in modo che gli agenti di IA ricevano sempre il contenuto più aggiornato. Questo perché utilizziamo impostazioni TTL (time-to-live) della cache ridotte (in ordine di minuti) in modo che qualsiasi aggiornamento del contenuto sul sito attivi una nuova ottimizzazione all’interno di tale finestra. Per opportunità di contenuto come **Aggiungi riepiloghi compatibili con LLM**, LLM Optimizer controlla la pagina di origine per eventuali modifiche. Se viene rilevata una modifica, l’ottimizzazione viene sospesa e contrassegnata per la revisione umana per evitare la deviazione del contenuto tra la pagina visibile dall’agente e la pagina visibile dall’uomo.
<!--As there is no universal TTL that fits every site, we can configure this TTL based on your cache invalidation rules to ensure both systems stay in sync.-->

D. L’ottimizzazione nella rete Edge è valida solo per i siti che utilizzano il servizio Adobe Edge Delivery (EDS)?

No. L’ottimizzazione nella rete Edge è indipendente dalla CDN e funziona con qualsiasi architettura front-end, non solo quelle implementate sullo Stack EDS di Adobe.

D. In che modo il pre-rendering dell’ottimizzazione nella rete Edge è diverso dal rendering lato server tradizionale (SSR)?

Entrambi risolvono problemi diversi e possono essere utilizzati insieme. Il rendering SSR tradizionale esegue il rendering dei contenuti lato server, ma non include i contenuti caricati successivamente nel browser. Il pre-rendering dell’ottimizzazione nella rete Edge acquisisce la pagina dopo il caricamento di JavaScript e dei dati lato client, generando la versione completamente assemblata sul lato della CDN. Il rendering SSR si concentra sul miglioramento dell’esperienza utente, mentre l’ottimizzazione nella rete Edge migliora l’esperienza web per gli LLM.

D. Cosa succede se distribuisco ottimizzazioni per alcuni URL nel mio dominio ma non per tutti?

Vengono modificati solo gli URL esplicitamente ottimizzati. Per gli URL con opportunità distribuite, gli agenti di IA ricevono la versione ottimizzata. Per gli URL senza opportunità distribuite, il nostro servizio effettua semplicemente il proxy della pagina originale così com’è, senza applicare modifiche o memorizzarla nel livello della cache di ottimizzazione. In questo modo puoi distribuire selettivamente le ottimizzazioni senza influire sul resto del sito.
