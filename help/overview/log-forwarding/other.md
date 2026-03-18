---
title: Inoltro log - Altro (caricamento manuale)
description: Scopri come caricare manualmente i registri CDN nel bucket S3 di Adobe per la raccolta di dati sul traffico agente in LLM Optimizer quando si utilizza un provider CDN non supportato.
feature: Agentic Traffic
source-git-commit: b590cd14ba7d64e56a6c972fd6090e2df9de58f6
workflow-type: tm+mt
source-wordcount: '670'
ht-degree: 2%

---


# Inoltro log: altro (caricamento manuale) {#log-forwarding-other}

Il metodo di provisioning **Altro BYOCDN** è un&#39;opzione onnicomprensiva per i clienti che desiderano fornire i registri CDN a LLM Optimizer quando:

- **I caricamenti manuali** sono preferiti. Ad esempio, i team operativi esportano i registri e li caricano periodicamente.
- **Sono utilizzati processi automatizzati ad hoc**: script una tantum, esportazioni pianificate, processi senza server.
- Il cliente utilizza una **rete CDN non supportata in modo nativo** dalle integrazioni di inoltro del registro incorporate.

Questo metodo imita il modello di &quot;inoltro continuo&quot;: i registri vengono prodotti e caricati nella posizione S3 prevista e infine elaborati automaticamente dalle pipeline di acquisizione.

## Passaggio 1: onboarding in LLM Optimizer {#step-1}

