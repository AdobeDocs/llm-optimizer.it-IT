---
title: Controllo degli accessi
description: Scopri le differenze tra gli utenti assegnati ai prodotti e quelli organizzativi in Adobe LLM Optimizer, cosa visualizzano gli utenti di sola lettura nell’interfaccia utente e come gli amministratori assegnano l’accesso in Adobe Admin Console.
feature: Customer Configuration
autotag-review: '2026-05-15T17:26:43.837Z'
TQID: 'https://experienceleague.adobe.com/hJpQQpuHBRMdKT5oKA9z0Y8H3d3p6To-n2hWKrXgZsQ'
product_v2:
  - id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2:
  - id: d1956731-2adb-4bb7-8301-2b239254ac72
subfeature_v2:
  - id: b704f6a0-b2fb-4df0-9177-9753751004f5
topic_v2:
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 7a92587197cf6a9eec6b01bd4eaeeaf1194d3088
workflow-type: tm+mt
source-wordcount: 618
ht-degree: 4%

---


# Controllo degli accessi

Adobe LLM Optimizer supporta il controllo degli accessi di base, in base agli utenti tipo. Questa funzionalità è disponibile solo per **clienti paganti** ed è abilitata su richiesta. Non è disponibile per i clienti di prova.

>[!IMPORTANT]
>
>Per richiedere l’accesso a questa funzione, i clienti paganti devono contattare il proprio account manager Adobe.

## Utenti assegnati ai prodotti {#product-assigned-users}

Se sei assegnato al prodotto, hai le stesse funzionalità di un utente organizzativo standard, oltre alle seguenti autorizzazioni:

* Accesso in scrittura in [Configurazione cliente](/help/dashboards/customer-configuration.md) per prompt, categorie, argomenti e impostazioni correlate.
* Distribuisci [Ottimizza in Edge](/help/dashboards/optimize-at-edge/overview.md) ottimizzazioni e gestisci suggerimenti.
* Gestisci configurazioni console di Google Search.
* Gestisci l’ottimizzazione nelle configurazioni Edge e CDN.
* Effettua l’onboarding di un nuovo sito.

## Utenti organizzativi {#organizational-users}

Gli utenti dell&#39;organizzazione sono utenti standard che sono **non** assegnati al prodotto. Se sei un utente dell&#39;organizzazione, hai accesso **in sola lettura** alle [dashboard di LLM Optimizer](/help/dashboards/dashboards-overview.md) e alle visualizzazioni correlate. Si applicano le seguenti restrizioni.

### Configurazione cliente {#customer-configuration-restrictions}

* **Le richieste di caricamento** sono disabilitate.
* La gestione e la modifica di prompt, categorie, argomenti e aree geografiche è disattivata.

  ![Restrizioni alla configurazione del cliente per utenti di sola lettura](/help/dashboards/assets/access-control-customer-configuration.png)

### Configurazione CDN (configurazione cliente) {#cdn-configuration-restrictions}

* **La rete CDN integrata** è disabilitata (gli utenti di sola lettura non possono aggiungere un provider CDN).
* **Eliminazione rete CDN** disabilitata (gli utenti di sola lettura non possono rimuovere una configurazione CDN esistente).
* Il pulsante **Invia** nella finestra di dialogo di onboard della rete CDN è disabilitato (gli utenti di sola lettura non possono completare l&#39;installazione della rete CDN).

  ![Restrizioni alla configurazione CDN per utenti di sola lettura](/help/dashboards/assets/access-control-cdn-configuration.png)

### Presenza dei brand: approfondimenti sui dati {#brand-presence-restrictions}

* I pulsanti **Elimina** accanto agli argomenti sono nascosti (gli utenti di sola lettura non possono rimuovere gli argomenti dal monitoraggio).
* I pulsanti **Elimina** accanto ai prompt sono nascosti (gli utenti di sola lettura non possono rimuovere i prompt dal tracciamento).

  ![Presenza dei brand azioni nascoste per utenti di sola lettura](/help/dashboards/assets/access-control-brand-presence.png)

### Opportunità di traffico agente (opportunità pagina di errore) {#agentic-opportunities}

Per opportunità quali 404, 403 e 503 pagine di errore:

* **Ottimizzazione distribuzione** è nascosto.
* Un avviso informativo spiega che è necessario l’accesso alla distribuzione.

  ![Ottimizzazione della distribuzione nascosta nelle opportunità di traffico agente](/help/dashboards/assets/access-control-agentic-deploy.png)

### Altre pagine opportunità {#other-opportunities}

Il comportamento di sola lettura si applica anche a tipi di opportunità quali:

* Sommario
* Riepilogazione
* Leggibilità
* Pre-rendering
* Titoli
* Domande frequenti
* Dati strutturati mancanti
* Opportunità di patch generica

Per queste pagine:

* **L&#39;ottimizzazione della distribuzione** è nascosta quando l&#39;utente non dispone dell&#39;accesso alla distribuzione.
* Un avviso in linea spiega che è necessario l’accesso alla distribuzione. Il messaggio è simile al seguente: *Distribuisci accesso richiesto: non si dispone dell&#39;autorizzazione per distribuire ottimizzazioni o gestire suggerimenti. Contattare l&#39;amministratore per richiedere l&#39;accesso.*
* La barra inferiore fissa con azioni di distribuzione è nascosta.

  ![Avviso in linea quando è richiesto l&#39;accesso alla distribuzione](/help/dashboards/assets/access-control-deploy-alert.png)

  ![Azioni di distribuzione Ottimizza in Edge nascoste per gli utenti di sola lettura](/help/dashboards/assets/access-control-optimize-at-edge.png)

### Configurazione del prompt della console Google Search {#gsc-restrictions}

* Le azioni di gestione e connessione sono disabilitate o nascoste.
* La colonna delle azioni utilizzata per aggiungere i prompt è nascosta.

  ![Restrizioni alla configurazione della console di Google Search](/help/dashboards/assets/access-control-gsc.png)

### Incorpora un nuovo sito {#onboarding-restrictions}

* L’onboarding di un nuovo sito è disabilitato per gli utenti senza controllo degli accessi.

  ![Nuovo sito integrato disabilitato](/help/dashboards/assets/access-control-onboarding.png)

## Assegnare il prodotto a un utente o gruppo {#assign-product}

Un **amministratore di sistema** della tua organizzazione può utilizzare [Adobe Admin Console](https://adminconsole.adobe.com/) per assegnare Adobe LLM Optimizer a un utente o a un gruppo.

1. Accedi a [Adobe Admin Console](https://adminconsole.adobe.com/) con un account con diritti amministrativi per la tua organizzazione.
1. Assegna il profilo di prodotto Adobe LLM Optimizer (o la licenza di prodotto equivalente della tua organizzazione) all’utente o al gruppo che deve ricevere le funzionalità assegnate al prodotto.

Per i passaggi dettagliati, vedi [Gestione dei prodotti in Admin Console](https://helpx.adobe.com/enterprise/using/manage-products.html) e [Gestione dei gruppi di utenti](https://helpx.adobe.com/it/enterprise/using/user-groups.html).

>[!NOTE]
>
>I flussi di schermo in Adobe Admin Console possono cambiare tra una versione e l’altra. Se le opzioni di cui sopra non corrispondono alla console, utilizza i collegamenti di aiuto interni al prodotto in Adobe Admin Console o contatta il team del tuo account Adobe.
