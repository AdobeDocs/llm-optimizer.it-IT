---
title: Traffico di riferimento
description: Panoramica dell’articolo.
source-git-commit: c83b4929a82331534654fcfdccd41d91eefe6d92
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 0%

---


# Traffico di riferimento

Il traffico di riferimento mostra come i visitatori arrivano al sito da piattaforme esterne, citazioni AI e collegamenti di riferimento. Tiene traccia e analizza le origini del traffico, i pattern di riferimento e le metriche di conversione da siti web e piattaforme esterni. Questo ti aiuterà a capire quali origini, aree geografiche e pagine generano il traffico più coinvolto. I dati provengono dai registri CDN o dalla telemetria operativa AEM **(collegamento di aggiunta)**. Entrambe queste fonti tutelano la privacy e non acquisiscono dati personali degli utenti.

Sono inoltre disponibili filtri personalizzabili per aiutarti a perfezionare i dati visualizzati.

In questa pagina sono disponibili i dettagli riportati di seguito.

* [Configurazione](#setup)
* [Filtri](#filters)
* [Prestazioni di riferimento generali](#overall-performance)
* [Primi URL di riferimento](#top-referrals)
* [Dettagli traffico di riferimento](#traffic-details)

## Configurazione {#setup}

Al primo accesso, il dashboard Traffico di riferimento potrebbe apparire vuoto. Per visualizzare i dati, devi configurare un provider del traffico di riferimento.

![Impostazione riferimento](/help/dashboards/assets/referral-setup.png)

1. Seleziona il tuo Source (registri CDN o telemetria operativa AEM).
2. Immetti un indirizzo e-mail di contatto principale.
3. Fai clic su **Richiedi attivazione** per abilitare l&#39;acquisizione dei dati.

Una volta attivata, la dashboard viene compilata con le metriche del traffico di riferimento.

## Filtri {#filters}

Nella parte superiore della pagina, puoi applicare i filtri per perfezionare la visualizzazione. I filtri scelti influiranno su **tutte** le sezioni presenti nel dashboard. Puoi personalizzare quanto segue:

**Intervallo date** - Selezionare l&#39;intervallo di tempo per i dati visualizzati. Ad esempio, le ultime 4 settimane. Puoi anche personalizzare il periodo di tempo selezionando l&#39;opzione **Settimane personalizzate**.
**Piattaforma** - Scegli un&#39;origine del traffico specifica, ad esempio Google, OpenAI o social media.
**Canale** - Filtra i canali, ad esempio Canale guadagnato o Pagato. Se preferisci una combinazione tra i due, seleziona l&#39;opzione **Tutti i canali**.
**Canale Source** - Filtra in base all&#39;origine del canale. le opzioni includono: visualizzazione, ricerca, riferimento, video e social network. È inoltre possibile utilizzare **Tutte le piattaforme** per visualizzare tutte le origini di canale.
**Tipo di dispositivo** - Analizza il traffico in base al tipo di dispositivo del visitatore, desktop, dispositivi mobili o tutti i dispositivi.
**Area** - Visualizza i pattern di riferimento in aree geografiche diverse.

Dopo aver selezionato il filtro desiderato, fare clic su **Applica filtri** per applicare la selezione al dashboard.

## Prestazioni di riferimento generali {#overall-performance}

La dashboard evidenzia le prestazioni complessive del riferimento visualizzando le metriche chiave seguenti:

* **Traffico di riferimento totale** - Traffico di riferimento totale da tutte le origini.
* **Percentuale di consenso** - La percentuale di visitatori che accettano una richiesta di consenso.
* **Percentuale di mancato recapito** - Percentuale di sessioni da origini di riferimento che non hanno avuto alcun evento di coinvolgimento.

![Pagina di riferimento](/help/dashboards/assets/referral-traffic.png)

Oltre alle metriche delle prestazioni complessive presentate qui sopra, il pannello **Prime aree geografiche** suddivide il traffico per area geografica. Nel frattempo, il pannello **Origini di riferimento principali** mostra le piattaforme che generano il maggior numero di visite.

## Primi URL di riferimento {#top-referrals}

L’elenco URL di riferimento principali fa emergere le pagine più visitate del sito dai riferimenti.

![URL di riferimento principali](/help/dashboards/assets/top-url.png)

## Dettagli traffico di riferimento {#traffic-details}

La tabella Dettagli traffico di riferimento consente di valutare sia il volume di traffico che la qualità. Fornisce una suddivisione dettagliata per origine, inclusi i conteggi delle visite, i tassi di mancato recapito e il tipo di canale.

![Dettagli traffico di riferimento](/help/dashboards/assets/traffic-details.png)

La tabella contiene le seguenti categorie:

**Source** - Origine del traffico di riferimento.
**Visite** - Numero totale di visite per ogni origine.
**Percentuale di mancato recapito** - Percentuale di sessioni dall&#39;origine di riferimento che non hanno avuto alcun evento di coinvolgimento.
**Canale** - Canale per l&#39;origine, guadagnato, pagato o entrambi.

Puoi utilizzare l&#39;opzione **Esporta** per scaricare la tabella .csv e condividere le informazioni con il tuo team oppure includere la tabella del traffico di riferimento nei report esecutivi.
