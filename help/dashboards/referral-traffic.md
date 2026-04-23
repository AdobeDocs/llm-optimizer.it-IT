---
title: Traffico da referral
description: Scopri come utilizzare la dashboard Traffico da referral per vedere come i visitatori accedono al tuo sito da piattaforme esterne, citazioni IA e collegamenti di referral.
feature: Referral Traffic
source-git-commit: 625807b8905f741aa89d551483d89cca2ef91873
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 79%

---


# Traffico da referral

Traffico da referral mostra come i visitatori accedono al tuo sito da piattaforme esterne, citazioni IA e collegamenti di referral. Tieni traccia e analizza le origini del traffico, i pattern di referral e le metriche di conversione da siti web e piattaforme esterni. Ti aiuterà a capire da quali origini, aree geografiche e pagine proviene il traffico con maggior coinvolgimento. <!--Data is sourced from the CDN logs, a privacy-preserving source that does not capture personal user data.--> Sono inoltre disponibili filtri personalizzabili per aiutarti a perfezionare i dati visualizzati.

>[!NOTE]
>Per impostazione predefinita, questo dashboard crea informazioni sul traffico da **registri CDN**. Se la tua organizzazione è su un&#39;offerta a pagamento, puoi connettere **Adobe Analytics** per aggiungere dati che misurino l&#39;individuazione basata sull&#39;intelligenza artificiale e il coinvolgimento del sito. Questi dati sono disponibili nella scheda **Impatto aziendale**. Senza l’integrazione in Adobe Analytics, la scheda non viene compilata. Per ulteriori dettagli, consulta [Integrazione Adobe Analytics](/help/dashboards/adobe-analytics-integration.md).

![Pagina Referral](/help/dashboards/assets/referral-traffic.png)

Questa pagina descrive quanto segue:

