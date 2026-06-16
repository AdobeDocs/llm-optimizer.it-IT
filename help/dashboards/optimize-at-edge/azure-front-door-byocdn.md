---
title: Ottimizza in Edge - Azure Front Door (BYOCDN)
description: Scopri come configurare Azure Front Door BYOCDN per l’ottimizzazione in Edge in LLM Optimizer.
feature: Opportunities
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: d1956731-2adb-4bb7-8301-2b239254ac72
subfeature_v2: id: d23587d6-14d6-4e3f-9ee1-cc18623832e1
source-git-commit: 1d07ce1820e2688a130e410ee88ab329d628356a
workflow-type: tm+mt
source-wordcount: 768
ht-degree: 24%

---


# Porta anteriore Azure (BYOCDN)

Questa configurazione indirizza il traffico da IA agentica (richieste da bot IA e da agenti utente LLM) al servizio back-end Edge Optimize (`live.edgeoptimize.net`). Le persone e i bot SEO continuano a ricevere come al solito i contenuti trasmessi dalla tua origine. Per testare la configurazione, al termine cerca nella risposta l’intestazione `x-edgeoptimize-request-id`.

Azure Front Door non esegue codice personalizzato sul server Edge. Il routing è configurato utilizzando un **set di regole** insieme a un **gruppo di origine** dedicato per Edge Optimize. Il failover viene gestito dalle sonde di integrità del gruppo di origine basate sulla priorità di Azure Front Door.

**Prerequisiti**

Prima di impostare le regole di instradamento di Azure Front Door, verificare di disporre dei seguenti elementi:

