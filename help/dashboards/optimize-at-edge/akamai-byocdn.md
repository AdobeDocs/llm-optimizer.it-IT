---
title: Ottimizzazione nella rete edge - Akamai (BYOCDN)
description: Scopri come configurare Akamai BYOCDN per l’ottimizzazione nella rete edge in LLM Optimizer.
feature: Opportunities
autotag-review: '2026-07-15T17:40:02.356Z'
TQID: 'https://experienceleague.adobe.com/XlHpXbtxqPl-XQQKWeQc3rbsizCT7U0TF1bQkyv0iM8'
product_v2:
  - id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2:
  - id: d1956731-2adb-4bb7-8301-2b239254ac72
  - id: e1b649f0-0a61-46e4-9082-64d5cb2576c6
  - id: ef4e63f5-cb4d-462d-bf9a-1f617edf2a3a
  - id: e0828736-236a-487b-a478-5a635455eadc
subfeature_v2:
  - id: d23587d6-14d6-4e3f-9ee1-cc18623832e1
  - id: e06fae5f-830b-4222-a469-b5e148d36465
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 4f0c6d398e2aab337485b7e26cf6f2aba56375fd
workflow-type: tm+mt
source-wordcount: 795
ht-degree: 70%

---


# Akamai (BYOCDN)

Questa configurazione indirizza il traffico da IA agentica (richieste da bot IA e da agenti utente LLM) al servizio back-end Edge Optimize (`live.edgeoptimize.net`). Le persone e i bot SEO continuano a ricevere come al solito i contenuti trasmessi dalla tua origine. Per testare la configurazione, al termine cerca nella risposta l’intestazione `x-edgeoptimize-request-id`.

**Prerequisiti**

Prima di impostare le regole di Gestione proprietà Akamai, assicurati di disporre di:

