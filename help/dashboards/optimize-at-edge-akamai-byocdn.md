---
title: Ottimizza in Edge - Akamai (BYOCDN)
description: Scopri come configurare Akamai BYOCDN per ottimizzare in Edge in LLM Optimizer.
feature: Opportunities
source-git-commit: 23752b30294c3d467ca477b085aa521cad0f72ca
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 26%

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

![Failover del sito](/help/assets/optimize-at-edge/akamai-step9-failover.png)

![Comportamenti di failover](/help/assets/optimize-at-edge/akamai-step9-failover-behaviors.png)

![Regole di failover](/help/assets/optimize-at-edge/akamai-step9-failover-rules.png)

Il failover del sito garantisce che se Edge Optimize restituisce un errore `4XX` o `5XX`, la richiesta venga automaticamente indirizzata all&#39;origine predefinita, in modo che l&#39;utente finale riceva comunque una risposta.

| Scenario | Comportamento |
| --- | --- |
| Edge Optimize restituisce `2XX` | Al client viene fornita una risposta ottimizzata. |
| Edge Optimize restituisce `4XX` o `5XX` | La richiesta viene indirizzata all’origine predefinita. |

{{verify-setup-byocdn}}

{{return-to-overview}}
