---
title: Inoltro dei registri - Altro (caricamento manuale)
description: Scopri come caricare manualmente i registri CDN nel bucket S3 di Adobe per la raccolta dati relativa al traffico da IA agentica in LLM Optimizer quando si utilizza un provider CDN non supportato.
feature: Agentic Traffic
autotag-review: '2026-05-15T17:54:15.685Z'
TQID: 'https://experienceleague.adobe.com/YBfhS4oM0qYRkFvS3zPzzcFAeLNBucRH5QmMBUH8h4E'
product_v2:
  - id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2:
  - id: d1956731-2adb-4bb7-8301-2b239254ac72
subfeature_v2:
  - id: d23587d6-14d6-4e3f-9ee1-cc18623832e1
topic_v2:
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: 564171851fdccee43afd233da143d66182464889
workflow-type: tm+mt
source-wordcount: 670
ht-degree: 100%

---


# Inoltro dei registri: altro (caricamento manuale) {#log-forwarding-other}

Il metodo di provisioning **Altro BYOCDN** è un’opzione onnicomprensiva per chi desidera fornire i registri CDN a LLM Optimizer nei seguenti casi:

- Si preferiscono i **caricamenti manuali**: ad esempio, i team operativi esportano i registri e li caricano periodicamente.
- Si utilizzano **processi automatizzati ad hoc**: script una tantum, esportazioni pianificate, processi senza server.
- Il cliente utilizza una **CDN non supportata in modo nativo** dalle integrazioni di inoltro dei registri incorporate.

Questo metodo imita il modello di “inoltro continuo”: i registri vengono prodotti e caricati nella posizione S3 prevista e infine elaborati in automatico dalle pipeline di acquisizione.

## Passaggio 1: eseguire l’onboarding in LLM Optimizer {#step-1}

