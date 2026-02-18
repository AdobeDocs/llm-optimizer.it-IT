---
title: Inspector URL
description: Scopri come utilizzare l’Inspector URL per analizzare le prestazioni a livello di ricerche IA di pagine specifiche nel tuo dominio.
feature: URL Inspector
source-git-commit: e50c87e8e5a669526f3c10855c1629ce82b67aef
workflow-type: ht
source-wordcount: '687'
ht-degree: 100%

---


# Inspector URL

L’Inspector URL consente di analizzare le prestazioni a livello di ricerche IA di pagine specifiche nel tuo domini. Combina visibilità, traffico da IA agentica e dati referral a livello di URL per fornire una vista granulare degli URL citati e della frequenza con cui compaiono nelle risposte.

![Inspector URL](/help/dashboards/assets/url-insp.png)

## Filtri

Nella parte superiore della pagina, puoi applicare i filtri per definire la vista. I filtri scelti influiranno su **tutte** le sezioni presenti nella dashboard. Puoi personalizzare quanto segue:

* **Intervallo di date**: seleziona l’arco temporale per i dati da visualizzare. Ad esempio, le ultime 4 settimane. Puoi anche personalizzare il periodo di tempo selezionando l’opzione **Settimane personalizzate**.
* **Categoria**: filtra i risultati visualizzati per categorie.
* **Piattaforma**: scegli quale motore IA analizzare.
* **Tipo di contenuto pagina**: filtra per tipo di contenuto.
* **Area geografica**: filtra i risultati per area geografica. Al momento del lancio non tutte le aree geografiche saranno disponibili.

Dopo aver selezionato il filtro, fai clic su **Applica filtri** per applicare la selezione alla dashboard.

## Metriche di panoramica

L’Inspector URL fornisce diverse metriche di panoramica che consentono di valutare rapidamente le prestazioni delle pagine nelle ricerche IA. Vengono fornite le metriche seguenti:

* **Prompt univoci con citazioni di proprietà**: numero totale di prompt IA univoci con citazioni di proprietà.
* **Totale prompt univoci**: numero totale di prompt IA univoci.
* **URL citati univoci**: numero di URL di proprietà univoci che sono stati citati.
* **Numero totale di citazioni**: numero totale delle volte in cui è stato citato un URL di proprietà nelle risposte generate dall’IA.
* **Hit totali da IA agentica**: numero totale di hit sui tuoi URL da agenti IA.
* **Hit di referral da LLM**: numero totale di hit indirizzati ai tuoi URL da risposte generate dall’IA.

Gli indicatori di tendenza per ogni metrica di panoramica mostrano le variazioni di questi valori nel tempo, rispetto al periodo precedente.

## I tuoi URL citati

La vista degli URL citati elenca tutti gli URL del tuo brand che sono stati citati nelle risposte generate dall’IA, con le relative metriche. Entrambe le tabelle hanno un campo di ricerca per l’accesso rapido agli argomenti, e puoi personalizzare le metriche visualizzate facendo clic sul pulsante **Configura colonne**. Inoltre, puoi utilizzare l&#39;opzione **Esporta** per scaricare il file .csv della tabella e condividerne gli insight con il tuo team oppure includere la tabella nei rapporti per il management.

![URL citati](/help/dashboards/assets/cited-urls.png)

Vengono fornite le metriche seguenti:

* **URL**: l’URL analizzato.
* **Numero di citazioni**: numero di volte in cui l’URL è stato citato nelle risposte generate dall’IA.
* **Prompt in cui viene citato**: numero di prompt di IA univoci in cui è stato citato l’URL.
* **Categorie**: categorie di prodotti o argomenti associati all’URL.
* **Aree geografiche**: area geografica in cui è stato citato l’URL.
* **Hit da IA agentica**: numero totale di hit sugli URL da agenti IA.
* **Hit di referral**: numero di hit indirizzati agli URL dalle risposte generate dall’IA.

## URL di tendenza in competizione per le citazioni

La vista URL di tendenza in competizione per le citazioni evidenzia gli URL esterni attualmente citati nelle risposte rilevanti per il tuo brand, misurando chi sta ottenendo più citazioni nel tuo spazio. La tabella dei dati contiene un campo di ricerca per l’accesso rapido a URL specifici. Inoltre, puoi utilizzare l&#39;opzione **Esporta** per scaricare il file .csv della tabella e condividerne gli insight con il tuo team oppure includere la tabella nei rapporti per il management.

![URL di tendenza in competizione per le citazioni](/help/dashboards/assets/trend-url.png)

Vengono fornite le metriche seguenti:

* **URL**: l’URL analizzato
* **Tipo di contenuto**: tipo di contenuto (di proprietà, social, earned media, altri).
* **Numero di citazioni**: numero di volte in cui l’URL è stato citato nelle risposte generate dall’IA.
* **Prompt in cui viene citato**: numero di prompt di IA univoci in cui è stato citato l’URL.
* **Categorie**: categorie di prodotti o argomenti associati all’URL.
* **Aree geografiche**: area geografica in cui è stato citato l’URL.

### Finestra Dettagli

Nelle viste delle citazioni e delle tendenze, alla fine di ogni riga di URL è presente un pulsante **Dettagli** . Quando fai clic su questo pulsante, viene visualizzata una finestra separata con ulteriori dettagli. La finestra dei dettagli mostra la frequenza con cui l’URL viene citato, <!--the sentiment of AI responses where it is mentioned,--> gli argomenti e i prompt in cui viene visualizzato e le tendenze in termini di traffico da IA agentica e da referral nel tempo (per gli URL di proprietà).

![Finestra Dettagli](/help/dashboards/assets/details-url.png)
