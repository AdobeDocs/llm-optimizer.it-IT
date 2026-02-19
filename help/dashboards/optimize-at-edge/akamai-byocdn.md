---
title: Ottimizza in Edge - Akamai (BYOCDN)
description: Scopri come configurare Akamai BYOCDN per ottimizzare in Edge in LLM Optimizer.
feature: Opportunities
source-git-commit: 9230e525340bb951fcd9f2ae1f88bad557d5b7d7
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 14%

---


# Akamai (BYOCDN)

Questa configurazione indirizza il traffico agente (richieste da bot di IA e agenti utente LLM) al servizio back-end Edge Optimize (`live.edgeoptimize.net`). I visitatori umani e i bot SEO continuano a essere serviti dalla tua origine come al solito. Per verificare la configurazione, al termine dell&#39;installazione, cercare l&#39;intestazione `x-edgeoptimize-request-id` nella risposta.

**Prerequisiti**

Prima di impostare le regole di Gestione proprietà Akamai, assicurati di disporre dei seguenti elementi:

* Accesso ad Akamai Property Manager per il dominio.
* Processo di onboarding in LLM Optimizer completato.
* Inoltro del registro CDN a LLM Optimizer completato.
* Chiave API di ottimizzazione Edge recuperata dall’interfaccia utente di LLM Optimizer.

{{retrieve-byocdn-api-key}}

**Configurazione**

La regola di Akamai Property Manager seguente indirizza gli agenti utente LLM ad Edge Optimize. La configurazione include i seguenti passaggi:

**1. Imposta i criteri di indirizzamento (corrispondenza agente utente)**

Imposta routing per i seguenti agenti utente:image.png

```
 *AdobeEdgeOptimize-AI*,
 *ChatGPT-User*,
 *GPTBot*,
 *OAI-SearchBot*,
 *PerplexityBot*,
 *Perplexity-User*
```

![Imposta i criteri di indirizzamento](/help/assets/optimize-at-edge/akamai-step1-routing.png)

**2. Imposta il comportamento di origine e SSL**

Imposta origine come `live.edgeoptimize.net` e abbina SAN a `*.edgeoptimize.net`

![Imposta il comportamento di origine e SSL](/help/assets/optimize-at-edge/akamai-step2-origin.png)

**3. Imposta la variabile chiave della cache**

Imposta la variabile chiave della cache `PMUSER_EDGE_OPTIMIZE_CACHE_KEY` su `LLMCLIENT=TRUE;X_FORWARDED_HOST={{builtin.AK_HOST}}`

![Imposta la variabile chiave della cache](/help/assets/optimize-at-edge/akamai-step3-cachekey.png)

**4. Regole di memorizzazione in cache**

![Regole di memorizzazione in cache](/help/assets/optimize-at-edge/akamai-step4-rules.png)

**5. Modifica le intestazioni delle richieste in ingresso**

Imposta le seguenti intestazioni di richiesta in ingresso:
`x-edgeoptimize-api-key` alla chiave API recuperata da LLMO
Da `x-edgeoptimize-config` a `LLMCLIENT=TRUE;`
Da `x-edgeoptimize-url` a `{{builtin.AK_URL}}`

![Modifica le intestazioni delle richieste in ingresso](/help/assets/optimize-at-edge/akamai-step5-request.png)

**6. Modifica le intestazioni delle risposte in ingresso**

![Modifica le intestazioni delle risposte in ingresso](/help/assets/optimize-at-edge/akamai-step6-response.png)

**7. Modifica l’ID cache**

![Modifica l’ID cache](/help/assets/optimize-at-edge/akamai-step7-cacheid.png)

**8. Modifica intestazioni richieste in uscita**

Imposta intestazione `x-forwarded-host` su `{{builtin.AK_HOST}}`

![Modifica intestazioni richieste in uscita](/help/assets/optimize-at-edge/akamai-step8-outgoing-request.png)

**9. Failover del sito**

