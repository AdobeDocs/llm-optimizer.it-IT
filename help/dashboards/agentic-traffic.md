---
title: Traffico agente
description: Panoramica dell’articolo.
source-git-commit: f92ca3eaa81d05135c65df60267280314c6e2d6f
workflow-type: tm+mt
source-wordcount: '955'
ht-degree: 0%

---


# Traffico agente {#agentic-traffic}

Il dashboard Traffico agente mostra come gli agenti di intelligenza artificiale (crawler e chatbot) interagiscono con il sito. Utilizzando questa vista puoi tenere traccia del numero totale di richieste e delle metriche generali relative alle prestazioni. Puoi anche visualizzare la distribuzione del traffico tra mercati, categorie, pagine e agenti. I dati utilizzati da questo dashboard provengono dai registri CDN, pertanto è necessario configurare **Inoltro dei registri CDN** per visualizzare le metriche. Sono inoltre disponibili filtri personalizzabili per aiutarti a perfezionare i dati visualizzati.

In questa pagina sono disponibili i dettagli riportati di seguito.

* [Filtri](#filters)
* [Configurazione CDN](#cdn-setup)
* [Distribuzione traffico](#traffic-distribution)
* [Tendenze traffico agente](#agentic-trends)
* [Spostamenti superiore e inferiore](#top-bottom-movers)
* [Analisi delle prestazioni dell’agente utente e dell’URL](#user-url-performance)

## Configurazione CDN {#cdn-setup}

Al primo accesso, il dashboard Traffico agente è vuoto. Per visualizzare le interazioni agente, devi configurare **Inoltro del registro CDN**. **Da oggi la configurazione della rete CDN è attiva in quickstart/onboarding?**

![Configurazione rete CDN](/help/dashboards/assets/ag-log-forward.png)

1. Seleziona il provider CDN (ad esempio Akamai, Fastly, Fastly, Fastly, AWS Cloudfront, Azure CDN, Cloudflare o Altro) gestito da Adobe.
2. Immetti un indirizzo e-mail di contatto principale.
3. Fai clic su **Richiedi attivazione** per abilitare l&#39;inoltro del registro.

Una volta attivati, i registri vengono acquisiti e la dashboard viene compilata con metriche quali interazioni totali dell’agente, tasso di successo, hit per mercato, analisi dell’agente utente e prestazioni a livello di URL.

## Filtri {#filters}

Nella parte superiore della pagina, puoi applicare i filtri per perfezionare la visualizzazione. I filtri scelti influiranno su **tutte** le sezioni presenti nel dashboard. Puoi personalizzare quanto segue:

* **Intervallo date** - Selezionare l&#39;intervallo di tempo per i dati visualizzati. Ad esempio, le ultime 4 settimane. Puoi anche personalizzare il periodo di tempo selezionando l&#39;opzione **Settimane personalizzate**.
* **Categoria** - Filtra i risultati visualizzati per categorie predefinite. Puoi anche aggiungere categorie personalizzate a questo campo (**SR**-come?).
* **Piattaforma** - Scegli quale motore di intelligenza artificiale analizzare.
* **Tipo di agente** - Filtra in base al tipo di agente di IA che ha interagito con il sito. Puoi filtrare tra crawler, chatbot o tutti gli agenti.
* **Percentuale di successo** - Filtra in base alla qualità dell&#39;interazione (alta, media o bassa). Questa metrica rappresenta la percentuale di richieste HTTP riuscite, inclusi sia le risposte dirette che i reindirizzamenti.
* **Tipo di contenuto** - Filtra per tipo di contenuto, HTML o txt.

Dopo aver selezionato il filtro desiderato, fare clic su **Applica filtri** per applicare la selezione al dashboard.

## Distribuzione traffico {#traffic-distribution}

La vista Distribuzione traffico mostra come il traffico dell’agente viene distribuito tra mercati, categorie e tipi di pagina. Di conseguenza, questa visualizzazione consente di determinare quali aree geografiche, aree di prodotto o formati di contenuto sono più frequentemente utilizzati dagli agenti di intelligenza artificiale durante l’interazione con il sito.

![Distribuzione traffico](/help/dashboards/assets/ag-main.png)

Nella parte superiore della pagina è necessario conoscere tre metriche chiave:

* **Interazioni agente** - Questa metrica rappresenta il numero totale di richieste effettuate dagli agenti di IA al sito Web. Questo include tutto il traffico proveniente da motori di ricerca, chatbot e altro traffico non umano.
* **Percentuale di successo** - Questa metrica rappresenta la percentuale di richieste HTTP riuscite, incluse sia le risposte dirette che i reindirizzamenti.
* **TTFB medio** - Time To First Byte (TTFB) misura il tempo necessario per ricevere il primo byte di dati dal server. Valori più bassi indicano tempi di risposta del server più rapidi.

Gli indicatori di tendenza per ciascuna metrica chiave mostrano le modifiche di questi valori nel tempo rispetto al periodo precedente.

## Tendenze traffico agente {#agentic-trends}

Utilizza il grafico delle tendenze del traffico agente per tenere traccia dei totali settimanali degli hit di successo, di errore e complessivi. Di conseguenza, puoi monitorare le modifiche dell’attività e delle prestazioni degli agenti nel tempo. Puoi anche passare il cursore del mouse lungo il grafico per vedere l’evoluzione dei dati nell’intervallo di tempo settimanale.

![Tendenze traffico agente](/help/dashboards/assets/ag-trends.png)

## Spostamenti superiore e inferiore {#top-bottom-movers}

Queste due metriche ordinano gli URL come segue:

* **Traslochi principali** - Gli URL con il maggiore aumento del traffico agente dalla settimana più vecchia a quella più recente.
* **Ultimi spostamenti** - URL con la diminuzione più significativa del traffico agente dalla settimana più vecchia a quella più recente.

## Analisi delle prestazioni dell’agente utente e dell’URL {#user-url-performance}

Le viste Agente utente e Analisi delle prestazioni URL forniscono ulteriori raggruppamenti di dati sul modo in cui crawler e chatbot interagiscono con il sito. Fai clic sulle schede seguenti per una descrizione dettagliata.

![Analisi prestazioni URL e agente utente](/help/dashboards/assets/user-agent.png)

>[!BEGINTABS]

>[!TAB Analisi agente utente]

La tabella Analisi agente utente fornisce un raggruppamento del traffico per tipo di pagina e di agente (ad esempio, crawler e chatbot). In questo modo, è facile capire quali agenti di intelligenza artificiale strisciano su quali parti del sito. Contiene le seguenti categorie:

* **Tipo di pagina**: il tipo di pagina.
* **Tipo di agente** - Agente di IA che esegue la ricerca per indicizzazione della pagina, un crawler o un chatbot.
* **Hit** - Numero totale di richieste effettuate dagli agenti di IA per quel tipo di pagina specifico.

Puoi anche utilizzare l&#39;opzione **Esporta** per scaricare la tabella .csv e condividere l&#39;analisi dell&#39;agente con il team o includerla nei report esecutivi.

>[!TAB Analisi prestazioni URL]

La tabella Analisi delle prestazioni degli URL mostra una visualizzazione dettagliata dei singoli URL. Ciò include hit, agenti univoci, agente principale, tassi di successo e categorie. In questo modo puoi identificare pagine di alto valore, rilevare spazi vuoti di ricerca per indicizzazione e ottimizzare i contenuti per i motori di intelligenza artificiale. Gli URL sono classificati per volume di traffico. La tabella contiene le seguenti categorie:

* **URL** - L&#39;URL esaminato.
* **Totale riscontri** - Numero totale di richieste effettuate dagli agenti di IA all&#39;URL.
* **Agenti univoci** - Numero di agenti di IA diversi che hanno effettuato l&#39;accesso all&#39;URL.
* **Agente principale** - Agente di IA che ha generato il maggior traffico verso l&#39;URL.
* **Tipo di agente principale**: il tipo dell&#39;agente di IA che ha generato più traffico per questo URL.
* **Percentuale di successo** - Percentuale di richieste HTTP riuscite, incluse risposte dirette riuscite e reindirizzamenti.
* **Categoria**: la categoria che corrisponde maggiormente al contenuto della pagina.

La tabella delle prestazioni URL contiene un campo di ricerca per l’accesso rapido agli URL. Inoltre, puoi utilizzare l&#39;opzione **Esporta** per scaricare la tabella .csv e condividere le informazioni con il tuo team oppure includere la tabella nei report manageriali.

>[!ENDTABS]
