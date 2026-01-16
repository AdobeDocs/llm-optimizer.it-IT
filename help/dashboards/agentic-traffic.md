---
title: Traffico agente
description: Scopri come utilizzare la dashboard Traffico agente per vedere come gli agenti di IA interagiscono con il tuo sito.
feature: Agentic Traffic
source-git-commit: 2993f840c7451adeccf4f11a0132b91a9bc81803
workflow-type: tm+mt
source-wordcount: '1302'
ht-degree: 0%

---


# Traffico agente {#agentic-traffic}

Il dashboard Traffico agente mostra come gli agenti di intelligenza artificiale (crawler e chatbot) interagiscono con il sito. Utilizzando questa vista puoi tenere traccia del numero totale di richieste e delle metriche generali relative alle prestazioni. Puoi anche visualizzare la distribuzione del traffico tra mercati, categorie, pagine e agenti. I dati utilizzati da questo dashboard provengono dai registri CDN, pertanto è necessario configurare **Inoltro dei registri CDN** per visualizzare le metriche. Sono inoltre disponibili filtri personalizzabili per aiutarti a perfezionare i dati visualizzati.

![Distribuzione traffico](/help/dashboards/assets/ag-main.png)

In questa pagina sono disponibili i dettagli riportati di seguito.

* [Filtri](#filters)
* [Configurazione CDN](#cdn-setup)
* [Distribuzione traffico](#traffic-distribution)
* [Tendenze traffico agente](#agentic-trends)
* [Spostamenti superiore e inferiore](#top-bottom-movers)
* [Analisi delle prestazioni dell’agente utente e dell’URL](#user-url-performance)

## Inoltro registro CDN {#cdn-setup}

Senza **inoltro del registro CDN**, il dashboard Traffico agente è vuoto. Per visualizzare le interazioni agente, devi configurare **Inoltro del registro CDN**.  Al primo accesso, verrà visualizzato un messaggio come mostrato nell&#39;immagine seguente.

![Configurazione rete CDN](/help/dashboards/assets/ag-log-forward1.png)

Seleziona **Vai alla configurazione** e passerai automaticamente alla scheda **Configurazione CDN** del [dashboard di configurazione del cliente](/help/dashboards/customer-configuration.md).

![Configurazione rete CDN integrata](/help/dashboards/assets/ag-log-forward2.png)

In questa scheda, seleziona **CDN integrato**. Viene visualizzata la finestra del provider CDN.

<!-- [CDN Provider](/help/dashboards/assets/ag-log-forward3.png)-->
Nella finestra **Provider CDN integrato**:

1. Seleziona il provider CDN (ad esempio Akamai, Fastly, Fastly, Fastly, AWS Cloudfront, Azure CDN, Cloudflare o Altro) gestito da Adobe.
2. Fai clic su **Onboard** per abilitare l&#39;inoltro del registro.

Se selezioni **Altro**, dovrai contattare llmo-now@adobe.com per assistenza.

Una volta attivati, i registri vengono acquisiti e la dashboard viene compilata con metriche quali interazioni totali dell’agente, tasso di successo, hit per mercato, analisi dell’agente utente e prestazioni a livello di URL.

LLM Optimizer acquisisce ed elabora solo un sottoinsieme di campi dai registri CDN. Anche se i nomi dei campi di registro non elaborati variano a seconda del provider CDN, vengono normalizzati e presentati come:

* URL (solo percorso)
* user_agent
* stato
* referer
* host
* Ttfb (tempo al primo byte)
* cdn_provider

Questi campi normalizzati vengono esposti tramite la vista agente. Nel dashboard [Traffico di riferimento](/help/dashboards/referral-traffic.md), i registri CDN vengono utilizzati per visualizzare le metriche di hit pagina. Non viene elaborata o memorizzata alcuna informazione personale identificabile (PII, Personally Identifiable Information) in nessuna fase dell’acquisizione del registro CDN o della successiva gestione dei dati.

## Filtri {#filters}

Nella parte superiore della pagina, puoi applicare i filtri per perfezionare la visualizzazione. I filtri scelti influiranno su **tutte** le sezioni presenti nel dashboard. Puoi personalizzare quanto segue:

* **Intervallo date** - Selezionare l&#39;intervallo di tempo per i dati visualizzati. Ad esempio, le ultime 4 settimane. Puoi anche personalizzare il periodo di tempo selezionando l&#39;opzione **Settimane personalizzate**.
* **Categoria** - Filtra i risultati visualizzati in base a categorie predefinite o personalizzate.
* **Piattaforma** - Scegli quale motore di intelligenza artificiale analizzare.
* **Tipo di agente** - Filtra in base al tipo di agente di IA che ha interagito con il sito. Puoi filtrare tra crawler, chatbot o tutti gli agenti.
* **Percentuale di successo** - Filtra in base alla qualità dell&#39;interazione (alta, media o bassa). Questa metrica rappresenta la percentuale di richieste HTTP riuscite, incluse sia le risposte dirette riuscite (codici di stato 2xx) che i reindirizzamenti (codici di stato 3xx).
* **Tipo di contenuto** - Visualizza l&#39;interazione agente per diversi tipi di contenuto, ad esempio HTML, PDF e così via.

Dopo aver selezionato il filtro desiderato, fare clic su **Applica filtri** per applicare la selezione al dashboard.

## Distribuzione traffico {#traffic-distribution}

La vista Distribuzione traffico mostra come il traffico dell’agente viene distribuito tra mercati, categorie e tipi di pagina. Di conseguenza, questa visualizzazione consente di determinare quali aree geografiche, aree di prodotto o formati di contenuto sono più frequentemente utilizzati dagli agenti di intelligenza artificiale durante l’interazione con il sito.

![Distribuzione traffico](/help/dashboards/assets/ag-main.png)

Nella parte superiore della pagina è necessario conoscere tre metriche chiave:

* **Interazioni agente** - Questa metrica rappresenta il numero totale di richieste effettuate dagli agenti di IA al sito Web. Questo include tutto il traffico proveniente da motori di ricerca, chatbot e altro traffico non umano.
* **Percentuale di successo** - Questa metrica rappresenta la percentuale di richieste HTTP riuscite, incluse sia le risposte dirette che i reindirizzamenti.
* **TTFB medio** - Time To First Byte (TTFB) misura il tempo necessario per ricevere il primo byte di dati dal server. Il valore medio è ponderato in base al numero di richieste che restituiscono ciascun codice ed esclude le richieste che hanno prodotto risposte 5xx. Valori più bassi indicano tempi di risposta del server più rapidi.

Gli indicatori di tendenza per ciascuna metrica chiave mostrano le modifiche di questi valori nel tempo rispetto al periodo precedente.

## Tendenze traffico agente {#agentic-trends}

Utilizza il grafico delle tendenze del traffico agente per tenere traccia dei totali settimanali degli hit di successo, di errore e complessivi. Di conseguenza, puoi monitorare le modifiche dell’attività e delle prestazioni degli agenti nel tempo. Puoi anche passare il cursore del mouse lungo il grafico per vedere l’evoluzione dei dati nell’intervallo di tempo settimanale.

![Tendenze traffico agente](/help/dashboards/assets/ag-trends.png)

## Spostamenti superiore e inferiore {#top-bottom-movers}

La vista Spostamenti in alto e in basso evidenzia gli URL con le modifiche più grandi, settimana dopo settimana, nel traffico agente: visite o hit dai sistemi di intelligenza artificiale che accedono al contenuto. **Primi spostamenti** mostra le pagine che acquistano visibilità o coinvolgimento, mentre **Ultimi spostamenti** rivela gli URL con i rifiuti più accentuati. Questo consente di identificare rapidamente quale contenuto ha una tendenza verso l’alto, che può richiedere attenzione e dove i modelli di individuazione basati sull’intelligenza artificiale si stanno spostando.

![Spostamenti superiore e inferiore](/help/dashboards/assets/movers.png)

## Analisi delle prestazioni dell’agente utente e dell’URL {#user-url-performance}

Le viste Agente utente e Analisi delle prestazioni URL forniscono ulteriori raggruppamenti di dati sul modo in cui crawler e chatbot interagiscono con il sito. Fai clic sulle schede seguenti per le descrizioni dettagliate.

![Analisi prestazioni URL e agente utente](/help/dashboards/assets/user-agent.png)

>[!BEGINTABS]

>[!TAB Analisi agente utente]

La tabella Analisi agente utente fornisce un raggruppamento del traffico per tipo di pagina e di agente (ad esempio, crawler e chatbot). In questo modo, è facile capire quali agenti di intelligenza artificiale strisciano su quali parti del sito. Contiene le seguenti categorie:

* **Tipo di pagina**: il tipo di pagina.
* **Tipo di agente** - Agente di IA che esegue la ricerca per indicizzazione della pagina, un crawler o un chatbot.
* **Hit** - Numero totale di richieste effettuate dagli agenti di IA per quel tipo di pagina specifico.

Puoi personalizzare le metriche da visualizzare facendo clic sul pulsante **Configura colonne**.

>[!TAB Analisi prestazioni URL]

La tabella Analisi delle prestazioni degli URL mostra una visualizzazione dettagliata dei singoli URL. Ciò include hit, agenti univoci, agente principale, tassi di successo e categorie. In questo modo puoi identificare pagine di alto valore, rilevare spazi vuoti di ricerca per indicizzazione e ottimizzare i contenuti per i motori di intelligenza artificiale. Gli URL sono classificati per volume di traffico. La tabella contiene le seguenti categorie:

* **URL** - L&#39;URL esaminato.
* **Totale riscontri** - Numero totale di richieste effettuate dagli agenti di IA all&#39;URL.
* **Agenti univoci** - Numero di agenti di IA diversi che hanno effettuato l&#39;accesso all&#39;URL.
* **Agente principale** - Agente di IA che ha generato il maggior traffico verso l&#39;URL.
* **Tipo di agente principale**: il tipo dell&#39;agente di IA che ha generato più traffico per questo URL.
* **Percentuale di successo** - Percentuale di richieste HTTP riuscite, incluse risposte dirette riuscite e reindirizzamenti.
* **Categoria**: la categoria che corrisponde maggiormente al contenuto della pagina.
* **TTFB medio (ms)** - Time To First Byte (TTFB) misura il tempo necessario per ricevere il primo byte di dati dal server (in millisecondi). Il valore medio è ponderato in base al numero di richieste che restituiscono ciascun codice ed esclude le richieste che hanno prodotto risposte 5xx. Valori più bassi indicano tempi di risposta del server più rapidi.
* **Codici di risposta** - Codici di stato HTTP osservati per l&#39;URL.

La tabella delle prestazioni degli URL contiene un campo di ricerca per l&#39;accesso rapido agli URL ed è possibile personalizzare le metriche visualizzate facendo clic sul pulsante **Configura colonne**. Puoi anche visualizzare ulteriori dettagli per ogni URL facendo clic sull&#39;icona **Dettagli** alla fine di ogni riga.

![Dettagli URL](/help/dashboards/assets/details.png)

La vista Dettagli URL fornisce una comprensione olistica delle prestazioni di una pagina, mostrando la frequenza con cui viene citata, la sensazione delle risposte AI in cui viene menzionata, gli argomenti e i prompt in cui viene visualizzata e le tendenze nel traffico agenziale e di riferimento nel tempo.

>[!ENDTABS]

In entrambe le tabelle è possibile utilizzare l&#39;opzione **Esporta** per scaricare il file .csv della tabella e condividere le informazioni con il team oppure includere le tabelle nel reporting esecutivo.
