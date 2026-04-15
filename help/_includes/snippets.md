---
source-git-commit: e9309dc8f8d1d81b953483f17dcb424e46d5cd3b
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---
# Snippet

## Passaggi per il recupero della chiave API {#retrieve-byocdn-api-key}

**Passaggi per recuperare la chiave API di produzione Edge Optimize:**

1. In LLM Optimizer, apri **Configurazione cliente** e seleziona la scheda **Configurazione CDN**.

   ![Passa a Configurazione cliente](/help/assets/optimize-at-edge/prereq-customer-config-nav.png)

2. Individua la sezione **Distribuire le ottimizzazioni agli agenti di IA**. Selezionare la casella di controllo **Abilita motore di ottimizzazione**.

   ![Distribuzione ottimizzazioni agli agenti di IA - in sospeso](/help/assets/optimize-at-edge/byocdn-deploy-optimizations-pending.png)

3. Nella finestra di dialogo di conferma, seleziona **Abilita**.

   ![Abilita la finestra di dialogo di conferma del motore di ottimizzazione](/help/assets/optimize-at-edge/byocdn-enable-optimization-engine-dialog.png)

4. Selezionare **Visualizza dettagli**. Nella finestra di dialogo **Dettagli ottimizzazione distribuzione**, copia la **chiave API di produzione** (utilizza **Copia** accanto al campo).

   ![Chiave API di produzione nei dettagli delle ottimizzazioni della distribuzione](/help/assets/optimize-at-edge/byocdn-production-api-key-details.png)

   >[!NOTE]
   >La finestra di dialogo potrebbe indicare che la configurazione non è completa. Questo è previsto fino alla verifica del routing: è comunque possibile copiare la chiave API in modo che il team IT o CDN possa completare la configurazione.

Inoltre, se hai bisogno di assistenza per i passaggi precedenti, contatta il team del tuo account Adobe o `llmo-at-edge@adobe.com`.

## Facoltativo: verifica del routing su un nome host di gestione temporanea {#retrieve-staging-edge-optimize-api-key}

**Facoltativo: verifica del routing in un nome host di gestione temporanea**

Se desideri convalidare il ciclo di produzione in un ambiente inferiore prima di abilitare il ciclo di produzione, puoi configurare un nome host di staging.

**Requisiti**

* Il nome host dell&#39;area di gestione temporanea deve trovarsi nello **stesso dominio registrabile** della produzione (ad esempio, `https://staging.example.com` quando la produzione è `https://www.example.com`).
* Solo **un** dominio di gestione temporanea per sito. Una volta salvato, non è possibile modificarlo senza contattare Adobe.

**Ottieni la chiave API di staging**

1. Apri **Configurazione cliente** e seleziona **Configurazione rete CDN**.
2. In **Distribuisci ottimizzazioni agli agenti di IA**, selezionare **Aggiungi dominio stage** (o **Dominio stage** se è già configurato un dominio di gestione temporanea).
3. Immetti l&#39;URL di gestione temporanea completo, incluso `https://`, e seleziona **Imposta dominio**.
4. Copia la chiave API **staging** dalla finestra di dialogo di conferma.

![Chiave API del dominio di gestione temporanea](/help/assets/optimize-at-edge/byocdn-staging-domain-api-key.png)

Distribuisci le stesse regole di routing nell’ambiente di staging utilizzando la chiave API di staging.

**Verifica traffico bot di staging**

Sostituisci `https://staging.example.com/page.html` con il tuo URL e percorso di staging effettivo. **Operazione completata:** La risposta include l&#39;intestazione `x-edgeoptimize-request-id`.

Se hai bisogno di aiuto, contatta `llmo-at-edge@adobe.com`.

## Verifica dello stato di indirizzamento in LLM Optimizer {#verify-routing-status-in-ui}

Lo stato del routing del traffico può essere controllato anche nell’interfaccia utente di LLM Optimizer. Passa a **Configurazione cliente** e seleziona la scheda **Configurazione CDN**.

![Distribuzione delle ottimizzazioni agli agenti di IA - completata](/help/assets/optimize-at-edge/byocdn-CDN-traffic-routed-tick.png)

## Consentire l’ottimizzazione in Edge tramite le regole del firewall (facoltativo) {#waf-allowlist-setup}

Se la rete CDN utilizza un WAF o un Bot Manager:

* Inserire nell&#39;elenco Consentiti l&#39;agente utente `*AdobeEdgeOptimize/1.0*` nel WAF o nel gestore bot in modo che il servizio Optimize at Edge possa recuperare il contenuto di origine.
* Se il firewall richiede ulteriori verifiche oltre all&#39;agente utente, generare un segreto (ad esempio, `openssl rand -hex 32`) e:
   * Aggiungi `x-edgeoptimize-fetcher-key` con il segreto nelle regole di routing insieme alle altre intestazioni `x-edgeoptimize-*`.
   * Aggiungi una regola di WAF o Bot Manager per consentire le richieste in cui `x-edgeoptimize-fetcher-key` corrisponde allo stesso segreto.
* Ottimizza in Edge inoltra questa intestazione così com’è, sei il proprietario dell’intero ciclo di vita delle chiavi.

## Torna alla panoramica {#return-to-overview}

Per ulteriori informazioni su Ottimizza in Edge, tra cui le opportunità disponibili, i flussi di lavoro di ottimizzazione automatica e le domande frequenti, torna alla [Panoramica sull&#39;ottimizzazione in Edge](/help/dashboards/optimize-at-edge/overview.md).
