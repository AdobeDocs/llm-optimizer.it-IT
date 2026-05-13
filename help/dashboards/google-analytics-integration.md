---
title: Integrazione Google Analytics
description: Scopri come collegare Google Analytics 4 con LLM Optimizer per misurare l’individuazione basata sull’intelligenza artificiale, il coinvolgimento dei siti e i risultati di business nel dashboard di Traffico da referral.
feature: Referral Traffic
source-git-commit: 368b3c1ee79660ede0c4bf9824f299d2e801c8b2
workflow-type: tm+mt
source-wordcount: '1169'
ht-degree: 0%

---


# Integrazione Google Analytics

L’integrazione di Google Analytics 4 (GA4) collega LLM Optimizer con i dati GA4 dell’organizzazione per consentirti di misurare come l’individuazione basata sull’intelligenza artificiale su piattaforme quali ChatGPT, Gemini, Copilot, Claude e Perplexity si traduce in un coinvolgimento reale del sito web e in risultati di business. Dopo aver connesso una proprietà GA4, LLM Optimizer richiama le metriche di traffico da referral, coinvolgimento e conversione che attribuiscono GA4 a tali origini e le inserisce nella dashboard **Traffico da referral** nella scheda **Impatto aziendale**.

>[!IMPORTANT]
>
>L’integrazione GA4 è inclusa nell’offerta a pagamento di LLM Optimizer. I clienti che utilizzano la versione di prova gratuita non potranno connettersi a GA4 fino a quando non effettueranno l’aggiornamento a un’offerta a pagamento.

## Prima di iniziare {#before-you-begin}

Per completare la connessione è necessario:

* Un account Google con almeno l&#39;accesso **Viewer** alla proprietà GA4 che si desidera connettere. L&#39;accesso a livello di proprietà viene gestito in Google Analytics in **Admin > Gestione accesso proprietà**.
* Autorizzazione per gestire la configurazione in LLM Optimizer (altrimenti il pulsante Connetti è visibile ma disabilitato).
* Browser che consente popup dall&#39;origine LLM Optimizer. Il passaggio di accesso a Google si apre in una nuova scheda.

**non** è necessario creare un progetto Google Cloud, generare un account di servizio, caricare una chiave JSON o immettere un ID proprietà. LLM Optimizer gestisce la connessione tramite la schermata di consenso OAuth standard di Google.

## Connettere GA4 al dashboard del Traffico da referral {#connect}

Il flusso di connessione inizia dal dashboard [Traffico da referral](/help/dashboards/referral-traffic.md) come segue:

1. Apri **Traffico da referral** in LLM Optimizer.

1. Apri la scheda **Impatto aziendale**.

   ![Dashboard di Traffico da referral, scheda Impatto aziendale](/help/dashboards/assets/ga4-integration-01-business-impact-tab.png)

1. Selezionare **Connetti ad Analytics**. LLM Optimizer ti indirizza a **Configurazione cliente > Analytics**. Nel selettore del provider Analytics, selezionare **Connetti Google Analytics 4**.

   ![Configurazione cliente, scheda Analytics con GA4 selezionato](/help/dashboards/assets/ga4-integration-02-analytics-ga4-picker.png)

1. Seleziona **Connetti account**. Viene visualizzata una nuova scheda del browser nella schermata di accesso di Google.

   ![Accesso a Google per la connessione GA4](/help/dashboards/assets/ga4-integration-03-google-sign-in.png)

1. Accedi con l&#39;account Google che ha accesso alla proprietà GA4 che desideri connettere. Approvare l&#39;autorizzazione `See and download your Google Analytics data` (ambito `analytics.readonly`) quando Google richiede.

1. Google ti riporta a LLM Optimizer, che elenca le proprietà GA4 a cui il tuo account può accedere. Seleziona la proprietà da connettere e inviare.

1. Torna alla scheda LLM Optimizer. La scheda Analytics rileva automaticamente la connessione completata e la scheda GA4 mostra lo stato **Connesso**.

### Dopo la connessione {#after-connect}

Dopo aver connesso GA4 a LLM Optimizer, si verifica quanto segue:

* LLM Optimizer esegue il backfill delle **ultime quattro settimane di calendario complete** e della **settimana di calendario corrente fino alla data**.
* Dopo il backfill, i dati vengono aggiornati **ogni giorno** con un pull di **giorno precedente completo**.

>[!NOTE]
>
>Il completamento della compilazione potrebbe richiedere un paio d’ore. Il dashboard Impatto aziendale inizia a essere popolato progressivamente con l’arrivo dei dati; non è richiesta alcuna azione da parte tua durante l’esecuzione della retrocompilazione.

Se ti riconnetti (ad esempio, per cambiare l’account Google o la proprietà GA4), viene ripristinata solo la settimana del calendario corrente, mentre le settimane precedenti già caricate vengono mantenute.

## Come funziona {#how-it-works}

### Modello di connessione

L’integrazione utilizza il flusso standard Google OAuth 2.0 delegato dall’utente. LLM Optimizer memorizza un token di aggiornamento con ambito nella proprietà GA4 selezionata e tale token consente a LLM Optimizer di chiamare l’API dati GA4 per tuo conto (con accesso in sola lettura) fino a quando non lo revochi dall’account Google.

### Come viene identificato il traffico LLM

