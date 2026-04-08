---
title: Ottimizza in Edge - Akamai (BYOCDN)
description: Scopri come configurare Akamai BYOCDN per ottimizzare in Edge in LLM Optimizer.
feature: Opportunities
source-git-commit: f2a652761acbea7ca5b8e8740c1dbd0132e42f7f
workflow-type: tm+mt
source-wordcount: '849'
ht-degree: 9%

---


# Akamai (BYOCDN)

Questa configurazione indirizza il traffico agente (richieste da bot di IA e agenti utente LLM) al servizio back-end Edge Optimize (`live.edgeoptimize.net`). I visitatori umani e i bot SEO continuano a essere serviti dalla tua origine come al solito. Per verificare la configurazione, al termine dell&#39;installazione, cercare l&#39;intestazione `x-edgeoptimize-request-id` nella risposta.

**Prerequisiti**

Prima di impostare le regole di Gestione proprietà Akamai, assicurati di disporre dei seguenti elementi:

* Accesso ad Akamai Property Manager per il dominio.
* Processo di onboarding in LLM Optimizer completato.
* Inoltro del registro CDN a LLM Optimizer completato.
* Chiave API di ottimizzazione Edge recuperata dall’interfaccia utente di LLM Optimizer.
* (Facoltativo) Una chiave API di ottimizzazione di Edge per la gestione temporanea se esegui prima il test del routing su un nome host per la gestione temporanea.

{{retrieve-byocdn-api-key}}

{{retrieve-staging-edge-optimize-api-key}}

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

Imposta origine come `live.edgeoptimize.net` e abbina SAN a `*.edgeoptimize.net`

>[!NOTE]
>
>Se l&#39;attivazione della proprietà non riesce dopo aver aggiunto la regola Ottimizza in Edge, verifica se la regola utilizza una modalità di verifica SSL del server di origine diversa da quella predefinita. In caso contrario, aggiorna la regola Ottimizza in Edge in modo che corrisponda alla regola predefinita. Se ad esempio la regola predefinita utilizza **Impostazioni piattaforma**, utilizzare anche **Impostazioni piattaforma**. Se non riesci a utilizzare l’impostazione richiesta, contatta il supporto Akamai.

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

>[!IMPORTANT]
>
>Il frammento XML in questo passaggio richiede il comportamento **Avanzato**. In alcuni ambienti Akamai, questo comportamento non è disponibile per la modifica self-service. Se non trovi l&#39;opzione **Avanzate**, contatta il team dell&#39;account Akamai o il supporto di Akamai per abilitare la configurazione richiesta.

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
>
>Inoltre, assicurati che la regola **Ottimizza su routing Edge** non sia sostituita da alcuna regola corrispondente successiva che modifichi l&#39;origine, il comportamento di caching o l&#39;ID cache per le stesse richieste. Se un’altra regola corrispondente ripristina questi comportamenti, il comando Ottimizza in fase di routing o caching di Edge potrebbe non funzionare come previsto.

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

**4. Dominio di gestione temporanea (facoltativo)**

Se utilizzi un nome host di staging e una chiave API di staging di LLM Optimizer, distribuisci lo stesso pattern di routing nella proprietà **staging** Akamai utilizzando la chiave **staging** nelle regole. Quindi verifica il traffico da bot sull’host di staging:

```
curl -svo /dev/null https://staging.example.com/page.html \
  --header "user-agent: chatgpt-user"
```

Sostituisci `https://staging.example.com/page.html` con il tuo URL e percorso di staging effettivo. Una risposta corretta include l&#39;intestazione `x-edgeoptimize-request-id`.

{{verify-routing-status-in-ui}}

{{return-to-overview}}