La configurazione di failover del sito è composta da due parti: il comportamento di failover (configurato all&#39;interno della regola principale di routing optimize-at-edge) e una regola di intestazione del test di failover separata.

**9 bis. Comportamento failover sito (all&#39;interno della regola principale di routing di ottimizzazione in Edge)**

All&#39;interno della regola di routing principale, configurare il comportamento Failover del sito e lo snippet XML avanzato come indicato di seguito:

![Failover del sito](/help/assets/optimize-at-edge/akamai-step9-failover.png)

Aggiungere l&#39;intestazione della richiesta `x-edgeoptimize-request` con il valore `fo` tramite XML avanzato:

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

**9 ter. Regola intestazione test di failover (regola di pari livello)**

>[!IMPORTANT]
>
>Crea la regola **Failover EdgeOptimize - Testing Header** come **pari livello** (allo stesso livello) delle regole di routing - **non** nidificate al loro interno. Nella struttura ad albero delle regole di Gestione proprietà Akamai, la gerarchia deve essere simile alla seguente:
>
>```
>▼ Parent Rule
>   ▶ Optimize at Edge Routing     ← routing rule
>       EdgeOptimize Failover - Test Header       ← sibling, same level
>```
>
>In questo modo la regola di intestazione del test di failover valuta **tutte** le regole di routing, non solo una.

Se il valore dell&#39;intestazione di richiesta `x-edgeoptimize-request` è `fo`, impostare l&#39;intestazione di risposta in uscita `x-edgeoptimize-fo` su `true`.

![Regole di failover](/help/assets/optimize-at-edge/akamai-step9-failover-rules.png)

Il failover del sito garantisce che se Edge Optimize restituisce un errore `4XX` o `5XX`, la richiesta venga automaticamente indirizzata all&#39;origine predefinita, in modo che l&#39;utente finale riceva comunque una risposta.

| Scenario | Comportamento |
| --- | --- |
| Edge Optimize restituisce `2XX` | Al client viene fornita una risposta ottimizzata. |
| Edge Optimize restituisce `4XX` o `5XX` | La richiesta viene indirizzata all’origine predefinita. |

**Verifica installazione**

Dopo aver completato la configurazione, verifica che il traffico da bot venga indirizzato ad Edge Optimize e che non venga influenzato dal traffico umano.

**1. Verifica traffico da bot (deve essere ottimizzato)**

Simulare una richiesta bot di intelligenza artificiale utilizzando un agente utente:

```
curl -svo /dev/null https://www.example.com/page.html \
  --header "user-agent: chatgpt-user"
```

Una risposta corretta include l&#39;intestazione `x-edgeoptimize-request-id`, a conferma che la richiesta è stata instradata tramite Edge Optimize:

```
< HTTP/2 200
< x-edgeoptimize-request-id: 50fce12d-0519-4fc6-af78-d928785c1b85
```

**2. Test del traffico umano (non dovrebbe essere interessato)**

Simula una richiesta browser umana regolare:

```
curl -svo /dev/null https://www.example.com/page.html \
  --header "user-agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36"
```

La risposta deve **non** contenere l&#39;intestazione `x-edgeoptimize-request-id`. Il contenuto della pagina e il tempo di risposta devono rimanere identici a prima di abilitare l’opzione Ottimizza in Edge.

**3. Come distinguere tra i due scenari**

| Intestazione | Traffico bot (ottimizzato) | Traffico umano (non interessato) |
|---|---|---|
| `x-edgeoptimize-request-id` | Presente — contiene un ID richiesta univoco | Assente |
| `x-edgeoptimize-fo` | Presente solo se si è verificato il failover (valore: `1`) | Assente |

Lo stato del routing del traffico può essere controllato anche nell’interfaccia utente di LLM Optimizer. Passa a **Configurazione cliente** e seleziona la scheda **Configurazione rete CDN**.

![Stato routing traffico IA con routing abilitato](/help/assets/optimize-at-edge/byocdn-CDN-traffic-routed-tick.png)

{{return-to-overview}}
