---
title: Ottimizzazione nella rete edge - Akamai (BYOCDN)
description: Scopri come configurare Akamai BYOCDN per l’ottimizzazione nella rete edge in LLM Optimizer.
feature: Opportunities
autotag-review: '2026-05-15T17:34:47.891Z'
TQID: 'https://experienceleague.adobe.com/oGtqsnvHYn0BSNLl40-KpVl0TjCZHESRgH1LcVmjOiY'
product_v2:
  - id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2:
  - id: d1956731-2adb-4bb7-8301-2b239254ac72
subfeature_v2:
  - id: d23587d6-14d6-4e3f-9ee1-cc18623832e1
source-git-commit: 7a92587197cf6a9eec6b01bd4eaeeaf1194d3088
workflow-type: tm+mt
source-wordcount: 809
ht-degree: 61%

---


# Akamai (BYOCDN)

Questa configurazione indirizza il traffico da IA agentica (richieste da bot IA e da agenti utente LLM) al servizio back-end Edge Optimize (`live.edgeoptimize.net`). Le persone e i bot SEO continuano a ricevere come al solito i contenuti trasmessi dalla tua origine. Per testare la configurazione, al termine cerca nella risposta l’intestazione `x-edgeoptimize-request-id`.

**Prerequisiti**

Prima di configurare le regole di Akamai Property Manager, assicurati di:

* aver accesso ad Akamai Property Manager per il tuo dominio;
* aver recuperato una chiave API di ottimizzazione edge dall’interfaccia di LLM Optimizer. Per i passaggi, consulta [Recuperare le chiavi API](/help/dashboards/optimize-at-edge/retrieve-api-keys.md#production-api-key).
* (Facoltativo) Per verificare il routing dell&#39;area di gestione temporanea, vedere [Chiave API di gestione temporanea](/help/dashboards/optimize-at-edge/retrieve-api-keys.md#staging-api-key-optional).

**Configurazione**

La seguente regola di Akamai Property Manager indirizza il traffico di pagina HTML agente ad Edge Optimize. La configurazione include i seguenti passaggi:

**1. Imposta criteri di routing (corrispondenza traffico agente utente e HTML)**

Impostare l&#39;instradamento per i seguenti agenti utente:

```
 *AdobeEdgeOptimize-AI*
 *ChatGPT-User*
 *GPTBot*
 *OAI-SearchBot*
 *PerplexityBot*
 *Perplexity-User*
```

>[!NOTE]
>
>Applica la regola di routing Optimize at Edge solo al traffico di pagina HTML agente. Un&#39;impostazione comune consiste nell&#39;utilizzare i criteri lato richiesta, ad esempio **Estensione file**, per far corrispondere `html` e `EMPTY_STRING` per gli URL di pagina senza estensione. Se il sito utilizza HTML da altri pattern di URL o include route non di pagina senza estensione, come endpoint API, perfeziona la regola con criteri aggiuntivi basati sul percorso.

![Imposta i criteri di indirizzamento](/help/assets/optimize-at-edge/akamai-step1-routing.png)

**2. Imposta il comportamento di origine e SSL**

Imposta l’origine come `live.edgeoptimize.net` e abbina SAN a `*.edgeoptimize.net`

>[!NOTE]
>
>Se l&#39;attivazione della proprietà non riesce dopo aver aggiunto la regola Ottimizza in Edge, verifica se la regola utilizza una modalità di verifica SSL del server di origine diversa da quella predefinita. In caso contrario, aggiorna la regola Ottimizza in Edge in modo che corrisponda alla regola predefinita. Se ad esempio la regola predefinita utilizza **Impostazioni piattaforma**, utilizzare anche **Impostazioni piattaforma**. Se non riesci a utilizzare l’impostazione richiesta, contatta il supporto Akamai.

![Imposta il comportamento di origine e SSL](/help/assets/optimize-at-edge/akamai-step2-origin.png)

**3. Imposta la variabile chiave della cache**

Imposta la variabile della chiave della cache `PMUSER_EDGE_OPTIMIZE_CACHE_KEY` su `LLMCLIENT=TRUE;X_FORWARDED_HOST={{builtin.AK_HOST}}`

![Imposta la variabile chiave della cache](/help/assets/optimize-at-edge/akamai-step3-cachekey.png)

**4. Regole di memorizzazione in cache**

![Regole di memorizzazione in cache](/help/assets/optimize-at-edge/akamai-step4-rules.png)

**5. Modifica le intestazioni delle richieste in ingresso**

Imposta le seguenti intestazioni di richiesta in ingresso:
`x-edgeoptimize-api-key` alla chiave API recuperata da LLMO
Da `x-edgeoptimize-config` a `LLMCLIENT=TRUE;`
Da `x-edgeoptimize-url` a `{{builtin.AK_URL}}`

![Modifica le intestazioni delle richieste in ingresso](/help/assets/optimize-at-edge/akamai-step5-request.png)

**Consenti ottimizzazione in Edge tramite regole firewall (facoltativo)**

{{waf-allowlist-setup}}

![Imposta l&#39;intestazione x-edgeoptimize-fetcher-key in Gestione proprietà](/help/assets/optimize-at-edge/akamai-step10-fetcher-key.png)

>[!NOTE]
>
>È inoltre possibile inserire nell&#39;elenco Consentiti l&#39;agente utente `*AdobeEdgeOptimize/1.0*` e l&#39;intestazione `x-edgeoptimize-fetcher-key` in Akamai Bot Manager.

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
>Il frammento XML in questo passaggio richiede il comportamento **Avanzato**. In alcuni ambienti Akamai, questo comportamento non è disponibile per la modifica self-service. Se non trovi l&#39;opzione **Avanzate**, contatta il team dell&#39;account Akamai o il supporto di Akamai per abilitare la configurazione richiesta.

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
>Inoltre, assicurati che la regola **Ottimizza su routing Edge** non sia sostituita da alcuna regola corrispondente successiva che modifichi l&#39;origine, il comportamento di caching o l&#39;ID cache per le stesse richieste. Se un’altra regola corrispondente ripristina questi comportamenti, il comando Ottimizza in fase di routing o caching di Edge potrebbe non funzionare come previsto.

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
