---
title: Integrazione di Adobe Analytics
description: Scopri come collegare Adobe Analytics a LLM Optimizer per misurare l’individuazione basata sull’intelligenza artificiale, il coinvolgimento sul sito e i risultati di business nel dashboard di Traffico da referral.
feature: Referral Traffic
source-git-commit: e7c9bc1d40267dc92608baa005f85f4be21cfda1
workflow-type: tm+mt
source-wordcount: '879'
ht-degree: 3%

---


# Integrazione di Adobe Analytics

L’integrazione di Adobe Analytics collega LLM Optimizer con i dati Adobe Analytics della tua organizzazione in modo da poter misurare come il rilevamento basato sull’intelligenza artificiale si traduce in un coinvolgimento reale del sito web e in risultati di business. Al termine del processo di integrazione, i dati saranno disponibili nel dashboard **Traffico da referral** nella scheda **Impatto aziendale**.

Collegando i dati di analisi con le informazioni sulla visibilità AI, LLM Optimizer consente di tenere traccia di:

* Coinvolgimento degli utenti nelle pagine basate sull’intelligenza artificiale.
* Segnali di conversione associati a percorsi di individuazione IA.
* Impatto delle prestazioni delle ottimizzazioni GEO.

Questa integrazione colma il divario tra la misurazione della visibilità dell’intelligenza artificiale e l’analisi delle prestazioni aziendali. Ora i team possono vedere non solo dove il brand appare nelle risposte AI, ma anche cosa accade dopo l’arrivo degli utenti.

## Disponibilità {#availability}

>[!IMPORTANT]
>
>L’integrazione di Adobe Analytics è inclusa nell’offerta a pagamento di LLM Optimizer. I clienti che utilizzano la versione di prova gratuita non potranno collegare Adobe Analytics fino a quando non effettueranno l’aggiornamento a un’offerta a pagamento.

## Connettere Adobe Analytics al dashboard Traffico da referral {#connect}

Il flusso di connessione inizia dal dashboard [Traffico da referral](/help/dashboards/referral-traffic.md) come segue:

1. Apri il dashboard [Traffico da referral](/help/dashboards/referral-traffic.md). La visualizzazione predefinita è **Informazioni sul traffico**.

   ![Dashboard di Traffico da referral, scheda Traffic Insights](/help/dashboards/assets/aa-integration-01-referral-traffic-traffic-insights.png)

1. Selezionare la scheda **Impatto aziendale**. Se nessun provider di analisi è connesso, viene visualizzato un banner: **Connettiti per vedere l&#39;impatto aziendale**, con **Connetti ad Analytics**.

   ![Scheda Impatto aziendale con Connessione ad Analytics](/help/dashboards/assets/aa-integration-02-business-impact-connect.png)

1. Selezionare **Connetti ad Analytics**. Verrà aperto il dashboard [Configurazione cliente](/help/dashboards/customer-configuration.md) nella scheda **Analytics**.

   ![Configurazione del cliente, scheda Analytics](/help/dashboards/assets/aa-integration-03-analytics-tab.png)

1. In **Credenziali**, immettere l&#39;**ID client** e il **Segreto client**, quindi selezionare **Verifica e continua**. Nota:

   * **Verifica e continua** è disponibile solo quando entrambi i campi sono compilati.
   * Dopo una verifica corretta, le suite di rapporti vengono caricate.
   * Utilizza **ID client** e **Segreto client** di un [account tecnico](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/) che ha accesso alla suite di rapporti necessaria.

   ![Credenziali di Analytics e verifica e continua](/help/dashboards/assets/aa-integration-04-credentials.png)

1. In **Configurazione** scegliere una **Suite di rapporti**.

   Quando è selezionata una suite di rapporti, LLM Optimizer carica le opzioni dell&#39;**URL pagina Dimension** disponibili per tale suite.

   ![Suite di rapporti selezionata e dimensioni in fase di caricamento](/help/dashboards/assets/aa-integration-05-report-suite.png)