* aver accesso ad Akamai Property Manager per il tuo dominio;
* aver recuperato dall’interfaccia di LLM Optimizer una chiave API del servizio Edge Optimize. Per la procedura, consulta [Recuperare le chiavi API](/help/dashboards/optimize-at-edge/retrieve-api-keys.md#production-api-key).
* (Facoltativo) Per verificare l’indirizzamento in fase di staging, consulta [Chiave API di staging](/help/dashboards/optimize-at-edge/retrieve-api-keys.md#staging-api-key-optional).

**Configurazione**

La seguente regola di Akamai Property Manager indirizza il traffico della pagina HTML da IA agentica verso il servizio Edge Optimize. La configurazione include i seguenti passaggi:

## &#x200B;1. Impostare i criteri di routing (corrispondenza traffico agente utente e HTML)

Imposta l’indirizzamento per i seguenti agenti utente:

```
 *AdobeEdgeOptimize-AI*
 *ChatGPT-User*
 *GPTBot*
 *OAI-SearchBot*
 *PerplexityBot*
 *Perplexity-User*
 *ClaudeBot*
 *Claude-User*
 *Claude-SearchBot*
```

>[!NOTE]
>
>Applica la regola di indirizzamento Ottimizza su rete Edge solo al traffico delle pagine HTML da IA agentica. Una configurazione comune prevede l’utilizzo di criteri lato richiesta come **Estensione file** per far corrispondere `html` e `EMPTY_STRING` per gli URL di pagine senza estensione. Se il tuo sito fornisce codice HTML da altri modelli di URL o include indirizzamenti senza estensione che non portano a pagine (ad esempio, endpoint API), perfeziona la regola con ulteriori criteri basati sul percorso.

![Imposta i criteri di indirizzamento](/help/assets/optimize-at-edge/akamai-step1-routing.png)

## &#x200B;2. Impostare il comportamento di Origin e SSL

Imposta l’origine come `live.edgeoptimize.net` e abbina SAN a `*.edgeoptimize.net`

>[!NOTE]
>
>Se l’attivazione della proprietà non riesce dopo aver aggiunto la regola Ottimizza su rete Edge, verifica se la regola utilizza una modalità di verifica SSL del server di origine diversa da quella predefinita. In tal caso, aggiorna la regola Ottimizza su rete Edge in modo che corrisponda alla regola predefinita. Ad esempio, se la regola predefinita utilizza **Impostazioni della piattaforma**, utilizza anche qui le **Impostazioni della piattaforma**. Se non riesci a utilizzare l’impostazione richiesta, contatta l’assistenza clienti di Akamai.

![Imposta il comportamento di origine e SSL](/help/assets/optimize-at-edge/akamai-step2-origin.png)

## &#x200B;3. Imposta variabile chiave cache

Imposta la variabile della chiave della cache `PMUSER_EDGE_OPTIMIZE_CACHE_KEY` su `LLMCLIENT=TRUE;X_FORWARDED_HOST={{builtin.AK_HOST}}`

![Imposta la variabile chiave della cache](/help/assets/optimize-at-edge/akamai-step3-cachekey.png)

## &#x200B;4. Regole di memorizzazione in cache

![Regole di memorizzazione in cache](/help/assets/optimize-at-edge/akamai-step4-rules.png)

## &#x200B;5. Modifica intestazioni richieste in ingresso

Imposta le seguenti intestazioni per le richieste in entrata:
`x-edgeoptimize-api-key` verso la chiave API recuperata da LLMO
`x-edgeoptimize-config` a `LLMCLIENT=TRUE;`
`x-edgeoptimize-url` a `{{builtin.AK_URL}}`

![Modifica le intestazioni delle richieste in ingresso](/help/assets/optimize-at-edge/akamai-step5-request.png)

## Consenti ottimizzazione in Edge tramite regole firewall (facoltativo)

{{waf-allowlist-setup}}

![Imposta l’intestazione x-edgeoptimize-fetcher-key in Property Manager](/help/assets/optimize-at-edge/akamai-step10-fetcher-key.png)

>[!NOTE]
>
>Inoltre, inserisci l’agente utente `*AdobeEdgeOptimize/1.0*` e l’intestazione `x-edgeoptimize-fetcher-key` all’elenco Consentiti in Akamai Bot Manager.

## &#x200B;6. Modifica intestazioni di risposta in ingresso

![Modifica le intestazioni delle risposte in ingresso](/help/assets/optimize-at-edge/akamai-step6-response.png)

## &#x200B;7. Modifica ID cache

![Modifica l’ID cache](/help/assets/optimize-at-edge/akamai-step7-cacheid.png)

## &#x200B;8. Modifica intestazioni richieste in uscita

Imposta l’intestazione `x-forwarded-host` su `{{builtin.AK_HOST}}`

![Modifica le intestazioni delle richieste in uscita](/help/assets/optimize-at-edge/akamai-step8-outgoing-request.png)

## &#x200B;9. Failover del sito

La configurazione del failover del sito è composta da due parti: un comportamento di failover all’interno della regola principale di routing Optimize at Edge e una regola di pari livello che aggiunge un’intestazione di risposta quando si verifica il fallback.

### 9 bis. Configurare il comportamento di failover del sito

All&#39;interno della regola di routing principale Ottimizza in Edge, creare una regola figlio denominata **Comportamento failover sito**. Impostalo su **Corrispondenza con qualsiasi** e aggiungi i seguenti criteri:

* **Il codice di stato della risposta** è compreso tra `400` e `599`.
* **Timeout origine** è `Yes`.

![Failover del sito](/help/assets/optimize-at-edge/akamai-step9-failover.png)

![Configurare il comportamento di failover del sito](/help/assets/optimize-at-edge/akamai-step9-failover-settings.png)

### 9 ter. Configurare la regola di intestazione della risposta di failover

>[!IMPORTANT]
>
>Crea la regola **EdgeOptimize Failover - Test Header** come una regola **sibiling** (di pari livello) rispetto alle regole di indirizzamento, **non** nidificata al loro interno. Nella struttura delle regole di Akamai Property Manager, la gerarchia si presenterà così:
>
>```
>▼ Optimize at Edge                         ← parent rule group
>   ▼ Optimize at Edge Routing               ← routing child
>       Site Failover Behavior                 ← nested child
>   EdgeOptimize Failover - Test Header      ← sibling of routing child
>```
>
>La regola di pari livello viene valutata quando Akamai ricrea la richiesta non riuscita per il nome host originale. Il criterio della chiave API nella regola di indirizzamento impedisce che la richiesta venga inviata nuovamente ad Edge Optimize.
>
>Accertati inoltre che la regola di **indirizzamento Ottimizza su rete Edge** non venga sovrascritta da alcuna regola corrispondente successiva che modifichi l’origine, il comportamento di caching o l’ID della cache per le stesse richieste. Se un’altra regola di corrispondenza reimposta questi comportamenti, l’indirizzamento o il caching di Ottimizza su rete Edge potrebbero non funzionare come previsto.

![Configurare la regola di intestazione della risposta di failover](/help/assets/optimize-at-edge/akamai-step9-failover-header.png)

Il failover del sito assicura che, se Edge Optimize restituisce un errore o un timeout, Akamai ricrei la richiesta per il nome host originale in modo che il visitatore riceva comunque la normale risposta del sito.

| Scenario | Comportamento |
| --- | --- |
| Il servizio Edge Optimize restituisce `2XX` o `3XX` | Viene trasmessa la risposta ottimizzata. `x-edgeoptimize-request-id` è presente. |
| Edge Optimize restituisce `4XX`-`5XX` oppure l&#39;origine scade | La richiesta viene ricreata per il nome host originale. La risposta include `x-edgeoptimize-fo: true`. |

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
| `x-edgeoptimize-fo` | Presente solo in caso di failover (valore: `true`) | Assente |

{{verify-routing-status-in-ui}}

{{return-to-overview}}
