---
title: Ispettore URL
description: Scopri come utilizzare l’Ispettore URL per analizzare le prestazioni di pagine specifiche sul dominio nelle ricerche AI.
feature: URL Inspector
source-git-commit: e50c87e8e5a669526f3c10855c1629ce82b67aef
workflow-type: tm+mt
source-wordcount: '681'
ht-degree: 0%

---


# Ispettore URL

L’Ispettore URL consente di analizzare le prestazioni di pagine specifiche sul dominio nelle ricerche AI. Combina visibilità, traffico agente e dati di riferimento a livello di URL per fornire una visualizzazione granulare degli URL citati e della frequenza con cui compaiono nelle risposte.

![Ispettore URL](/help/dashboards/assets/url-insp.png)

## Filtri

Nella parte superiore della pagina, puoi applicare i filtri per perfezionare la visualizzazione. I filtri scelti influiranno su **tutte** le sezioni presenti nel dashboard. Puoi personalizzare quanto segue:

* **Intervallo date** - Selezionare l&#39;intervallo di tempo per i dati visualizzati. Ad esempio, le ultime 4 settimane. Puoi anche personalizzare il periodo di tempo selezionando l&#39;opzione **Settimane personalizzate**.
* **Categoria** - Filtra i risultati visualizzati per categorie.
* **Piattaforma** - Scegli quale motore di intelligenza artificiale analizzare.
* **Tipo di contenuto pagina** - Filtra per tipo di contenuto.
* **Area** - Filtra i risultati per area geografica. Al momento del lancio non tutte le aree geografiche saranno disponibili.

Dopo aver selezionato il filtro desiderato, fare clic su **Applica filtri** per applicare la selezione al dashboard.

## Metriche di panoramica

L’Ispettore URL fornisce diverse metriche di panoramica che consentono di valutare rapidamente le prestazioni delle pagine nelle ricerche AI. Vengono fornite le metriche seguenti:

* **Richieste univoche con citazioni di proprietà** - Numero totale di richieste di IA univoche con citazioni di proprietà.
* **Totale prompt univoci** - Numero totale di prompt di IA univoci.
* **URL citati univoci** - Numero di URL di proprietà univoci citati.
* **Totale volte citate** - Totale volte in cui un URL di proprietà è stato citato nelle risposte generate da IA.
* **Totale hit agente** - Numero totale di hit dagli agenti di IA negli URL.
* **Risultati di riferimento da LLM** - Numero totale di risultati indirizzati dalle risposte generate dall&#39;intelligenza artificiale agli URL.

Gli indicatori di tendenza per ogni metrica panoramica mostrano le modifiche di questi valori nel tempo rispetto al periodo precedente.

## Gli URL citati

La visualizzazione URL citati elenca tutti gli URL del brand citati nelle risposte generate dall’intelligenza artificiale, con metriche di supporto. Entrambe le tabelle dispongono di un campo di ricerca per l&#39;accesso rapido agli argomenti ed è possibile personalizzare le metriche visualizzate facendo clic sul pulsante **Configura colonne**. Inoltre, puoi utilizzare l&#39;opzione **Esporta** per scaricare la tabella .csv e condividere le informazioni con il tuo team oppure includere la tabella nei report manageriali.

![URL citati](/help/dashboards/assets/cited-urls.png)

Vengono fornite le metriche seguenti:

* **URL** - URL analizzato.
* **Volte citate** - Il numero di volte in cui l&#39;URL è stato citato nelle risposte generate da IA.
* **Prompt citati in** - Numero di prompt di IA univoci che hanno citato l&#39;URL.
* **Categorie** - Le categorie di prodotti o gli argomenti associati all&#39;URL.
* **Aree**: l&#39;area geografica in cui è stato citato l&#39;URL.
* **Hit agenti** - Numero totale di hit dagli agenti di IA negli URL.
* **Hit di riferimento** - Numero di hit indirizzati dalle risposte generate dall&#39;intelligenza artificiale agli URL.

## URL di tendenza in competizione per le citazioni

Gli URL di tendenza in competizione per la visualizzazione delle citazioni evidenziano gli URL esterni attualmente citati nelle risposte pertinenti al tuo marchio, misurando chi sta vincendo le citazioni nel tuo spazio. La tabella dati contiene un campo di ricerca per l’accesso rapido a URL specifici. Inoltre, puoi utilizzare l&#39;opzione **Esporta** per scaricare la tabella .csv e condividere le informazioni con il tuo team oppure includere la tabella nei report manageriali.

![URL di tendenza in competizione per le citazioni](/help/dashboards/assets/trend-url.png)

Vengono fornite le metriche seguenti:

* **URL** - URL analizzato
* **Tipo di contenuto** - Il tipo di contenuto (di proprietà, social, guadagnato, altro).
* **Volte citate** - Il numero di volte in cui l&#39;URL è stato citato nelle risposte generate da IA.
* **Prompt citati in** - Numero di prompt di IA univoci che hanno citato l&#39;URL.
* **Categorie** - Le categorie di prodotti o gli argomenti associati all&#39;URL.
* **Aree**: l&#39;area geografica in cui è stato citato l&#39;URL.

### Finestra Dettagli

Sia per la visualizzazione citata che per quella di tendenza, gli URL dispongono di un pulsante **Dettagli** alla fine di ogni riga. Facendo clic sul pulsante viene visualizzata una finestra separata con ulteriori dettagli. La finestra dei dettagli mostra la frequenza con cui l&#39;URL viene citato, <!--the sentiment of AI responses where it is mentioned,--> gli argomenti e le richieste in cui viene visualizzato e le tendenze nel traffico di agenti e di riferimento nel tempo (per gli URL di proprietà).

![Finestra Dettagli](/help/dashboards/assets/details-url.png)