In [LLM Optimizer](https://llmo.now/):

1. Passa a **Configurazione**.

   ![Pulsante Configurazione](/help/overview/assets/log-forwarding/common/config-button.png)

1. Fai clic sulla scheda **Configurazione CDN**.

   ![Scheda Configurazione CDN](/help/overview/assets/log-forwarding/common/cdn-config-tab.png)

1. Fai clic su **Inizia**.

   <!-- ![Onboard CDN button](/help/overview/assets/log-forwarding/common/onboard-cdn-button.png)-->

1. Accanto ad **Attiva analisi traffico IA**, fai clic su **Configura**.

   ![Configura](/help/overview/assets/log-forwarding/common/configure.png)

1. Seleziona **Altro**.

   ![Seleziona Altro](/help/overview/assets/log-forwarding/other/other-select.png)

1. Fai clic su **Esegui onboarding**.

<!--   ![Onboard button](/help/overview/assets/log-forwarding/common/onboard-button.png)-->

## Passaggio 2: preparare e caricare i registri {#step-2}

### Formato registro obbligatorio (righe JSON) {#log-format}

I registri devono essere caricati come JSON delimitato da nuova riga (**un oggetto JSON per riga**). Ogni riga di registro deve includere i seguenti campi **esattamente come sono stati scritti di seguito**.

#### Schema campo per campo {#schema}

| Campo | Tipo | Descrizione | Esempio |
|---|---|---|---|
| **marca temporale** | Stringa | La marca temporale della richiesta che segue il formato **ISO 8601**. | `"2025-02-01T23:00:05Z"` |
| **host** | Stringa | Il dominio web richiesto dal client. | `"www.example.com"` |
| **url** | Stringa | Il **percorso** e i **parametri delle query** sono obbligatori, mentre il dominio **non** deve essere incluso. | `"/home?utm_source=google"` |
| **request_method** | Stringa | Il metodo di richiesta HTTP, a volte indicato come verbi HTTP. | `"GET"` |
| **request_user_agent** | Stringa | L’intestazione della richiesta intestazione HTTP User-Agent. | `"Mozilla/5.0 (compatible; GPTBot/1.0"` |
| **request_referer** | Stringa | L’intestazione della richiesta HTTP Referer (può essere vuota). | `"https://chatgpt.com"` |
| **response_status** | Numero intero | Il codice di stato della risposta HTTP. | `200` |
| **response_content_type** | Stringa | L’intestazione della risposta HTTP Content-Type. | `"text/html; charset=utf-8"` |
| **time_to_first_byte** | Numero intero | Il periodo di tempo compreso tra la creazione di una connessione al server e il download del contenuto di una pagina web, espresso in **millisecondi**. Impostare su zero se sconosciuto o non disponibile. | `42` |

#### Esempio di righe di registro {#example}

L’esempio che segue mostra tre righe di registro:

```json
{"timestamp":"2025-02-01T23:06:14Z","host":"www.example.com","url":"/products/llm-optimizer?utm_source=google","request_method":"GET","request_user_agent":"Mozilla/5.0 (compatible; GPTBot/1.0; +https://openai.com/gptbot)","response_status":200,"request_referer":"","response_content_type":"text/html; charset=utf-8","time_to_first_byte":198}
{"timestamp":"2025-02-01T23:19:32Z","host":"www.example.com","url":"/services/ai-consulting/overview","request_method":"GET","request_user_agent":"PerplexityBot/1.0 (+https://www.perplexity.ai/perplexitybot)","response_status":200,"request_referer":"","response_content_type":"text/html; charset=utf-8","time_to_first_byte":255}
{"timestamp":"2025-02-01T23:44:05Z","host":"www.example.com","url":"/products/pricing/enterprise?utm_medium=social","request_method":"GET","request_user_agent":"ClaudeBot/1.0 (+https://www.anthropic.com)","response_status":200,"request_referer":"","response_content_type":"application/pdf","time_to_first_byte":312}
```

### Dichiarazione di non responsabilità critica (ortografia e tipi) {#disclaimer}

Le pipeline di acquisizione e aggregazione sono rigorose per **i nomi dei campi e i tipi di dati**.

- I nomi dei campi devono corrispondere **esattamente** (maiuscole/minuscole e ortografia).
- I tipi di dati devono essere corretti, come segue:
   - **timestamp** deve essere una stringa in formato **ISO 8601**. Le marche temporali basate su UNIX potrebbero non funzionare.
   - **response_status** deve essere un numero intero.
   - **time_to_first_byte** deve essere un numero intero e utilizzare i millisecondi.
   - Le stringhe devono essere stringhe JSON valide.
- Il formato JSON non valido o i campi mancanti/errati possono causare l’omissione o l’impossibilità di analizzare i registri, con conseguente mancanza di dati nei rapporti.

### Percorso di caricamento e frequenza di elaborazione {#upload-location}

#### Regola del percorso {#path-rule}

Carica i registri nel percorso della cartella appropriato utilizzando il formato: **`yyyy/mm/dd/`** (con barre).

Un esempio di registro dal 1° febbraio 2025 UTC: `ABC123AdobeOrg/raw/byocdn-other/2025/02/01/`

#### Regola di elaborazione {#processing-rule}

- I registri caricati durante un determinato **giorno UTC** vengono elaborati dalle pipeline **verso la fine di quel giorno UTC** (esecuzione giornaliera).
- I registri caricati nelle **cartelle dei giorni precedenti** (retrocompilazione) sono **rilevati ed elaborati** entro 24 ore.

## Scenari {#scenarios}

### Scenario 1: registri di Splunk/Elasticsearch - Esportazione e caricamento in S3 {#scenario-splunk}

**Obiettivo**: recuperare i registri dalle piattaforme di osservabilità esistenti e distribuirli alla posizione S3.

- Estrai i campi richiesti dagli eventi di ricerca Splunk/Elastic.
- Trasforma ogni evento in un oggetto JSON seguendo lo schema precedente (righe JSON).
- Carica i file risultanti nel bucket S3 designato e nel percorso **del giorno UTC corrente**: `…/byocdn-other/yyyy/mm/dd/`
- I registri saranno elaborati automaticamente entro la fine del giorno UTC.

### Scenario 2: funzione Lambda/Azure - Formattazione e caricamento su S3 {#scenario-serverless}

**Obiettivo**: utilizzare il calcolo senza server per recuperare/ricevere i registri CDN, normalizzarli e consegnarli alla posizione S3.

- La funzione recupera i registri dall’origine del cliente (archivio registri, coda, archiviazione BLOB, ecc.).
- La funzione mappa i campi nello schema previsto ed emette **righe JSON**.
- La funzione carica l’output in: `…/byocdn-other/yyyy/mm/dd/`
- I registri saranno elaborati automaticamente entro la fine del giorno UTC.

## Elenco di controllo rapido {#checklist}

- **Un oggetto JSON per riga** (righe JSON)
- **Ortografia precisa del campo** come specificato
- Correzione tipi di dati
- **time_to_first_byte** in millisecondi (numero intero)
- Caricamento nella cartella UTC appropriata: **aaaa/mm/gg/** in **byocdn-other**
