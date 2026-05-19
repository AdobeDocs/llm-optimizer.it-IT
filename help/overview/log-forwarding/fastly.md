---
title: Inoltro dei registri - Fastly
description: Scopri come inoltrare i registri CDN da Fastly al bucket S3 di Adobe per la raccolta di dati sul traffico da IA agentica in LLM Optimizer.
feature: Agentic Traffic
autotag-review: '2026-05-15T17:51:51.808Z'
TQID: 'https://experienceleague.adobe.com/9SH1I6ajHKLFeEWXy-NpvPm-Ylk2xBKhQro3qobVEX8'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: d1956731-2adb-4bb7-8301-2b239254ac72
subfeature_v2: id: d23587d6-14d6-4e3f-9ee1-cc18623832e1
topic_v2: id: d3cdead0-685a-4489-9250-4bb709942f66id: e1e0219c-f879-479f-8427-888ed2a6e9c2
source-git-commit: 564171851fdccee43afd233da143d66182464889
workflow-type: tm+mt
source-wordcount: 381
ht-degree: 100%

---


# Inoltro dei registri: Fastly {#log-forwarding-fastly}

Questa pagina spiega come inoltrare i registri CDN da Fastly al bucket S3 di Adobe per la raccolta di dati sul traffico da IA agentica. Per effettuare l’onboarding in LLM Optimizer, utilizza la pagina Configurazione CDN di LLM Optimizer. Al termine del processo di onboarding, segui i passaggi descritti in questa pagina per configurare l’inoltro dei registri nella console web di Fastly.

## Passaggio 1: eseguire l’onboarding in LLM Optimizer {#step-1}

Nella pagina LLM Optimizer [https://llmo.now/](https://llmo.now/):

1. Passa a **Configurazione**.

   ![Pulsante Configurazione](/help/overview/assets/log-forwarding/common/config-button.png)

1. Fai clic sulla scheda **Configurazione CDN**.

   ![Scheda Configurazione CDN](/help/overview/assets/log-forwarding/common/cdn-config-tab.png)

1. Fai clic su **Inizia**.
1. Accanto ad **Attiva analisi traffico IA**, fai clic su **Configura**.

   ![Configura](/help/overview/assets/log-forwarding/common/configure.png)
1. Seleziona **Fastly (BYOCDN)**.

   ![Seleziona Fastly](/help/overview/assets/log-forwarding/fastly/fastly-select.png)
1. Fai clic su **Esegui onboarding**.

## Passaggio 2: creare un endpoint S3 in Fastly {#step-2}

Per creare un endpoint S3, nel **Pannello di controllo di Fastly**:

1. Nella dashboard di Fastly, passa a **CDN services** (Servizi CDN), non Servizi di calcolo automatico.
1. Nell’area **Amazon Web Services S3**, fai clic su **Create endpoint** (Crea endpoint).
1. Compila i campi **Create an Amazon S3 endpoint** (Crea un endpoint Amazon S3):

| Campo | Descrizione |
| --- | --- |
| **Nome** | Nome leggibile dell’endpoint. |
| **Posizionamento** | Predefiniti |
| **Formato registro** | Utilizza la stringa del formato del registro mostrata nella sezione **Stringa del formato del registro** di seguito. |
| **Formato marca temporale** | `%Y-%m-%dT%H:%M:%S.000` |
| **Nome bucket** | Copia il **Nome bucket** dalla pagina di configurazione di LLM Optimizer. ![Nome bucket](/help/overview/assets/log-forwarding/fastly/fastly-bucket-name.png) |
| **Dominio** | Copia il **Nome dominio** dalla pagina di configurazione di LLM Optimizer. ![Nome dominio](/help/overview/assets/log-forwarding/fastly/fastly-domain-name.png) |
| **Metodo di accesso** | **Credenziali utente** |
| **Credenziali utente** | Copia la **Chiave di accesso** e la **Chiave segreta** dalla pagina di configurazione di LLM Optimizer. ![Chiavi di accesso](/help/overview/assets/log-forwarding/common/access-keys.png) |
| **Periodo** | `300` |

**Stringa del formato del registro:**

```json
{ "timestamp": "%{strftime(\{"%Y-%m-%dT%H:%M:%S%z"\}, time.start)}V", "host": "%{if(req.http.Fastly-Orig-Host, req.http.Fastly-Orig-Host, req.http.Host)}V", "url": "%{json.escape(req.url)}V", "request_method": "%{json.escape(req.method)}V", "request_referer": "%{json.escape(req.http.referer)}V", "request_user_agent": "%{json.escape(req.http.User-Agent)}V", "response_status": %{resp.status}V, "response_content_type": "%{json.escape(resp.http.Content-Type)}V", "client_country_code": "%{client.geo.country_name}V", "time_to_first_byte": "%{time.to_first_byte}V" }
```

>[!WARNING]
>
>I gestori di password possono compilare automaticamente il campo **Chiave segreta** con la password di Fastly. Se l’integrazione di AWS non riesce, immetti manualmente la chiave segreta.

Dopo aver completato i passaggi precedenti, fai clic su **Opzioni avanzate** e imposta:

| Campo | Descrizione |
| --- | --- |
| **Percorso** | Copia **Percorso** dalla pagina di configurazione di LLM Optimizer. ![Percorso](/help/overview/assets/log-forwarding/fastly/fastly-path.png) |
| **Seleziona un formato per la riga di registro** | Vuoto |
| **Compressione** | Gzip |
| **Livello di ridondanza** | Standard |
| **ACL** | Nessuno |
| **Crittografia lato server** | Nessuno |
| **Numero massimo di byte** | 0 |

Dopo aver impostato le opzioni avanzate:

1. Fai clic su **Crea** per creare l’endpoint.
1. Dal menu **Attiva**, seleziona **Attiva in produzione** per effettuare l’implementazione.

>[!NOTE]
>
>Fastly trasmette i registri in modo continuo a S3, ma il sito Web e l’API di S3 rendono i file disponibili solo dopo il completamento del caricamento.

### Esempio di voce di registro {#example}

Di seguito è riportata una stringa di formato di esempio per l’invio di dati ad Amazon S3:

```json
{
  "timestamp": "2026-02-10T05:05:36+0000",
  "host": "example.com",
  "url": "/my/path",
  "request_method": "GET",
  "request_referer": "https://example.com/my/other/path",
  "request_user_agent": "Mozilla/5.0 (iPhone; CPU iPhone OS 13_2_3 like Mac OS X) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/13.0.3 Mobile/15E148 Safari/604.1",
  "response_status": 200,
  "response_content_type": "text/css; charset=utf-8",
  "client_country_code": "argentina",
  "time_to_first_byte": "0.138"
}
```