* Accesso al profilo Azure Front Door.
* aver recuperato dall’interfaccia di LLM Optimizer una chiave API del servizio Edge Optimize. Per la procedura, consulta [Recuperare le chiavi API](/help/dashboards/optimize-at-edge/retrieve-api-keys.md#production-api-key).
* (Facoltativo) Per verificare l’indirizzamento in fase di staging, consulta [Chiave API di staging](/help/dashboards/optimize-at-edge/retrieve-api-keys.md#staging-api-key-optional).

## Passaggio 1: creare un gruppo di origine per Edge Optimize

Il profilo Azure Front Door dispone già di un gruppo di origine predefinito che punta all’origine. Crea un gruppo di origine **nuovo** per Edge Optimize:

* **Nome:** `edge-optimize-origin-group`
* **Origini (failover basato su priorità):**
   * **Priorità 1** - `live.edgeoptimize.net` (intestazione host di origine: `live.edgeoptimize.net`)
   * **Priorità 2**: endpoint di dominio (ad esempio, `www.example.com`). Questo è per il failover: se Edge Optimize non è integro, le richieste vengono indirizzate al dominio, che entra nuovamente in Azure Front Door e viene fornito dall’origine predefinita.
* **Sonde di integrità:** **Abilitate**
   * Percorso: `/health/<your-domain>` (ad esempio, `/health/www.example.com`)
   * Protocollo: HTTPS
   * Intervallo: 225 secondi
* **Affinità sessione:** **Disabilitata**
* **Convalida del nome soggetto certificato:** **Abilitato**

![Edge Ottimizza il gruppo di origine con due origini e due sonde di integrità basate sulla priorità](/help/assets/optimize-at-edge/azure-front-door-origin-group.png)

>[!NOTE]
>
>Il gruppo di origine `edge-optimize-origin-group` visualizza un avviso **&quot;Non associato&quot;** nel portale. Ciò è previsto, poiché vi si fa riferimento tramite una sostituzione del ciclo di lavorazione del set di regole, non direttamente tramite un ciclo di lavorazione.

## Passaggio 2: configurare il percorso

Un percorso predefinito viene in genere creato con il profilo Azure Front Door. Il set di regole (passaggio 3) esegue l’override del gruppo di origine per il traffico agente, pertanto non è necessario alcun percorso separato per Edge Optimize.

## Passaggio 3: creare il set di regole

Vai a **Set di regole** > **Aggiungi un set di regole** e denominalo `EORouting`. Aggiungi tre regole in questo ordine.

![Set di regole EORouting che mostra le regole di stripping dell&#39;intestazione e di routing dei bot](/help/assets/optimize-at-edge/azure-front-door-ruleset-routing.png)

### Regola 1: StripIncomingEOHeaders01

Elimina le intestazioni Edge Optimize in arrivo per impedire lo spoofing. Nessuna condizione - si applica a tutte le richieste. Interrompi valutazione: **Disattivato**.

**Azioni** — Elimina intestazione richiesta per ciascuno di:

* `x-edgeoptimize-url`
* `x-edgeoptimize-config`
* `x-edgeoptimize-api-key`
* `x-edgeoptimize-fetcher-key`

### Regola 2: EOGPTBotRootGET03

Indirizza le richieste bot sui percorsi delle pagine HTML a Edge Optimize. Interrompi valutazione: **Il**.

**Condizioni** (tutte devono corrispondere):

* Metodo di richiesta: **Equal** `GET`
* Percorso richiesta: **RegEx** `(^$|^.*/$|(^|.*/)[^./]+$|^.*\.html$)` (corrisponde alla directory principale del sito, ai percorsi che terminano in `/`, ai percorsi di pagina senza estensione e ai percorsi `.html`)
* Agente utente: **contiene uno di** `chatgpt-user`, `gptbot`, `oai-searchbot`, `adobeedgeoptimize-ai`, `perplexitybot`, `perplexity-user`, `claudebot`, `claude-user`, `claude-searchbot`. Imposta trasformazione stringa su **In minuscolo**.
* `x-edgeoptimize-monitor`: **Non contiene** `1`
* `x-edgeoptimize-request`: **Non contiene nessuno di** `failover`, `1`

**Azioni**:

* Sovrascrittura intestazione richiesta `x-edgeoptimize-url` = `/{url_path}?{query_string}`
* Sovrascrittura intestazione richiesta `x-edgeoptimize-config` = `LLMCLIENT=TRUE;`
* Sovrascrittura intestazione richiesta `x-edgeoptimize-api-key` = `YOUR_API_KEY`
* Sovrascrittura intestazione richiesta `x-edgeoptimize-monitor` = `1`
* Sostituzione configurazione route: gruppo di origine → `edge-optimize-origin-group`, protocollo di inoltro → corrispondenza richiesta in ingresso, memorizzazione nella cache → **Disabilitato**

### Regola 3: HealthProbeRewrite03

Riscrive le richieste del probe di integrità di Azure Front Door in modo che raggiungano l&#39;origine come `/` invece di `/health/<domain>`. Questo consente ad Azure Front Door di monitorare la disponibilità di Edge senza richiedere un endpoint di integrità dedicato sull’origine. Interrompi valutazione: **Il**.

![Regola di riscrittura probe integrità](/help/assets/optimize-at-edge/azure-front-door-ruleset-healthprobe.png)

**Condizioni** (tutte devono corrispondere):

* Percorso URL richiesta: **Inizia con** `/health/`
* `x-fd-healthprobe`: **Contiene** `1`

**Azioni**:

* Riscrittura URL — Schema Source: `/health/`, Destinazione: `/`
* Sovrascrittura intestazione risposta `custom-origin-health` = `routed` (diagnostica — può essere rimossa dopo la verifica)
* Aggiunta intestazione richiesta `user-agent` = ` AdobeEdgeOptimize/1.0` (aggiungere uno spazio iniziale — Azure Front Door aggiunge il valore così com&#39;è)
* Sostituzione configurazione route: gruppo di origine → `default-origin-group`, protocollo di inoltro → corrispondenza richiesta in ingresso, memorizzazione nella cache → **Disabilitato**

## Passaggio 4: associare il set di regole al ciclo di lavorazione

Apri la route, scorri fino alla sezione **Regole** in basso e seleziona il set di regole `EORouting` dal menu a discesa. Se sono presenti set di regole esistenti, utilizzare **Sposta in alto** per posizionare `EORouting` alle **#1**. Le regole di ottimizzazione in Edge intercettano solo il traffico agente e le richieste di loop-back di Edge Optimize: tutto il traffico non viene influenzato dalle altre regole. Salvare e attendere la propagazione (circa 20 minuti).

## Consenti ottimizzazione in Edge tramite regole firewall (facoltativo)

{{waf-allowlist-setup}}

## Verificare la configurazione

Dopo aver completato la configurazione, verifica che il traffico proveniente da bot venga indirizzato al servizio Edge Optimize e che il traffico da persone non sia interessato da alcuna modifica.

**1. Test del traffico da bot (deve risultare ottimizzato)**

Simula una richiesta da un bot IA utilizzando un agente utente da IA agentica:

```
curl -svo /dev/null https://www.example.com/page.html \
  --header "user-agent: chatgpt-user"
```

Se il test ha esito positivo, la risposta contiene l’intestazione `x-edgeoptimize-request-id`, a conferma che la richiesta è stata indirizzata tramite il servizio Edge Optimize:

```
< HTTP/2 200
< x-edgeoptimize-request-id: 50fce12d-0519-4fc6-af78-d928785c1b85
```

**2. Test del traffico da persone (deve risultare NON interessato da modifiche)**

Simula una normale richiesta inserita da una persona nel browser:

```
curl -svo /dev/null https://www.example.com/page.html \
  --header "user-agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36"
```

La risposta **non** deve contenere l’intestazione `x-edgeoptimize-request-id`. Il contenuto della pagina e il tempo di risposta devono risultare identici rispetto a prima che sia stata abilitata la funzione Ottimizza su rete edge.

**3. Differenze tra i due scenari**

| Intestazione | Traffico da bot (ottimizzato) | Traffico da persone (non interessato da modifiche) |
|---|---|---|
| `x-edgeoptimize-request-id` | Presente: contiene un ID di richiesta univoco | Assente |

{{verify-routing-status-in-ui}}

{{return-to-overview}}
