---
title: Ottimizzazione nella rete edge - Akamai (BYOCDN)
description: Scopri come configurare Akamai BYOCDN per l’ottimizzazione nella rete edge in LLM Optimizer.
feature: Opportunities
autotag-review: '2026-05-15T17:34:47.891Z'
TQID: 'https://experienceleague.adobe.com/oGtqsnvHYn0BSNLl40-KpVl0TjCZHESRgH1LcVmjOiY'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: d1956731-2adb-4bb7-8301-2b239254ac72
subfeature_v2: id: d23587d6-14d6-4e3f-9ee1-cc18623832e1
source-git-commit: 34837b04c48141b8c3657b8f07cb3c2e4852a9ea
workflow-type: tm+mt
source-wordcount: 809
ht-degree: 100%

---


# Akamai (BYOCDN)

Questa configurazione indirizza il traffico da IA agentica (richieste da bot IA e da agenti utente LLM) al servizio back-end Edge Optimize (`live.edgeoptimize.net`). Le persone e i bot SEO continuano a ricevere come al solito i contenuti trasmessi dalla tua origine. Per testare la configurazione, al termine cerca nella risposta l’intestazione `x-edgeoptimize-request-id`.

**Prerequisiti**

Prima di configurare le regole di Akamai Property Manager, assicurati di:

