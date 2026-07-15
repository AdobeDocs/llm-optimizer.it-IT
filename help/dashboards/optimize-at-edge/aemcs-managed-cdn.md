---
title: Ottimizzazione sulla rete edge - CDN gestita da AEM Cloud Service (Fastly)
description: Scopri come configurare la rete CDN gestita da AEM Cloud Service (Fastly) per l’ottimizzazione su rete edge in LLM Optimizer.
feature: Opportunities
autotag-review: '2026-07-15T16:49:32.275Z'
TQID: 'https://experienceleague.adobe.com/2-IzfF1iTEzW-gpqPA-t3mffRuhMxaKi1Dp0A62IZ9U'
product_v2:
  - id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2:
  - id: d1956731-2adb-4bb7-8301-2b239254ac72
  - id: e0828736-236a-487b-a478-5a635455eadc
  - id: e1b649f0-0a61-46e4-9082-64d5cb2576c6
  - id: ef4e63f5-cb4d-462d-bf9a-1f617edf2a3a
subfeature_v2:
  - id: d23587d6-14d6-4e3f-9ee1-cc18623832e1
  - id: e06fae5f-830b-4222-a469-b5e148d36465
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 2705cf26faea9c09817bbdcec4b4c531552df7ba
workflow-type: tm+mt
source-wordcount: 836
ht-degree: 100%

---


# CDN gestita da AEM Cloud Service (Fastly)

Questa configurazione indirizza il traffico da IA agentica (richieste da bot IA e da agenti utente LLM) al servizio back-end Edge Optimize (`live.edgeoptimize.net`). Le persone e i bot SEO continuano a ricevere come al solito i contenuti trasmessi dalla tua origine. Per testare la configurazione, al termine cerca nella risposta l’intestazione `x-edgeoptimize-request-id`.

## Prerequisiti

Per accedere a questa funzione:

- I clienti a pagamento devono disporre dell’accesso al profilo di prodotto IMS **Utenti Adobe LLM Optimizer**. Contatta l’amministratore della tua organizzazione per richiedere l’accesso.
  ![Aggiungere utenti a un profilo di prodotto](/help/assets/optimize-at-edge/cs-fastly-user-product-profiles.png)
- I clienti di prova devono far parte del gruppo IMS **LLMO Admin**. Se il gruppo non esiste, l’amministratore della tua organizzazione può crearlo e aggiungerti.
  ![Creare un gruppo IMS LLMO Admin](/help/assets/optimize-at-edge/cs-fastly-create-ims-group.png)

>[!NOTE]
> Questa funzione non è supportata in Safari o nelle modalità di navigazione in incognito/privata.

## Passaggi per abilitare l’indirizzamento

Per iniziare a indirizzare il traffico da IA agentica al servizio Edge Optimize:

1. In LLM Optimizer, apri **Configurazione cliente** e seleziona la scheda **Configurazione CDN**.

   ![Passa a Configurazione cliente](/help/assets/optimize-at-edge/cs-fastly-prereq-customer-config-nav.png)

2. Individua la sezione **Implementare le ottimizzazioni negli agenti IA**. Fai clic sul pulsante **Abilita**.

   ![Implementare le ottimizzazioni negli agenti IA - In sospeso](/help/assets/optimize-at-edge/cs-fastly-enable-button.png)