1. Scegli un **URL pagina Dimension** (elenco di dimensioni specifiche della suite), quindi seleziona **Salva e abilita**.

   * **L&#39;URL della pagina Dimension** rimane disabilitato finché non viene selezionata una suite di rapporti e finché le dimensioni non vengono caricate.
   * **Salva e abilita** è disponibile solo dopo aver selezionato una dimensione URL pagina.

   ![Dimensione URL pagina e Salva e abilita](/help/dashboards/assets/aa-integration-06-page-url-dimension.png)

1. Dopo il salvataggio, nella configurazione deve essere visualizzato lo stato **Connesso**. Puoi tornare al dashboard di Traffico da referral con **Vai al dashboard di Traffico da referral**. In **Traffico da referral** nella scheda **Impatto aziendale**, lo stato dovrebbe essere **Connesso ad Adobe Analytics**.

   ![Connesso ad Adobe Analytics nella configurazione e impatto aziendale](/help/dashboards/assets/aa-integration-07-connected.png)

### Dopo la connessione {#after-connect}

* LLM Optimizer esegue il backfill delle **ultime quattro settimane di calendario complete** e della **settimana di calendario corrente fino alla data**.
* Dopo il backfill, i dati vengono aggiornati **ogni giorno** con un pull di **giorno precedente completo**.

>[!NOTE]
>
>Il completamento della compilazione potrebbe richiedere un paio d’ore.

## Come funziona {#how-it-works}

### Configurazione

Durante la configurazione, definisci la suite di rapporti e la dimensione di pagina che LLM Optimizer utilizza per l’acquisizione di Adobe Analytics. La dimensione pagina può essere la mappatura standard `variables/page` o una `eVar` personalizzata, a seconda della suite di rapporti.

### Come viene identificato il traffico LLM

Il traffico originato da LLM viene identificato utilizzando il tipo di riferimento Adobe Analytics [Strumenti di IA per la conversazione](https://experienceleague.adobe.com/en/docs/analytics/components/dimensions/referrer-type#conversational-ai-tools).

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

Questo set di dati potenzia le informazioni di LLM Optimizer per:

* Prestazioni del traffico LLM a livello di pagina.
* Prestazioni del referrer tra le origini LLM.
* Tendenze regionali e a livello di dispositivo.
* Risultati commerciali a valle.

## Domande frequenti {#faq}

D: L’integrazione di Adobe Analytics è disponibile durante la prova?

No. L’integrazione è disponibile solo per i clienti LLM Optimizer a pagamento.

D: Quali dati vengono raccolti o memorizzati?

Vedi il capitolo [Dati acquisiti](#data-ingested) sopra. LLM Optimizer funziona con metriche aggregate provenienti dalle API di Adobe Analytics autorizzate dalla tua organizzazione, non con i dati non elaborati a livello di hit.

D: Come vengono acquisiti i dati?

La tua organizzazione autorizza LLM Optimizer a eseguire query sulle API di Adobe Analytics. Il traffico da referral allineato alle origini LLM viene utilizzato tramite tali API.

D: Con quale frequenza vengono aggiornati i dati?

I dati vengono aggiornati **ogni giorno** (l&#39;intero giorno precedente al completamento della retrocompilazione).

D: I dati non elaborati a livello di hit sono memorizzati in LLM Optimizer?

No. Solo le metriche **aggregate** vengono utilizzate per comprendere i pattern e le tendenze del traffico.

D: vengono memorizzati URL completi, stringhe di query o contenuto della pagina?

È possibile acquisire gli URL completi utilizzati per la dimensione pagina selezionata; le stringhe di query e il contenuto della pagina non vengono acquisiti per questa integrazione.

D: gli identificatori utente (ECID, indirizzo IP, ID cookie) sono memorizzati?

No.

D: Per quanto tempo vengono conservati i dati?

Tenere presente che i criteri di conservazione possono evolvere. Attualmente, i dati vengono memorizzati a tempo indefinito.

D: I dati sono crittografati in transito e a riposo?

Attualmente, i dati vengono crittografati in transito e non a riposo. Questo comportamento potrebbe cambiare negli aggiornamenti futuri.

D: I dati storici vengono recuperati?

Sì. Dopo una configurazione corretta, vengono recuperate le ultime quattro settimane di calendario complete e la settimana di calendario corrente. Vedi anche [Dopo la connessione](#after-connect).
