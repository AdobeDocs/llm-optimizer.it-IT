---
source-git-commit: beae935e7a34f5bccbe21578fa9a928912958710
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 2%

---
# Snippet

## Verificare la configurazione - Adobe Managed CDN {#verify-setup-adobe-aem-cs-cdn}

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

![Stato routing traffico IA con routing abilitato](/help/assets/optimize-at-edge/adobe-CDN-traffic-routed-tick.png)

## Verificare la configurazione - BYOCDN {#verify-setup-byocdn}

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

## Passaggi per il recupero della chiave API {#retrieve-byocdn-api-key}

**Passaggi per recuperare la chiave API:**

1. Passa a **Configurazione cliente** e seleziona la scheda **Configurazione rete CDN**.

   ![Passa a Configurazione cliente](/help/assets/optimize-at-edge/prereq-customer-config-nav.png)

2. In **Routing traffico IA per distribuire ottimizzazioni**, selezionare la casella di controllo **Distribuisci ottimizzazioni agli agenti IA**.

   ![Distribuisci ottimizzazioni agli agenti di intelligenza artificiale](/help/assets/optimize-at-edge/prereq-deploy-checkbox.png)

3. Copia la chiave API e procedi con i passaggi di configurazione dell’indirizzamento riportati di seguito.

   ![Copia la chiave API](/help/assets/optimize-at-edge/prereq-copy-api-key.png)

   >[!NOTE]
   >A questo punto, lo stato potrebbe mostrare una croce rossa che indica che la configurazione non è ancora stata completata. Questo è previsto: una volta completata la configurazione di indirizzamento seguente e il traffico da bot AI inizia a fluire, lo stato si aggiorna a un segno di spunta verde che conferma che il routing è stato abilitato correttamente.

Inoltre, se hai bisogno di assistenza per i passaggi precedenti, contatta il team del tuo account Adobe o `llmo-at-edge@adobe.com`.

## Torna alla panoramica {#return-to-overview}

Per ulteriori informazioni su Ottimizza in Edge, tra cui le opportunità disponibili, i flussi di lavoro di ottimizzazione automatica e le domande frequenti, torna alla [Panoramica sull&#39;ottimizzazione in Edge](/help/dashboards/optimize-at-edge.md).
