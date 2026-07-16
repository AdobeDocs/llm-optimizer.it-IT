---
title: Integrazione di Adobe Analytics
description: Scopri come effettuare la connessione di Adobe Analytics con LLM Optimizer per misurare l’individuazione basata sull’intelligenza artificiale, il coinvolgimento sul sito e i risultati di business nella dashboard Traffico da referral.
feature: Referral Traffic
autotag-review: '2026-07-15T16:46:49.693Z'
TQID: 'https://experienceleague.adobe.com/H0p8HV2bf1KuKYqF1ByAF2BpGlb4YScsWDQU5mMkTRY'
product_v2:
  - id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2:
  - id: d1956731-2adb-4bb7-8301-2b239254ac72
subfeature_v2:
  - id: e69d5a42-0217-4ca5-9396-a9a826a170da
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: c2be0313-b3ae-45e0-b454-d20bf54b23f2
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 2705cf26faea9c09817bbdcec4b4c531552df7ba
workflow-type: tm+mt
source-wordcount: 950
ht-degree: 92%

---


# Integrazione di Adobe Analytics

L’integrazione di Adobe Analytics connette LLM Optimizer con i dati Adobe Analytics della tua organizzazione in modo da poter misurare come l’individuazione basata sull’intelligenza artificiale si traduce in un coinvolgimento reale del sito Web e in risultati di business. Al termine del processo di integrazione, i dati saranno disponibili nella dashboard **Traffico da referral**, nella scheda **Impatto aziendale**.

Collegando i dati di analisi con gli insight sulla visibilità dell’IA, LLM Optimizer consente di tenere traccia di:

* Coinvolgimento dell’utente nelle pagine basate sull’intelligenza artificiale.
* Segnali di conversione associati a percorsi di individuazione IA.
* Impatto delle prestazioni delle ottimizzazioni GEO.

Questa integrazione colma il divario tra la misurazione della visibilità dell’intelligenza artificiale e l’analisi delle prestazioni aziendali. Ora i team possono vedere non solo dove compare il brand nelle risposte dell’IA, ma anche cosa succede dopo l’arrivo degli utenti.

## Disponibilità {#availability}

>[!IMPORTANT]
>
>L’integrazione di Adobe Analytics è inclusa nell’offerta a pagamento di LLM Optimizer. I clienti che utilizzano la versione di prova gratuita non potranno connettere Adobe Analytics fino a quando non effettueranno l’aggiornamento a un’offerta a pagamento.

## Connettere Adobe Analytics alla dashboard Traffico da referral {#connect}

Il flusso di connessione inizia dalla dashboard [Traffico da referral](/help/dashboards/referral-traffic.md) come segue:

1. Apri la dashboard [Traffico da referral](/help/dashboards/referral-traffic.md). La vista predefinita è **Insight sul traffico**.

   ![Dashboard Traffico da referral, scheda Insight sul traffico](/help/dashboards/assets/aa-integration-01-referral-traffic-traffic-insights.png)

1. Seleziona la scheda **Impatto aziendale**. Se nessun fornitore della soluzione di analisi è connesso, viene visualizzato un banner: **Connettiti per visualizzare l’impatto aziendale** con **Connetti ad Analytics**.

   ![Scheda Impatto aziendale con Connetti ad Analytics](/help/dashboards/assets/aa-integration-02-business-impact-connect.png)

1. Seleziona **Connetti ad Analytics**. In questo modo, si apre la dashboard [Configurazione cliente](/help/dashboards/customer-configuration.md) nella scheda **Analytics**.

   ![Configurazione cliente, scheda Analytics](/help/dashboards/assets/aa-integration-03-analytics-tab.png)

1. In **Credenziali**, immetti l’**ID client** e il **Segreto client**, quindi seleziona **Verifica e continua**. Nota:

   * **Verifica e continua** è disponibile solo quando entrambi i campi sono compilati.
   * Dopo una verifica corretta, le suite di rapporti vengono caricate.
   * Utilizza **ID client** e **Segreto client** di un [account tecnico](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/) che ha accesso alla suite di rapporti necessaria.

   ![Credenziali di Analytics e Verifica e continua](/help/dashboards/assets/aa-integration-04-credentials.png)

1. In **Configurazione** scegli una **Suite di rapporti**.

   Quando è selezionata una suite di rapporti, LLM Optimizer carica le opzioni della **Dimensione URL pagina** disponibili per tale suite.

   ![Suite di rapporti selezionata e caricamento delle dimensioni](/help/dashboards/assets/aa-integration-05-report-suite.png)

1. Scegli una **Dimensione URL pagina** (elenco di dimensioni specifiche della suite), quindi seleziona **Salva e abilita**.

   * La **Dimensione URL della pagina** rimane disabilitata finché non viene selezionata una suite di rapporti e finché le dimensioni non vengono caricate.
   * **Salva e abilita** è disponibile solo dopo aver selezionato una dimensione URL pagina.

   ![Dimensione URL pagina e Salva e abilita](/help/dashboards/assets/aa-integration-06-page-url-dimension.png)

