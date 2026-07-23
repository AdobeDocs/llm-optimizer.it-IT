---
title: Ottimizza in Edge - Server HTTP Apache
description: Scopri come configurare Apache HTTP Server (self-hosted reverse proxy) BYOCDN per l’ottimizzazione in Edge in LLM Optimizer.
feature: Opportunities
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: d1956731-2adb-4bb7-8301-2b239254ac72
subfeature_v2: id: d23587d6-14d6-4e3f-9ee1-cc18623832e1
source-git-commit: d7e723161836027dcdde931378f5d0f776a1ecfc
workflow-type: tm+mt
source-wordcount: 585
ht-degree: 32%

---


# Apache HTTP Server

Questa configurazione si applica quando Apache HTTP Server funge da proxy inverso davanti all&#39;origine (installazione con hosting autonomo, **senza** AEM Dispatcher). Indirizza il traffico agente (richieste da bot di IA e agenti utente LLM) al servizio back-end Edge Optimize (`live.edgeoptimize.net`). Le persone e i bot SEO continuano a ricevere come al solito i contenuti trasmessi dalla tua origine. Per testare la configurazione, al termine cerca nella risposta l’intestazione `x-edgeoptimize-request-id`.

L&#39;integrazione è un set di file Apache `Include` nativi. Nessun codice o processo di lavoro da distribuire. Si scaricano tre file, si imposta la chiave API e si aggiungono due `Include` righe all&#39;host virtuale.

**Prerequisiti**

Prima di impostare le regole di instradamento di Apache, assicurati di disporre di:

* Apache HTTP Server 2.4 o versione successiva con questi moduli abilitati: `proxy`, `proxy_http`, `ssl`, `rewrite`, `headers`, `env` e `setenvif`.
* Accesso alla configurazione di Apache (il `<VirtualHost>` per il sito) e possibilità di ricaricare Apache.
* aver recuperato dall’interfaccia di LLM Optimizer una chiave API del servizio Edge Optimize. Per la procedura, consulta [Recuperare le chiavi API](/help/dashboards/optimize-at-edge/retrieve-api-keys.md#production-api-key).
* (Facoltativo) Per verificare l’indirizzamento in fase di staging, consulta [Chiave API di staging](/help/dashboards/optimize-at-edge/retrieve-api-keys.md#staging-api-key-optional).

## Configurazione

**1. Scarica i file di configurazione**

Scarica i tre file di inclusione di Edge Optimize dall&#39;archivio degli esempi di codice [Optimize at Edge](https://github.com/adobe/llmo-code-samples/tree/main/optimize-at-edge/apache) e inseriscili in una directory sul server Apache (ad esempio, `conf/oae/`):

| File | Scopo |
|------|---------|
| `oae-routing.conf` | Rileva i bot di intelligenza artificiale, inserisce le intestazioni di Edge Optimize, indirizza le richieste di pagine HTML al backend e imposta l’isolamento e il failover della cache. |
| `oae-failover.conf` | Riproduce la richiesta originale rispetto all’origine se Edge Optimize restituisce un errore. |
| `domains.conf` | Abilita l’ottimizzazione in Edge per dominio e contiene la tua chiave API. |

Non è necessario modificare `oae-routing.conf` o `oae-failover.conf`. Utilizzarli così come sono.

**2. Abilitare il dominio e impostare la chiave API (`domains.conf`)**

Modificare `domains.conf` e aggiungere una riga per ogni dominio che si sta abilitando. Sostituisci l&#39;host con il tuo dominio e `YOUR_API_KEY` con la chiave dell&#39;interfaccia utente di LLM Optimizer. I domini non elencati vengono indirizzati all’origine senza modifiche, pertanto puoi abilitare un dominio alla volta.

```
SetEnvIfExpr "%{HTTP_HOST} =~ m#(?i)^(www\.)?example\.com(:\d+)?$#" OAE_DOMAIN_ENABLED=1 OAE_API_KEY=YOUR_API_KEY
```

**3. Includi i file nell&#39;host virtuale**

Aggiungi le due `Include` righe al tuo `<VirtualHost *:443>` esistente. Il file di routing passa **prima** della riscrittura e delle `ProxyPass` regole; il file di failover passa **dopo**. Nell&#39;esempio seguente, le righe contrassegnate con `#NEWLINE` sono le uniche righe aggiunte per l&#39;ottimizzazione in Edge. Tutto il resto (`ServerName`, `ProxyPass` e il resto) è la configurazione esistente non modificata.

```
Define OAE_CONF_DIR conf/oae                       #NEWLINE  directory holding the OAE include files

<VirtualHost *:443>
    ServerName www.example.com

    Include "${OAE_CONF_DIR}/oae-routing.conf"     #NEWLINE  OAE routing — BEFORE your Rewrite & ProxyPass rules

    # --- your existing rewrite rules and ProxyPass to origin ---
    ProxyPass        "/" "https://www.example.com/"
    ProxyPassReverse "/" "https://www.example.com/"

    Include "${OAE_CONF_DIR}/oae-failover.conf"    #NEWLINE  OAE failover — AFTER your ProxyPass rules
</VirtualHost>
```

**4. Ricarica Apache**

Convalida la configurazione e ricarica Apache per applicare le modifiche.

>[!NOTE]
>
>Le risposte umane e ottimizzate per bot vengono mantenute automaticamente in voci di cache separate (set di file di routing `Vary: x-edgeoptimize-config`). Se il tuo Apache utilizza già `mod_cache`, assicurati che sia `CacheQuickHandler Off` in modo che la ricerca nella cache venga eseguita dopo l&#39;impostazione delle intestazioni di Edge Optimize.

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
| `x-edgeoptimize-fo` | Presente solo in caso di failover (valore: `1`) | Assente |

{{verify-routing-status-in-ui}}

{{return-to-overview}}
