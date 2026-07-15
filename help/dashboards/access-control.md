---
title: Controllo degli accessi
description: Scopri le differenze tra utenti assegnati ai prodotti e utenti organizzativi in Adobe LLM Optimizer, cosa possono vedere gli utenti di sola lettura nell’interfaccia utente e come gli amministratori assegnano l’accesso in Adobe Admin Console.
feature: Customer Configuration
autotag-review: '2026-07-15T16:44:26.227Z'
TQID: 'https://experienceleague.adobe.com/km1BB-gqTl1U92LhHxbXtoH4MTA2tLXS3mPx5u9rEoQ'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: d1956731-2adb-4bb7-8301-2b239254ac72
subfeature_v2: id: d622681e-b12a-44e4-b49f-91c12f18b52b
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1id: e1e0219c-f879-479f-8427-888ed2a6e9c2id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 2705cf26faea9c09817bbdcec4b4c531552df7ba
workflow-type: tm+mt
source-wordcount: 618
ht-degree: 100%

---


# Controllo degli accessi

Adobe LLM Optimizer supporta il controllo degli accessi di base, in funzione degli utenti tipo. Questa funzionalità è disponibile solo per i **clienti a pagamento** ed è abilitata su richiesta. Non è disponibile per chi usa la versione di prova.

>[!IMPORTANT]
>
>Per richiedere l’accesso a questa funzione, i clienti a pagamento devono contattare il proprio account manager Adobe.

## Utenti assegnati ai prodotti {#product-assigned-users}

Se sei assegnato al prodotto, disponi delle stesse funzionalità di un utente organizzativo standard, oltre alle seguenti autorizzazioni:

* Accesso in scrittura in [Configurazione cliente](/help/dashboards/customer-configuration.md) per prompt, categorie, argomenti e impostazioni correlate.
* Distribuzione delle ottimizzazioni di [Ottimizza su Edge](/help/dashboards/optimize-at-edge/overview.md) e gestione dei suggerimenti.
* Gestione delle configurazioni di Google Search Console.
* Gestione delle configurazioni “Ottimizza su Edge” e “CDN”.
* Esegui l’onboarding di un nuovo sito.

## Utenti organizzativi {#organizational-users}

Gli utenti organizzativi sono utenti standard **non** assegnati al prodotto. Se sei un utente organizzativo, disponi dell’accesso **in sola lettura** alle [dashboard di LLM Optimizer](/help/dashboards/dashboards-overview.md) e alle viste correlate. Si applicano le seguenti restrizioni.

### Configurazione cliente {#customer-configuration-restrictions}

* **I prompt di caricamento** sono disabilitati.
* La gestione e la modifica di prompt, categorie, argomenti e aree geografiche è disattivata.

  ![Restrizioni alla configurazione cliente per utenti di sola lettura](/help/dashboards/assets/access-control-customer-configuration.png)

### Configurazione CDN (Configurazione cliente) {#cdn-configuration-restrictions}

* **Esegui onboarding** è disabilitato (gli utenti di sola lettura non possono aggiungere un provider CDN).
* **Elimina CDN** è disabilitato (gli utenti di sola lettura non possono rimuovere una configurazione CDN esistente).
* Il pulsante **Invia** nella finestra di dialogo di onboarding della CDN è disabilitato (gli utenti di sola lettura non possono completare la configurazione della CDN).

  ![Restrizioni alla configurazione CDN per utenti di sola lettura](/help/dashboards/assets/access-control-cdn-configuration.png)

### Presenza del brand: insight sui dati {#brand-presence-restrictions}

* I pulsanti **Elimina** accanto agli argomenti sono nascosti (gli utenti di sola lettura non possono rimuovere gli argomenti dal tracciamento).
* I pulsanti **Elimina** accanto ai prompt sono nascosti (gli utenti di sola lettura non possono rimuovere i prompt dal tracciamento).

  ![Azioni della presenza del brand nascoste per gli utenti di sola lettura](/help/dashboards/assets/access-control-brand-presence.png)

### Opportunità di traffico da IA agentica (opportunità pagina di errore) {#agentic-opportunities}

Per opportunità quali le pagine di errore 404, 403 e 503:

* **Implementa ottimizzazione** è nascosto.
* Un avviso informativo spiega che è obbligatorio l’accesso all’implementazione.

  ![Implementa ottimizzazione nascosto nelle opportunità di traffico da IA agentica](/help/dashboards/assets/access-control-agentic-deploy.png)

### Altre pagine di opportunità {#other-opportunities}

Il comportamento di sola lettura si applica anche a tipi di opportunità quali:

* Indice
* Riepilogazione
* Leggibilità
* Pre-rendering
* Titoli
* Domande frequenti
* Dati strutturati mancanti
* Opportunità di patch generica

Per queste pagine:

* **Implementa ottimizzazione** è nascosto quando l’utente non dispone dell’accesso all’implementazione.
* Un avviso in linea spiega che è obbligatorio l’accesso all’implementazione. Il messaggio è simile al seguente: *Accesso all’implementazione obbligatorio: non si dispone delle autorizzazioni per implementare ottimizzazioni o gestire suggerimenti. Contatta il tuo amministratore per richiedere l’accesso.*
* La barra persistente in basso con le azioni di implementazione è nascosta.

  ![Avviso in linea quando è obbligatorio l’accesso all’implementazione](/help/dashboards/assets/access-control-deploy-alert.png)

  ![Azioni per l’implementazione di Ottimizza su Edge nascoste per gli utenti di sola lettura](/help/dashboards/assets/access-control-optimize-at-edge.png)

### Configurazione dei prompt per Google Search Console {#gsc-restrictions}

* Le azioni di gestione e connessione sono disabilitate o nascoste.
* La colonna delle azioni utilizzata per aggiungere i prompt è nascosta.

  ![Restrizioni alla configurazione di Google Search Console](/help/dashboards/assets/access-control-gsc.png)

### Eseguire l’onboarding di un nuovo sito {#onboarding-restrictions}

* L’onboarding di un nuovo sito è disabilitato per gli utenti senza controllo di accesso.

  ![Onboarding di un nuovo sito disabilitato](/help/dashboards/assets/access-control-onboarding.png)

## Assegnare il prodotto a un utente o gruppo {#assign-product}

Un **amministratore di sistema** della tua organizzazione può utilizzare [Adobe Admin Console](https://adminconsole.adobe.com/) per assegnare Adobe LLM Optimizer a un utente o a un gruppo.

1. Accedi ad [Adobe Admin Console](https://adminconsole.adobe.com/) con un account con diritti amministrativi per la tua organizzazione.
1. Assegna il profilo del prodotto Adobe LLM Optimizer (o il diritto per un prodotto equivalente della tua organizzazione) all’utente o al gruppo che deve ricevere le funzionalità assegnate al prodotto.

Per i passaggi dettagliati, consulta [Gestione dei prodotti in Admin Console](https://helpx.adobe.com/it/enterprise/using/manage-products.html) e [Gestire i gruppi di utenti](https://helpx.adobe.com/it/enterprise/using/user-groups.html).

>[!NOTE]
>
>I flussi di schermo in Adobe Admin Console possono cambiare da una versione all’altra. Se le opzioni precedenti non corrispondono alla tua console, utilizza i collegamenti di aiuto interni del prodotto in Adobe Admin Console o contatta il team Adobe Account.
