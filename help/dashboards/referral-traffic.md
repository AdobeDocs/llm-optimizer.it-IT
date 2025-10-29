---
title: Traffico di riferimento
description: Scopri come utilizzare il dashboard Traffico di riferimento per vedere come i visitatori arrivano al tuo sito da piattaforme esterne, citazioni AI e collegamenti di riferimento.
feature: Referral Traffic
source-git-commit: e50c87e8e5a669526f3c10855c1629ce82b67aef
workflow-type: tm+mt
source-wordcount: '603'
ht-degree: 0%

---


# Traffico di riferimento

Il traffico di riferimento mostra come i visitatori arrivano al sito da piattaforme esterne, citazioni AI e collegamenti di riferimento. Tiene traccia e analizza le origini del traffico, i pattern di riferimento e le metriche di conversione da siti web e piattaforme esterni. Questo ti aiuterà a capire quali origini, aree geografiche e pagine generano il traffico più coinvolto. <!--Data is sourced from the CDN logs, a privacy-preserving source that does not capture personal user data.--> Sono inoltre disponibili filtri personalizzabili che consentono di perfezionare i dati visualizzati.

![Pagina di riferimento](/help/dashboards/assets/referral-traffic.png)

In questa pagina sono disponibili i dettagli riportati di seguito.

* [Configurazione](#setup)
* [Filtri](#filters)
* [Prestazioni di riferimento generali](#overall-performance)
* [Primi URL di riferimento](#top-referrals)
* [Dettagli traffico di riferimento](#traffic-details)

## Configurazione {#setup}

Al primo accesso, il dashboard Traffico di riferimento potrebbe apparire vuoto. Per visualizzare i dati, devi configurare [Inoltro registro CDN](/help/dashboards/customer-configuration.md#cdn-configuration) selezionando **Vai alla configurazione**.

![Impostazione riferimento](/help/dashboards/assets/referral-setup1.png)

<!--- 1. Select your Source (either CDN logs or AEM Operational Telemetry).
2. Enter a primary contact email.
3. Click **Request activation** to enable data ingestion. Hiding this until confirmation from PM-->

Una volta attivata, la dashboard verrà compilata con le metriche del traffico di riferimento.

## Filtri {#filters}

Nella parte superiore della pagina, puoi applicare i filtri per perfezionare la visualizzazione. I filtri scelti influiranno su **tutte** le sezioni presenti nel dashboard. Puoi personalizzare quanto segue:

* **Intervallo date** - Selezionare l&#39;intervallo di tempo per i dati visualizzati. Ad esempio, le ultime 4 settimane. Puoi anche personalizzare il periodo di tempo selezionando l&#39;opzione **Settimane personalizzate**.
* **Piattaforma** - Scegli un&#39;origine del traffico specifica, ad esempio Google, OpenAI o social media.
* **Intento pagina** - Filtra il traffico di riferimento in base all&#39;intento dell&#39;utente.
* **Canale Source** - Filtra in base all&#39;origine del canale. le opzioni includono: LLM, canali di riferimento acquisiti, a pagamento o misti.
* **Tipo di dispositivo** - Analizza il traffico in base al tipo di dispositivo del visitatore, desktop, dispositivi mobili o tutti i dispositivi.
  **Area** - Visualizza i pattern di riferimento in aree geografiche diverse.

Dopo aver selezionato il filtro desiderato, fare clic su **Applica filtri** per applicare la selezione al dashboard.

## Prestazioni di riferimento generali {#overall-performance}

La dashboard evidenzia le prestazioni complessive del riferimento visualizzando metriche chiave, tra cui:

* **Traffico di riferimento totale** - Traffico di riferimento totale da tutte le origini.
* **Traffico di riferimento da LLM** - Totale del traffico di riferimento da LLM.
* **Percentuale di consenso** - La percentuale di visitatori che accettano una richiesta di consenso.
* **Percentuale di mancato recapito** - Percentuale di sessioni da origini di riferimento che non hanno avuto alcun evento di coinvolgimento.

![Pagina di riferimento](/help/dashboards/assets/referral-traffic.png)

Oltre alle metriche delle prestazioni complessive presentate in precedenza, sono disponibili tre pannelli aggiuntivi che mostrano la distribuzione del traffico tra diversi mercati, origini di riferimento e categorie di intento pagina <!-- the **Top Regions** panel breaks down traffic by geography. Meanwhile, the **Top Referral Sources** panel shows the platforms driving the most visits. Trend indicators for the metrics show how these values are changing over time compared to the previous period.-->

<!--## Top Referral URLs {#top-referrals}

The Top Referral URLs list surfaces your site's most visited pages from referrals.

![Top Referral URLs](/help/dashboards/assets/top-url.png)-->

## Dettagli delle origini di riferimento e analisi delle prestazioni degli URL {#traffic-details}

Le tabelle Dettagli origini di riferimento e Analisi delle prestazioni degli URL consentono di valutare sia il volume di traffico che la qualità. Fai clic su ciascuna scheda di seguito per ulteriori dettagli:

![Dettagli traffico di riferimento](/help/dashboards/assets/traffic-details.png)

>[!BEGINTABS]

>[!TAB Dettagli origini di riferimento]

La vista Dettagli origini di riferimento suddivide il traffico proveniente da diverse piattaforme come OpenAI, Microsoft, Google e Perplessità. Visualizza metriche chiave come visite, tasso di mancato recapito e tipo di canale, che ti aiutano a capire quali origini di intelligenza artificiale e ricerca generano il traffico più coinvolto verso il tuo sito.

* **Source** - Origine del traffico di riferimento.
* **Visite** - Numero totale di visite per ogni origine.
* **Percentuale di mancato recapito** - Percentuale di sessioni dall&#39;origine di riferimento che non hanno avuto alcun evento di coinvolgimento.
* **Canale** - Canale per l&#39;origine, guadagnato, pagato o entrambi.

>[!TAB Analisi prestazioni URL]

La vista Analisi delle prestazioni degli URL classifica le pagine con le prestazioni migliori in base al volume di traffico di riferimento proveniente da LLM e da altre origini. Mette in evidenza metriche quali traffico, frequenza di rimbalzo, frequenza di consenso e intento di pagina, consentendoti di identificare quali pagine attirano e mantengono i visitatori più coinvolti dai riferimenti basati sull’intelligenza artificiale. La tabella contiene un campo di ricerca per l&#39;accesso rapido agli argomenti.

>[!ENDTABS]

In entrambe le tabelle è possibile utilizzare l&#39;opzione **Esporta** per scaricare il file .csv della tabella e condividere le informazioni con il team oppure includere le tabelle nel reporting esecutivo. Inoltre, per entrambe le tabelle, è possibile personalizzare le metriche da visualizzare facendo clic sul pulsante **Configura colonne**.