3. Nella finestra di dialogo di conferma, seleziona **Abilita** per confermare che desideri abilitare l’indirizzamento. Se viene visualizzato un errore, fai riferimento alla sezione [Risoluzione dei problemi](#troubleshooting) per risolverlo.

   ![Abilitare la finestra di dialogo di conferma del motore di ottimizzazione](/help/assets/optimize-at-edge/cs-fastly-enable-dialog.png)

4. Una volta confermato, il completamento dell’indirizzamento richiede alcuni minuti.

   ![Indirizzamento in corso](/help/assets/optimize-at-edge/cs-fastly-enable-button-clicked-routing-in-progress.png)

   Ricarica la pagina dopo 5 minuti per verificare che l’indirizzamento sia stato completato. Una volta configurato e attivato l’indirizzamento, lo stato viene aggiornato a **Completato** e presenta un segno di spunta verde per indicare che l’indirizzamento è stato abilitato. Non sono richiesti ulteriori interventi da parte tua.

   ![Implementare le ottimizzazioni negli agenti IA - Completate](/help/assets/optimize-at-edge/cs-fastly-disable-button.png)

   Per disabilitare l’indirizzamento in qualsiasi momento, torna alla sezione **Implementa le ottimizzazioni negli agenti IA** nella scheda **Configurazione CDN** e fai clic su **Disabilita**.

Inoltre, se hai bisogno di assistenza per i passaggi precedenti, contatta il team Adobe Account o `llmo-at-edge@adobe.com`.

## Risoluzione dei problemi

Se viene visualizzato un errore durante l’attivazione o la disattivazione dell’instradamento, l’aspetto sarà simile al seguente:

![Errore nella finestra di dialogo di conferma](/help/assets/optimize-at-edge/cs-fastly-confirmation-dialog-error.png)

Utilizza l’elenco seguente per identificare l’errore e segui le indicazioni.

1. **L’utente non dispone dell’accesso al prodotto LLMO**

   **Causa:** l’account utente non dispone del contesto di prodotto LLM Optimizer nel profilo Adobe IMS. Questo è necessario per i clienti a pagamento al fine di configurare l’indirizzamento CDN.

   **Consiglio:** verifica che l’amministratore della tua organizzazione ti abbia assegnato il profilo di prodotto **Utenti Adobe LLM Optimizer** in Adobe Admin Console.

2. **Solo i membri del gruppo LLMO Admin possono configurare l’indirizzamento CDN**

   **Causa:** il tuo account non è iscritto al gruppo IMS **LLMO Admin**. Questo è necessario per i clienti di prova al fine di configurare l’indirizzamento CDN.

   **Consiglio:** verifica di essere stato aggiunto al gruppo IMS **LLMO Admin** in Adobe Admin Console dall’amministratore della tua organizzazione.

3. **Il tipo di CDN richiesto aem-cs-fastly non corrisponde alla CDN rilevata per questo dominio**

   **Causa:** indica che il tipo di CDN rilevato per il sito non è *CDN gestita da AEM Cloud Service (Fastly)*.

   **Consiglio:** verifica che il tuo sito sia gestito tramite CDN gestita da AEM Cloud Service (Fastly).

4. **Errore durante la verifica del sito**

   **Causa:** LLM Optimizer non è stato in grado di raggiungere il sito durante la configurazione dell’indirizzamento. Ciò può accadere se il sito non è accessibile, se non è raggiungibile o se la richiesta è scaduta.

   **Consiglio:** verifica che il sito sia accessibile al pubblico e restituisca una risposta valida, quindi riprova.

5. **Il sito non ha restituito una risposta valida per la verifica dell’indirizzamento**

   **Causa:** il sito ha restituito uno stato HTTP imprevisto (non 2xx o 301) quando è stato analizzato durante la configurazione.

   **Consiglio:** verifica che il sito restituisca una risposta corretta (2xx) per l’URL di base registrato in LLM Optimizer, quindi riprova.

6. **Autenticazione non riuscita con il servizio IMS upstream**

   **Causa:** la sessione potrebbe essere scaduta o si è verificato un problema di autenticazione con Adobe IMS durante la richiesta di indirizzamento.

   **Consiglio:** disconnettiti da LLM Optimizer e accedi di nuovo, quindi prova ad abilitare di nuovo l’indirizzamento.

Se il problema persiste, contatta il team Adobe Account o `llmo-at-edge@adobe.com`.

## (Facoltativo) Verificare la configurazione

Dopo aver completato la configurazione dell’indirizzamento, puoi verificare che il traffico proveniente da bot IA venga indirizzato al servizio di Ottimizzazione sulla rete Edge e che il traffico da persone non sia interessato da alcuna modifica.

1. **Test del traffico da bot (deve risultare ottimizzato)**

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

2. **Test del traffico da persone (deve risultare NON interessato da modifiche)**

   Simula una normale richiesta inserita da una persona nel browser:

   ```
   curl -svo /dev/null https://www.example.com/page.html \
     --header "user-agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36"
   ```

   La risposta non deve contenere l’intestazione `x-edgeoptimize-request-id`. Il contenuto della pagina e il tempo di risposta devono risultare identici rispetto a prima che sia stata abilitata la funzione Ottimizza su rete Edge.

3. **Differenze tra i due scenari**

   | Intestazione | Traffico da bot (ottimizzato) | Traffico da persone (non interessato da modifiche) |
   |---|---|---|
   | `x-edgeoptimize-request-id` | Presente: contiene un ID di richiesta univoco | Assente |
   | `x-edgeoptimize-fo` | Presente solo in caso di failover (valore: `1`) | Assente |

4. **Verificare stato indirizzamento in LLM Optimizer**

   Puoi anche confermare l’indirizzamento nell’interfaccia utente di LLM Optimizer. Apri **Configurazione cliente** e seleziona la scheda **Configurazione CDN**. Quando l’indirizzamento è attivo, la sezione **Implementare le ottimizzazioni negli agenti IA** mostra **Completato**.

   ![Implementare le ottimizzazioni negli agenti IA - Completato](/help/assets/optimize-at-edge/cs-fastly-disable-button.png)

{{return-to-overview}}