1. Dopo il salvataggio, la configurazione dovrebbe mostrare lo stato **Connesso**. Puoi tornare alla dashboard Traffico da referral tramite **Passa alla dashboard Traffico da referral**. In **Traffico da referral** nella scheda **Impatto aziendale**, lo stato dovrebbe essere **Connesso ad Adobe Analytics**.

   ![Connesso ad Adobe Analytics nella configurazione e Impatto aziendale](/help/dashboards/assets/aa-integration-07-connected.png)

### Dopo la connessione {#after-connect}

* LLM Optimizer esegue una retrocompilazione delle **ultime quattro settimane di calendario intere** e della **settimana di calendario corrente alla data attuale**.
* Dopo la retrocompilazione, i dati vengono aggiornati **ogni giorno** con un richiamo del **giorno precedente intero**.

>[!NOTE]
>
>Il completamento della retrocompilazione potrebbe richiedere un paio d’ore.

## Vedere Impatto aziendale in azione

La visibilità basata sull’intelligenza artificiale è solo una parte della storia. Per capire se gli sforzi di ottimizzazione stanno guidando i risultati di business, è necessario sapere cosa accade dopo che i visitatori arrivano sul sito.

Questo video introduce la vista **Impatto aziendale**, che combina LLM Optimizer con Adobe Analytics per mostrare come il traffico con riferimento all&#39;intelligenza artificiale si traduce in coinvolgimento, conversioni e ricavi, aiutandoti a misurare il valore effettivo della tua presenza all&#39;intelligenza artificiale.

>[!VIDEO](https://video.tv.adobe.com/v/3492511/?captions=ita&learn=on){transcript=true}

## Come funziona {#how-it-works}

### Configurazione

Durante la configurazione, definisci la suite di rapporti e la dimensione di pagina che LLM Optimizer utilizza per l’acquisizione di Adobe Analytics. La dimensione pagina può essere la mappatura `variables/page` standard o una `eVar` personalizzata, a seconda della suite di rapporti.

### Come viene identificato il traffico LLM

Il traffico originato da LLM viene identificato utilizzando il [Tipo di referrer - Strumenti di IA conversazionale](https://experienceleague.adobe.com/it/docs/analytics/components/dimensions/referrer-type#conversational-ai-tools) di Adobe Analytics.

### Dati acquisiti {#data-ingested}

I seguenti dati vengono acquisiti da LLM Optimizer:

**Dimensioni**

* Dominio referrer
* Tipo di referrer
* Paese
* Tipo di dispositivo
* Dimensione pagina selezionata

**Metriche**

* Visualizzazioni pagina
* Visite
* Visitatori
* Ingressi
* Uscite
* Mancati recapiti
* Visite a pagina singola
* Tempo trascorso
* Carrelli
* Aggiunte al carrello
* Rimozioni dal carrello
* Visualizzazioni carrello
* Pagamenti
* Ordini
* Ricavi
* Unità

### Utilizzo dei dati in LLM Optimizer

Questo set di dati potenzia gli insight di LLM Optimizer per:

* Prestazioni del traffico LLM a livello di pagina.
* Prestazioni del referrer tra le origini LLM.
* Tendenze regionali e a livello di dispositivo.
* Risultati commerciali a valle.

## Domande frequenti {#faq}

D: L’integrazione di Adobe Analytics è disponibile nella versione di prova?

No. L’integrazione è disponibile solo per i clienti LLM Optimizer a pagamento.

D: Quali dati vengono raccolti o memorizzati?

Consulta il capitolo [Dati acquisiti](#data-ingested) qui sopra. LLM Optimizer funziona con metriche aggregate provenienti dalle API di Adobe Analytics autorizzate dalla tua organizzazione, non con i dati non elaborati a livello di hit.

D: Come vengono acquisiti i dati?

La tua organizzazione autorizza LLM Optimizer a eseguire query sulle API di Adobe Analytics. Il traffico da referral allineato alle origini LLM viene utilizzato tramite tali API.

D: Con quale frequenza vengono aggiornati i dati?

I dati vengono aggiornati **ogni giorno** (l’intero giorno precedente al completamento della retrocompilazione).

D: I dati non elaborati a livello di hit vengno memorizzati in LLM Optimizer?

No. Solo le metriche **aggregate** vengono utilizzate per comprendere i pattern e le tendenze del traffico.

D: Vengono memorizzati URL completi, stringhe di query o contenuti della pagina?

È possibile che vengano acquisiti gli URL completi utilizzati per la dimensione pagina selezionata; le stringhe di query e il contenuto della pagina non vengono acquisiti per questa integrazione.

D: Gli identificativi degli utenti (ECID, indirizzo IP, ID cookie) vengono memorizzati?

No.

D: Per quanto tempo vengono conservati i dati?

I criteri di conservazione possono cambiare. Attualmente, i dati vengono memorizzati a tempo indefinito.

D: I dati sono crittografati in transito e a riposo?

Attualmente, i dati vengono crittografati in transito e non a riposo. Questo aspetto potrebbe cambiare negli aggiornamenti futuri.

D: I dati storici vengono retrocompilati?

Sì. Dopo una configurazione corretta, vengono retrocompilate le ultime quattro settimane di calendario intere e la settimana di calendario corrente. Consulta anche [Dopo la connessione](#after-connect).