* [Configurazione](#setup)
* [Filtri](#filters)
* [Prestazioni di referral complessive](#overall-performance)
* [URL di referral principali](#top-referrals)
* [Dettagli del traffico da referral](#traffic-details)

Se sei sulla [esperienza incentrata sul marchio](/help/overview/quick-start.md#brand-centric-experience), passa a **Traffico da referral** e seleziona il sito per il quale desideri visualizzare le informazioni sul Traffico da referral LLM.

![Traffico da referral — selettore del sito (esperienza incentrata sul marchio)](/help/assets/brand-centric-experience/referral-traffic-dashboard.png)

## Configurazione {#setup}

Al primo accesso, la dashboard Traffico da referral potrebbe apparire vuota. Per visualizzare i dati, devi configurare l’inoltro del registro CDN.

Per i clienti che si trovano nella [esperienza incentrata sul marchio](/help/overview/quick-start.md#brand-centric-experience), puoi aggiungere informazioni sull&#39;inoltro del registro CDN passando a **Gestione marchi** e facendo clic sull&#39;etichetta **CDN**. Vedi anche [Traffico agente - Configurazione CDN](/help/dashboards/agentic-traffic.md#cdn-setup).

**Configurazione del cliente (esperienza classica):** Configura [Inoltro del registro CDN](/help/dashboards/customer-configuration.md#cdn-configuration) selezionando **Vai alla configurazione**.

![Configurazione di referral](/help/dashboards/assets/referral-setup1.png)

<!--
1. Select your Source (either CDN logs or AEM Operational Telemetry).
2. Enter a primary contact email.
3. Click **Request activation** to enable data ingestion. Hiding this until confirmation from PM
-->

Una volta attivato, nella dashboard verranno inserite le metriche del traffico da referral.

## Filtri {#filters}

Nella parte superiore della pagina, puoi applicare i filtri per definire la vista. I filtri che scegli influiranno su **tutte** le sezioni presenti nella dashboard. Puoi personalizzare quanto segue:

* **Intervallo di date**: seleziona l’arco temporale per i dati da visualizzare. Ad esempio, le ultime 4 settimane. Puoi anche personalizzare il periodo di tempo selezionando l’opzione **Settimane personalizzate**.
* **Piattaforma**: scegli un’origine del traffico specifica, ad esempio Google, OpenAI o social media.
* **Intento pagina**: filtra il traffico da referral in base all’intento degli utenti.
* **Origine canale**: filtra in base all’origine del canale. Le opzioni includono: LLM, earned media, a pagamento, o canali di referral misti.
* **Tipo di dispositivo**: analizza il traffico in base al tipo di dispositivo del visitatore, ossia desktop, dispositivi mobili o tutti i dispositivi.
* **Area geografica**: visualizza i pattern di referral da aree geografiche diverse.

Una volta selezionato il filtro, fai clic su **Applica filtri** per applicare la selezione alla dashboard.

## Prestazioni di referral complessive {#overall-performance}

La dashboard evidenzia le prestazioni di referral complessive visualizzando metriche chiave, tra cui:

* **Totale traffico da referral**: traffico da referral totale da tutte le origini.
* **Traffico di referral totale da LLM**: traffico da referral totale da LLM.
* **Tasso di consenso**: percentuale di visitatori che accettano un prompt di consenso.
* **Tasso di rimbalzo**: percentuale di sessioni da origini di referral che non hanno avuto alcun evento di coinvolgimento.

![Pagina di referral](/help/dashboards/assets/referral-traffic.png)

Oltre alle metriche delle prestazioni complessive presentate in precedenza, sono disponibili tre pannelli aggiuntivi che mostrano la distribuzione del traffico per diversi mercati, origini di referral e categorie di intento delle pagina. <!-- the **Top Regions** panel breaks down traffic by geography. Meanwhile, the **Top Referral Sources** panel shows the platforms driving the most visits. Trend indicators for the metrics show how these values are changing over time compared to the previous period.-->

<!--
## Top Referral URLs {#top-referrals}

The Top Referral URLs list surfaces your site's most visited pages from referrals.

![Top Referral URLs](/help/dashboards/assets/top-url.png)
-->

## Dettagli origini di referral e Analisi prestazioni URL {#traffic-details}

Le tabelle Dettagli origini di referral e Analisi prestazioni URL consentono di valutare sia il volume di traffico che la qualità. Fai clic su ciascuna scheda di seguito per ulteriori dettagli:

![Dettagli traffico da referral](/help/dashboards/assets/traffic-details.png)

>[!BEGINTABS]

>[!TAB Dettagli origini di referral]

La vista Dettagli origini di referral suddivide il traffico proveniente da diverse piattaforme come OpenAI, Microsoft, Google e Perplexity. Visualizza metriche chiave come visite, tasso di rimbalzo e tipo di canale, utili per comprendere quali origini IA e di ricerca generano il traffico con maggior coinvolgimento verso il tuo sito.

* **Origine**: origine del traffico da referral.
* **Visite**: numero totale di visite per ogni origine.
* **Tasso di rimbalzo**: percentuale di sessioni dall’origine di referral che non hanno avuto alcun evento di coinvolgimento.
* **Canale**: canale per l’origine, ossia earned media, a pagamento o entrambi.

>[!TAB Analisi prestazioni URL]

La vista Analisi prestazioni URL classifica le pagine con le prestazioni migliori in base al volume di traffico da referral proveniente da LLM e da altre origini. Evidenzia metriche quali traffico, tasso di rimbalzo, tasso di consenso e intento della pagina, per aiutarti a individuare le pagine che attirano e mantengono i visitatori con maggiore coinvolgimento dai referral basati sull’IA. La tabella contiene un campo di ricerca per l’accesso rapido agli argomenti.

>[!ENDTABS]

In entrambe le tabelle puoi utilizzare l’opzione **Esporta** per scaricare il file .csv della tabella e condividere gli insight con il tuo team oppure includere le tabelle nei rapporti per il management.. Inoltre, per entrambe le tabelle, puoi personalizzare le metriche da visualizzare facendo clic sul pulsante **Configura colonne**.