* aver accesso ad Akamai Property Manager per il tuo dominio;
* aver recuperato dall’interfaccia di LLM Optimizer una chiave API del servizio Edge Optimize. Per la procedura, consulta [Recuperare le chiavi API](/help/dashboards/optimize-at-edge/retrieve-api-keys.md#production-api-key).
* (Facoltativo) Per verificare l’indirizzamento in fase di staging, consulta [Chiave API di staging](/help/dashboards/optimize-at-edge/retrieve-api-keys.md#staging-api-key-optional).

**Configurazione**

La seguente regola di Akamai Property Manager indirizza il traffico della pagina HTML da IA agentica verso il servizio Edge Optimize. La configurazione include i seguenti passaggi:

**1. Imposta i criteri di indirizzamento (corrispondenza per agenti utente e traffico HTML)**

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

**2. Imposta il comportamento di origine e SSL**

Imposta l’origine come `live.edgeoptimize.net` e abbina SAN a `*.edgeoptimize.net`

>[!NOTE]
>
>Se l’attivazione della proprietà non riesce dopo aver aggiunto la regola Ottimizza su rete Edge, verifica se la regola utilizza una modalità di verifica SSL del server di origine diversa da quella predefinita. In tal caso, aggiorna la regola Ottimizza su rete Edge in modo che corrisponda alla regola predefinita. Ad esempio, se la regola predefinita utilizza **Impostazioni della piattaforma**, utilizza anche qui le **Impostazioni della piattaforma**. Se non riesci a utilizzare l’impostazione richiesta, contatta l’assistenza clienti di Akamai.

![Imposta il comportamento di origine e SSL](/help/assets/optimize-at-edge/akamai-step2-origin.png)

**3. Imposta la variabile chiave della cache**

Imposta la variabile della chiave della cache `PMUSER_EDGE_OPTIMIZE_CACHE_KEY` su `LLMCLIENT=TRUE;X_FORWARDED_HOST={{builtin.AK_HOST}}`

![Imposta la variabile chiave della cache](/help/assets/optimize-at-edge/akamai-step3-cachekey.png)

**4. Regole di memorizzazione in cache**

![Regole di memorizzazione in cache](/help/assets/optimize-at-edge/akamai-step4-rules.png)

**5. Modifica le intestazioni delle richieste in ingresso**

Imposta le seguenti intestazioni per le richieste in entrata:
`x-edgeoptimize-api-key` verso la chiave API recuperata da LLMO
`x-edgeoptimize-config` a `LLMCLIENT=TRUE;`
`x-edgeoptimize-url` a `{{builtin.AK_URL}}`

![Modifica le intestazioni delle richieste in ingresso](/help/assets/optimize-at-edge/akamai-step5-request.png)

**Consenti Ottimizza su rete Edge tramite le regole del firewall (facoltativo)**

{{waf-allowlist-setup}}

![Imposta l’intestazione x-edgeoptimize-fetcher-key in Property Manager](/help/assets/optimize-at-edge/akamai-step10-fetcher-key.png)

>[!NOTE]
>
>Inoltre, inserisci l’agente utente `*AdobeEdgeOptimize/1.0*` e l’intestazione `x-edgeoptimize-fetcher-key` all’elenco Consentiti in Akamai Bot Manager.

**6. Modifica le intestazioni delle risposte in ingresso**

![Modifica le intestazioni delle risposte in ingresso](/help/assets/optimize-at-edge/akamai-step6-response.png)

**7. Modifica l’ID cache**

![Modifica l’ID cache](/help/assets/optimize-at-edge/akamai-step7-cacheid.png)

**8. Modifica le intestazioni delle richieste in uscita**

Imposta l’intestazione `x-forwarded-host` su `{{builtin.AK_HOST}}`

![Modifica le intestazioni delle richieste in uscita](/help/assets/optimize-at-edge/akamai-step8-outgoing-request.png)

**9. Failover del sito**

La configurazione di failover del sito è composta da due parti: il comportamento di failover (che viene configurato all’interno della regola di indirizzamento optimize-at-edge principale) e una regola distinta per l’intestazione a scopo di test del failover.

**9a. Comportamento di failover del sito (nella regola di indirizzamento optimize-at-edge principale)**

Nella regola di indirizzamento principale, configura il comportamento di failover del sito e lo snippet XML avanzato come indicato di seguito:

>[!IMPORTANT]
>
>Lo snippet XML in questo passaggio richiede il comportamento **Avanzato**. In alcuni ambienti Akamai, questo comportamento non è disponibile per la modifica self-service. Se non visualizzi l’opzione **Avanzato**, contatta il tuo team di account Akamai o l’assistenza Akamai per abilitare la configurazione necessaria.

![Failover del sito](/help/assets/optimize-at-edge/akamai-step9-failover.png)

Aggiungi l’intestazione di richiesta `x-edgeoptimize-request` con il valore `fo` tramite XML avanzato:

```
<forward:availability.fail-action2>
<add-header>
<status>on</status>
<name>x-edgeoptimize-request</name>
<value>fo</value>
</add-header>
</forward:availability.fail-action2>
```

![Comportamenti di failover](/help/assets/optimize-at-edge/akamai-step9-failover-behaviors.png)

**9b. Regola intestazione per test del failover (regola di pari livello)**

>[!IMPORTANT]
>
>Crea la regola **EdgeOptimize Failover - Test Header** come una regola **sibiling** (di pari livello) rispetto alle regole di indirizzamento, **non** nidificata al loro interno. Nella struttura delle regole di Akamai Property Manager, la gerarchia si presenterà così:
>
>```
>▼ Parent Rule
>   ▶ Optimize at Edge Routing     ← routing rule
>       EdgeOptimize Failover - Test Header       ← sibling, same level
>```
>
>In questo modo la regola per l’intestazione del test di failover viene valutata per **tutte** le regole di indirizzamento, non solo per una di esse.
>
>Accertati inoltre che la regola di **indirizzamento Ottimizza su rete Edge** non venga sovrascritta da alcuna regola corrispondente successiva che modifichi l’origine, il comportamento di caching o l’ID della cache per le stesse richieste. Se un’altra regola di corrispondenza reimposta questi comportamenti, l’indirizzamento o il caching di Ottimizza su rete Edge potrebbero non funzionare come previsto.

Se il valore dell’intestazione della richiesta `x-edgeoptimize-request` è `fo`, imposta l’intestazione della risposta in uscita `x-edgeoptimize-fo` su `true`.

![Regole di failover](/help/assets/optimize-at-edge/akamai-step9-failover-rules.png)

Il failover del sito fa sì che, se il servizio Edge Optimize restituisce un errore `4XX` o `5XX`, la richiesta viene indirizzata automaticamente all’origine predefinita, in modo che l’utente finale riceva comunque una risposta.

| Scenario | Comportamento |
| --- | --- |
| Il servizio Edge Optimize restituisce `2XX` | Al client viene trasmessa una risposta ottimizzata. |
| Il servizio Edge Optimize restituisce `4XX` o `5XX` | La richiesta viene indirizzata all’origine predefinita. |

**Verificare la configurazione**

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
| `x-edgeoptimize-fo` | Presente solo in caso di failover (valore: `1`) | Assente |

{{verify-routing-status-in-ui}}

{{return-to-overview}}
