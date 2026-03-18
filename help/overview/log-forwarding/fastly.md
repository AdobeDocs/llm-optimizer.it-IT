---
title: Inoltro registro - Fastly
description: Scopri come inoltrare i registri CDN da Fastly al bucket S3 di Adobe per la raccolta di dati sul traffico agente in LLM Optimizer.
feature: Agentic Traffic
source-git-commit: d1f98770b39f550c36d93ece9b89933c0e90f189
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 4%

---


# Inoltro log: Fastly {#log-forwarding-fastly}

Questa pagina spiega come inoltrare i registri CDN da Fastly al bucket S3 di Adobe per la raccolta di dati sul traffico agente. Per effettuare l’onboarding in LLM Optimizer, utilizza la pagina Configurazione CDN di LLM Optimizer. Al termine del processo di onboarding, segui i passaggi descritti in questa pagina per configurare l’inoltro dei registri nella console web Fastly.

## Passaggio 1: onboarding in LLM Optimizer {#step-1}

Nella pagina LLM Optimizer [https://llmo.now/](https://llmo.now/):

1. Vai a **Configurazione**.

   ![Pulsante Configurazione](/help/overview/assets/log-forwarding/common/config-button.png)

1. Fare clic sulla scheda **Configurazione CDN**.

   ![Scheda Configurazione CDN](/help/overview/assets/log-forwarding/common/cdn-config-tab.png)

1. Fai clic su **Inizia**.
1. Accanto a **Attiva analisi traffico IA**, fai clic su **Configura**.

   ![Configura](/help/overview/assets/log-forwarding/common/configure.png)
1. Selezionare **Fastly (BYOCDN)**.

   ![Seleziona in modo rapido](/help/overview/assets/log-forwarding/fastly/fastly-select.png)
1. Fare clic su **Onboard**.

## Passaggio 2: creare un endpoint S3 in Fastly {#step-2}

Per creare un endpoint S3, nel **Pannello di controllo Campaign Fastly**:

1. Nel dashboard Fastly, vai a **Servizi CDN** (non a Servizi di calcolo).
1. Nell&#39;area **Amazon Web Services S3**, fare clic su **Crea endpoint**.
1. Compila i campi **Crea un endpoint Amazon S3**:

| Campo | Descrizione |
| --- | --- |
| **Nome** | Nome leggibile dell’endpoint. |
| **Posizionamento** | Predefiniti |
| **Formato registro** | Utilizza la stringa del formato del registro mostrata nella sezione **Stringa del formato del registro** seguente. |
| **Formato timestamp** | `%Y-%m-%dT%H:%M:%S.000` |
| **Nome bucket** | Copia il **nome bucket** dalla pagina di configurazione di LLM Optimizer. ![Nome bucket](/help/overview/assets/log-forwarding/fastly/fastly-bucket-name.png) |
| **Dominio** | Copia il **Nome dominio** dalla pagina di configurazione di LLM Optimizer. ![Nome dominio](/help/overview/assets/log-forwarding/fastly/fastly-domain-name.png) |
| **Metodo di accesso** | **Credenziali utente** |
| **Credenziali utente** | Copia la **chiave di accesso** e la **chiave segreta** dalla pagina di configurazione di LLM Optimizer. ![Chiavi di accesso](/help/overview/assets/log-forwarding/common/access-keys.png) |
| **Periodo** | `300` |

**Stringa formato registro:**

```json
{ "timestamp": "%{strftime(\{"%Y-%m-%dT%H:%M:%S%z"\}, time.start)}V", "host": "%{if(req.http.Fastly-Orig-Host, req.http.Fastly-Orig-Host, req.http.Host)}V", "url": "%{json.escape(req.url)}V", "request_method": "%{json.escape(req.method)}V", "request_referer": "%{json.escape(req.http.referer)}V", "request_user_agent": "%{json.escape(req.http.User-Agent)}V", "response_status": %{resp.status}V, "response_content_type": "%{json.escape(resp.http.Content-Type)}V", "client_country_code": "%{client.geo.country_name}V", "time_to_first_byte": "%{time.to_first_byte}V" }
```

>[!WARNING]
>
>I gestori delle password possono compilare automaticamente il campo **Chiave segreta** con la password rapida. Se l’integrazione di AWS non riesce, immetti manualmente la chiave segreta.

Dopo aver completato i passaggi precedenti, fai clic su **Opzioni avanzate** e imposta:

| Campo | Descrizione |
| --- | --- |
| **Percorso** | Copia **Percorso** dalla pagina di configurazione di LLM Optimizer. ![Percorso](/help/overview/assets/log-forwarding/fastly/fastly-path.png) |
| **Selezionare un formato per la riga di registro** | Vuoto |
| **Compressione** | Gzip |
| **Livello di ridondanza** | Standard |
| **ACL** | Nessuno |
| **Crittografia lato server** | Nessuno |
| **Numero massimo di byte** | 0 |

Dopo aver impostato le opzioni avanzate:

1. Fai clic su **Crea** per creare l&#39;endpoint.
1. Dal menu **Attiva**, seleziona **Attiva in produzione** da distribuire.

>[!NOTE]
>
>Fastly Streams registra in modo continuo in S3, il sito web S3 e l’API rendono i file disponibili solo dopo il completamento del caricamento.

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
