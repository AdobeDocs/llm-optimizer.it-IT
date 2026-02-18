---
title: Traffico da IA agentica
description: Scopri come utilizzare la dashboard Traffico da IA agentica per scoprire come gli agenti IA interagiscono con il tuo sito.
feature: Agentic Traffic
source-git-commit: 26926f3ed4df3a408b74b0208f0d1eb064b97d28
workflow-type: ht
source-wordcount: '1316'
ht-degree: 100%

---


# Traffico da IA agentica {#agentic-traffic}

La dashboard Traffico da IA agentica mostra come gli agenti IA, crawler e chatbot, interagiscono con il tuo sito.Utilizzando questa vista puoi tenere traccia del numero totale di richieste e delle metriche generali relative alle prestazioni.Puoi anche visualizzare la distribuzione del traffico tra mercati, categorie, pagine e agenti.I dati utilizzati da questa dashboard provengono dai registri CDN, pertanto devi configurare l’**inoltro del registro CDN** per visualizzare le metriche.Sono inoltre disponibili filtri personalizzabili per aiutarti a perfezionare i dati visualizzati.

![Distribuzione del traffico](/help/dashboards/assets/ag-main.png)

Questa pagina descrive quanto segue:

* [Filtri](#filters)
* [Configurazione CDN](#cdn-setup)
* [Distribuzione del traffico](#traffic-distribution)
* [Tendenze traffico da IA agentica](#agentic-trends)
* [Risultati migliori e peggiori](#top-bottom-movers)
* [Analisi prestazioni URL e agente utente](#user-url-performance)

## Inoltro del registro CDN {#cdn-setup}

Senza l’**inoltro del registro CDN**, la dashboard Traffico da IA agentica è vuota.Per visualizzare le interazioni agentiche, devi configurare l’**Inoltro del registro CDN**.Al primo accesso, visualizzerai un messaggio come mostrato nell’immagine seguente.

![Configurazione CDN](/help/dashboards/assets/ag-log-forward1.png)

Seleziona **Passa alla configurazione** per accedere automaticamente alla scheda **Configurazione CDN** della [dashboard Configurazione cliente](/help/dashboards/customer-configuration.md).

![Onboarding della configurazione CDN](/help/dashboards/assets/ag-log-forward2.png)

In questa scheda, seleziona **Effettua onboarding CDN**.Viene visualizzata la finestra del provider CDN.

<!-- [CDN Provider](/help/dashboards/assets/ag-log-forward3.png)-->
Nella finestra **Effettua onboarding provider CDN**:

1. Seleziona il provider CDN, ad esempio Akamai, Fastly gestito da Adobe, Fastly, Fastly, AWS Cloudfront, Azure CDN, Cloudflare o altri.
2. Fai clic su **Effettua onboarding** per abilitare l’inoltro del registro.

Se selezioni **Altro**, dovrai scrivere un’e-mail all’indirizzo llmo-now@adobe.com per ricevere assistenza.

Una volta attivata, i registri vengono acquisiti e la dashboard sarà popolata con metriche quali il totale delle interazioni degli agenti, il tasso di successo, gli hit per mercato, l’analisi dell’agente utente e prestazioni a livello di URL.

LLM Optimizer elabora un sottoinsieme di campi dai registri CDN. Anche se i nomi dei campi del registro non elaborati variano a seconda del provider CDN, vengono normalizzati e riportati come:

* URL (solo percorso)
* Agente utente
* Codice stato
* Intestazione referrer
* Intestazione host
* Tempo per il primo byte (TTFB)
* Metodo di richiesta
* Marca temporale
* Tipo di contenuto

Questi campi normalizzati vengono esposti tramite la vista agentica.Nella dashboard [Traffico da referral](/help/dashboards/referral-traffic.md), i registri CDN vengono utilizzati per mostrare le metriche degli hit pagina.Non viene elaborata o memorizzata alcuna informazione di identificazione personale (PII) in nessuna fase dell’acquisizione del registro CDN o della successiva gestione dei dati.

## Filtri {#filters}

Nella parte superiore della pagina, puoi applicare i filtri per definire la vista. I filtri scelti influiranno su **tutte** le sezioni presenti nella dashboard.Puoi personalizzare quanto segue:

* **Intervallo di date**: seleziona l’arco temporale per i dati visualizzati.Ad esempio, le ultime 4 settimane. Puoi anche personalizzare il periodo di tempo selezionando l’opzione **Settimane personalizzate**.
* **Categoria**: filtra i risultati visualizzati in base a categorie predefinite o personalizzate.
* **Piattaforma**: scegli quale motore di IA analizzare.
* **Tipo di agente**: filtra in base al tipo di agente IA che ha interagito con il tuo sito.Puoi filtrare per crawler, chatbot o tutti gli agenti.
* **Tasso di successo**: filtra in base alla qualità dell’interazione: alta, media o bassa.Questa metrica rappresenta la percentuale di richieste HTTP riuscite, incluse le risposte dirette (codici di stato 2xx) e i reindirizzamenti (codici di stato 3xx) riuisciti.
* **Tipo di contenuto**: visualizza l’interazione agentica per diversi tipi di contenuto, ad esempio HTML, PDF e così via.

Dopo aver selezionato il filtro, fai clic su **Applica filtri** per applicare la selezione alla dashboard.

## Distribuzione del traffico {#traffic-distribution}

La vista Distribuzione del traffico mostra in che modo il traffico dell’agente viene distribuito tra mercati, categorie e tipi di pagina. Di conseguenza, questa vista ti consente di determinare quali aree geografiche, aree di prodotto o formati di contenuto siano più frequentemente consultati dagli agenti IA quando interagiscono con il tuo sito.

![Distribuzione del traffico](/help/dashboards/assets/ag-main.png)

Nella parte superiore della pagina sono presenti tre metriche chiave da tenere d’occhio:

* **Interazioni agentiche**: questa metrica rappresenta il numero totale di richieste effettuate dagli agenti IA al tuo sito web.Include tutto il traffico proveniente da motori di ricerca, chatbot e altro traffico non umano.
* **Tasso di successo**: questa metrica rappresenta la percentuale di richieste HTTP riuscite, incluse le risposte dirette e gli reindirizzamenti riusciti.
* **TTFB medio**: il tempo per il primo byte misura il tempo necessario per la ricezione del primo byte di dati dal server.Il valore medio è ponderato in base al numero di richieste che restituiscono ciascun codice ed esclude le richieste che hanno generato risposte di tipo 5xx.Valori più bassi indicano tempi di risposta del server più rapidi.

Gli indicatori di tendenza per ciascuna metrica chiave mostrano come questi valori cambiano nel tempo rispetto al periodo precedente.

## Tendenze traffico da IA agentica {#agentic-trends}

Utilizza il grafico delle tendenze del traffico da IA agentica per tenere traccia dei totali settimanali degli hit riusciti, non riusciti e complessivi.Di conseguenza, puoi monitorare le modifiche di attività e prestazioni dell’agente nel tempo.Puoi anche passare il puntatore del mouse lungo il grafico per visualizzare l’evoluzione dei dati nell’arco temporale settimanale.

![Tendenze traffico da IA agentica](/help/dashboards/assets/ag-trends.png)

## Risultati migliori e peggiori {#top-bottom-movers}

La vista Risultati migliori e peggiori evidenzia gli URL che hanno registrato le maggiori variazioni nel traffico da IA agentica su base settimanale: visite o hit provenienti dai sistemi di IA che accedono ai tuoi contenuti. **Fattori principali** mostra le pagine che acquisicono visibilità o coinvolgimento, mentre **Fattori minori** rivela gli URL che hanno registrato i cali più drastici.Questo ti consente di identificare rapidamente quali contenuti sono in crescita, quali potrebbero richiedere attenzione e dove i pattern di individuazione basati sull’IA stanno cambiando.

![Risultati migliori e peggior](/help/dashboards/assets/movers.png)

## Analisi prestazioni URL e agente utente {#user-url-performance}

Le viste Analisi prestazioni URL e agente utente forniscono ulteriori raggruppamenti di dati sul modo in cui crawler e chatbot interagiscono con il tuo sito.Fai clic sulle schede seguenti per le descrizioni dettagliate.

![Analisi prestazioni URL e agente utente](/help/dashboards/assets/user-agent.png)

>[!BEGINTABS]

>[!TAB Analisi agente utente]

La tabella Analisi agente utente fornisce un raggruppamento del traffico per tipo di pagina e di agente, ad esempio, crawler rispetto a chatbot.In questo modo è più facile capire quali agenti IA stanno effettuando la ricercabilità per indicizzazione e di quali parti del tuo sito.Contiene le seguenti categorie:

* **Tipo di pagina**: il tipo di pagina.
* **Tipo di agente**: l’agente IA che effettua la ricercabilità per indicizzazione della pagina, un crawler o un chatbot.
* **Hit**: il numero totale di richieste effettuate dagli agenti IA per quel tipo di pagina specifico.

Puoi personalizzare le metriche da visualizzare facendo clic sul pulsante **Configura colonne**.

>[!TAB Analisi prestazioni URL]

La tabella Analisi prestazioni URL mostra una visualizzazione dettagliata dei singoli URL.Include hit, agenti univoci, agente principale, tassi di successo e categorie.In questo modo, puoi identificare le pagine di alto valore, rilevare le lacune nella ricercabilità per indicizzazione e ottimizzare i contenuti per i motori di IA.Gli URL sono classificati per volume di traffico.La tabella contiene le seguenti categorie:

* **URL**: URL esaminato.
* **Hit totali**: numero totale di richieste effettuate da agenti IA a questo URL.
* **Agenti univoci**: numero di agenti IA diversi che hanno effettuato l’accesso all’URL.
* **Agente migliore**: agente IA che ha generato maggior traffico per l’URL.
* **Tipo di agente migliore**: tipo di agente IA che ha generato maggior traffico per l’URL.
* **Tasso di successo**: percentuale di richieste HTTP completate, incluse risposte dirette e reindirizzamenti completati.
* **Categoria**: categoria che corrisponde maggiormente al contenuto della pagina.
* **TTFB medio (ms)**: il tempo per il primo byte (TTFB, Time To First Byte) misura il tempo necessario per la ricezione del primo byte di dati dal server (in millisecondi). Il valore medio è ponderato in base al numero di richieste che restituiscono ciascun codice ed esclude le richieste che hanno generato risposte di tipo 5xx.Valori più bassi indicano tempi di risposta del server più rapidi.
* **Codici di risposta**: codici di stato HTTP osservati per l’URL.

La tabella delle prestazioni URL contiene un campo di ricerca per l’accesso rapido agli URL. Per personalizzare le metriche visualizzate, fai clic sul pulsante **Configura colonne**. Puoi anche visualizzare ulteriori dettagli per ogni URL facendo clic sull’icona **Dettagli** alla fine di ogni riga.

![Dettagli URL](/help/dashboards/assets/details.png)

La vista Dettagli URL fornisce un quadro olistico delle prestazioni di una pagina: mostra la frequenza con cui viene citata, il sentiment delle risposte fornite dall’IA in cui viene menzionata, gli argomenti e i prompt in cui compare e le tendenze nel tempo in termini di traffico da IA agentica e da referral.

>[!ENDTABS]

In entrambe le tabelle puoi utilizzare l’opzione **Esporta** per scaricare la tabella `.csv` e condividere gli insight con il tuo team oppure includere le tabelle nei rapporti per il management.