In [LLM Optimizer](https://llmo.now/):

1. Vai a **Configurazione**.

   ![Pulsante Configurazione](/help/overview/assets/log-forwarding/common/config-button.png)

1. Fare clic sulla scheda **Configurazione CDN**.

   ![Scheda Configurazione CDN](/help/overview/assets/log-forwarding/common/cdn-config-tab.png)

1. Fai clic su **Inizia**.

   <!-- ![Onboard CDN button](/help/overview/assets/log-forwarding/common/onboard-cdn-button.png)-->

1. Accanto a **Attiva analisi traffico IA**, fai clic su **Configura**.

   ![Configura](/help/overview/assets/log-forwarding/common/configure.png)

1. Seleziona **Altro**.

   ![Seleziona altro](/help/overview/assets/log-forwarding/other/other-select.png)

1. Fare clic su **Onboard**.

<!--   ![Onboard button](/help/overview/assets/log-forwarding/common/onboard-button.png)-->

## Passaggio 2: preparare e caricare i registri {#step-2}

### Formato registro richiesto (righe JSON) {#log-format}

I registri devono essere caricati come JSON delimitato da nuova riga (**un oggetto JSON per riga**). Ogni riga di registro deve includere i campi seguenti **esattamente come sono stati scritti di seguito**.

#### Schema campo per campo {#schema}

| Campo | Tipo | Descrizione | Esempio |
|---|---|---|---|
| **marca temporale** | Stringa | Il timestamp della richiesta che segue il formato **ISO 8601**. | `"2025-02-01T23:00:05Z"` |
| **host** | Stringa | Il dominio web richiesto dal client. | `"www.example.com"` |
| **url** | Stringa | **path** e **query parameters** sono obbligatori, mentre il dominio deve **not** essere incluso. | `"/home?utm_source=google"` |
| **metodo_richiesta** | Stringa | Il metodo di richiesta HTTP, a volte indicato come verbi HTTP. | `"GET"` |
| **request_user_agent** | Stringa | Intestazione della richiesta HTTP dell’agente utente. | `"Mozilla/5.0 (compatible; GPTBot/1.0"` |
| **referer_richiesta** | Stringa | L’intestazione della richiesta HTTP Referer (può essere vuota). | `"https://chatgpt.com"` |
| **stato_risposta** | Numero intero | Il codice di stato della risposta HTTP. | `200` |
| **tipo_contenuto_risposta** | Stringa | L’intestazione di risposta HTTP Content-Type. | `"text/html; charset=utf-8"` |
| **time_to_first_byte** | Numero intero | Tempo tra la creazione di una connessione al server e il download del contenuto di una pagina Web in **millisecondi**. Imposta su zero se sconosciuto o non disponibile. | `42` |

#### Esempio di righe di registro {#example}

L&#39;esempio seguente mostra tre righe di registro:

```json
{"timestamp":"2025-02-01T23:06:14Z","host":"www.example.com","url":"/products/llm-optimizer?utm_source=google","request_method":"GET","request_user_agent":"Mozilla/5.0 (compatible; GPTBot/1.0; +https://openai.com/gptbot)","response_status":200,"request_referer":"","response_content_type":"text/html; charset=utf-8","time_to_first_byte":198}
{"timestamp":"2025-02-01T23:19:32Z","host":"www.example.com","url":"/services/ai-consulting/overview","request_method":"GET","request_user_agent":"PerplexityBot/1.0 (+https://www.perplexity.ai/perplexitybot)","response_status":200,"request_referer":"","response_content_type":"text/html; charset=utf-8","time_to_first_byte":255}
{"timestamp":"2025-02-01T23:44:05Z","host":"www.example.com","url":"/products/pricing/enterprise?utm_medium=social","request_method":"GET","request_user_agent":"ClaudeBot/1.0 (+https://www.anthropic.com)","response_status":200,"request_referer":"","response_content_type":"application/pdf","time_to_first_byte":312}
```

### Dichiarazione di non responsabilità critica (ortografia e tipi) {#disclaimer}

Le pipeline di acquisizione e aggregazione sono rigorose per **nomi di campi e tipi di dati**.

- I nomi dei campi devono corrispondere **esattamente** (maiuscole/minuscole e ortografia).
- I tipi di dati devono essere corretti, come segue:
   - **timestamp** deve essere una stringa in formato **ISO 8601**. I timestamp UNIX-like potrebbero non funzionare.
   - **response_status** deve essere un numero intero.
   - Il valore di **time_to_first_byte** deve essere un numero intero e utilizzare millisecondi.
   - Le stringhe devono essere stringhe JSON valide.
- Il formato JSON non valido o i campi mancanti/errati possono causare l’omissione o l’impossibilità di analizzare i registri, con conseguente perdita di dati nei rapporti.

### Percorso di caricamento e frequenza di elaborazione {#upload-location}

#### Regola del percorso {#path-rule}

Caricare i registri nel percorso appropriato della cartella utilizzando il formato: **`yyyy/mm/dd/`** (con barre).

Un esempio di registro dal 1° febbraio 2025 UTC: `ABC123AdobeOrg/raw/byocdn-other/2025/02/01/`

#### Regola di elaborazione {#processing-rule}

- I registri caricati durante un dato **giorno UTC** vengono elaborati dalle pipeline **verso la fine di quel giorno UTC** (esecuzione giornaliera).
- I registri caricati nelle **cartelle dei giorni precedenti** (backfill) sono **rilevati ed elaborati** entro 24 ore.

## Scenari {#scenarios}

### Scenario 1: registri in Splunk / Elasticsearch — esportare e caricare in S3 {#scenario-splunk}

**Obiettivo**: recupera i registri dalle piattaforme di osservabilità esistenti e distribuiscili alla posizione S3.

- Estrai i campi richiesti dagli eventi di ricerca Splunk/Elastic.
- Trasforma ogni evento in un oggetto JSON seguendo lo schema precedente (Righe JSON).
- Carica i file risultanti nel bucket S3 designato e nel percorso **del giorno UTC corrente**: `…/byocdn-other/yyyy/mm/dd/`
- I registri verranno elaborati automaticamente entro la fine del giorno UTC.

### Scenario 2: funzione Lambda/Azure — formattazione e caricamento su S3 {#scenario-serverless}

**Obiettivo**: utilizza il calcolo senza server per recuperare/ricevere i registri CDN, normalizzarli e consegnarli alla posizione S3.

- La funzione recupera i registri dall’origine del cliente (archivio registri, coda, archiviazione BLOB, ecc.).
- La funzione mappa i campi nello schema previsto ed emette **righe JSON**.
- La funzione carica l&#39;output in: `…/byocdn-other/yyyy/mm/dd/`
- I registri verranno elaborati automaticamente entro la fine del giorno UTC.

## Elenco di controllo rapido {#checklist}

- **Un oggetto JSON per riga** (righe JSON)
- **Correzione esatta del campo** come specificato
- Correggere i tipi di dati
- **time_to_first_byte** in millisecondi (numero intero)
- Carica nella cartella UTC appropriata: **aaaa/mm/gg/** in **byocdn-other**