LLM Optimizer chiede a GA4 solo per le sessioni che la stessa GA4 attribuisce a una piattaforma LLM. Oggi si tratta di sessioni il cui `sessionSourceMedium` corrisponde a uno di `chatgpt`, `gemini.google.com`, `copilot.microsoft.com`, `claude` o `perplexity`. L’elenco delle origini LLM supportate è gestito da Adobe e può espandersi nel tempo.

### Dati acquisiti {#data-ingested}

Ogni pull giornaliero recupera un report aggregato contenente quanto segue:

**Dimensioni**

| Dimensione GA4 | Cosa rappresenta |
| --- | --- |
| `date` | Il giorno in cui si è verificata la sessione. |
| `landingPage` | La prima pagina che il visitatore ha visto sul tuo sito. |
| `countryId` | Il paese del visitatore, come determinato dalla geolocalizzazione IP di GA4. |
| `deviceCategory` | Mobile/desktop/tablet. |
| `sessionSourceMedium` | La sorgente/supporto LLM attribuita da GA4. |

**Metriche**

| Metrica GA4 | Cosa rappresenta |
| --- | --- |
| `sessions` | Numero di sessioni nel bucket. |
| `screenPageViews` | Visualizzazioni di pagina nel bucket. |
| `bounceRate` | Frazione di sessioni non recapitate. |
| `totalPurchasers` | acquirenti distinti (se l’e-commerce è configurato in GA4). |
| `transactions` | Conteggio delle transazioni (se è configurato l’e-commerce). |
| `purchaseRevenue` | Ricavi da acquisto (USD). |
| `totalRevenue` | Ricavi totali (USD). |

### Utilizzo dei dati in LLM Optimizer

LLM Optimizer utilizza questi dati per popolare le prestazioni a livello di pagina della dashboard Impatto aziendale, i raggruppamenti delle origini, le suddivisioni per paese e dispositivo e le tendenze temporali. Nessun dato viene utilizzato per addestrare modelli o condiviso al di fuori del tenant.

### Cosa non viene acquisito

Nessun identificatore utente (ID client Google, indirizzo IP, ID dispositivo), nessuna riga a livello di sessione, nessuna riga a livello di evento, nessuna dimensione o metrica personalizzata oltre a quelle elencate in precedenza e nessuna definizione di pubblico o segmento GA4.

## Domande frequenti {#faq}

D: L’integrazione GA4 è disponibile durante la prova?

No. L’integrazione è disponibile solo per i clienti LLM Optimizer a pagamento.

D: È necessario creare un account di progetto o di servizio Google Cloud?

No. La connessione è un accesso standard a Google. LLM Optimizer gestisce il client Google OAuth sul lato Adobe; è sufficiente un account Google con accesso al visualizzatore sulla proprietà GA4.

D: Quali dati vengono raccolti o memorizzati?

LLM Optimizer funziona con metriche aggregate dall’API dati GA4 autorizzata dalla tua organizzazione, non con dati non elaborati a livello di evento.

D: Come vengono acquisiti i dati?

La tua organizzazione autorizza LLM Optimizer a eseguire query sull’API dati GA4 per la proprietà selezionata. Il traffico da referral allineato alle origini LLM viene utilizzato tramite tale API.

D: Con quale frequenza vengono aggiornati i dati?

I dati vengono aggiornati **ogni giorno** (l&#39;intero giorno precedente al completamento della retrocompilazione).

D: I dati non elaborati a livello di evento sono memorizzati in LLM Optimizer?

No. Solo le metriche **aggregate** vengono utilizzate per comprendere i pattern e le tendenze del traffico.

D: vengono memorizzati URL completi, stringhe di query o contenuto della pagina?

I percorsi delle pagine di destinazione vengono acquisiti come parte del rapporto standard; le stringhe di query e il contenuto della pagina non vengono acquisiti per questa integrazione.

D: gli identificatori utente (ID client Google, indirizzo IP, ID dispositivo) sono memorizzati?

No.

D: Per quanto tempo vengono conservati i dati?

Attualmente, i dati vengono memorizzati a tempo indefinito.

D: I dati sono crittografati in transito e a riposo?

Attualmente, i dati vengono crittografati in transito, non a riposo. Questo comportamento potrebbe cambiare negli aggiornamenti futuri.

D: I dati storici vengono recuperati?

Sì. Dopo una configurazione corretta, vengono recuperate le ultime quattro settimane di calendario complete e la settimana di calendario corrente. Vedi anche [Dopo la connessione](#after-connect).

D: Posso disconnettere o revocare l’accesso?

Sì, in qualsiasi momento. Puoi riconnetterti a un account o a una proprietà diversa dalla scheda GA4 in LLM Optimizer oppure revocare l&#39;accesso a LLM Optimizer completamente dall&#39;account Google all&#39;indirizzo [https://myaccount.google.com/permissions](https://myaccount.google.com/permissions). La revoca dell’accesso interrompe le nuove estrazioni di dati; i dati aggregati precedentemente acquisiti rimangono in LLM Optimizer.

D: La mia proprietà GA4 è connessa ma l’impatto aziendale è vuoto — perché?

LLM Optimizer richiama solo le sessioni che la stessa GA4 attribuisce a un’origine/supporto LLM supportato (oggi: ChatGPT, Gemini, Copilot, Claude, Perplexity). Se la proprietà GA4 non ha ancora registrato le sessioni di riferimento da nessuna di queste origini nella finestra temporale mostrata, la dashboard risulterà vuota anche se la connessione è integra.
