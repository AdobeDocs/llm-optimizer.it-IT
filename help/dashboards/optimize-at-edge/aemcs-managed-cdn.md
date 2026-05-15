---
title: Ottimizzazione sulla rete edge - CDN gestita da AEM Cloud Service (Fastly)
description: Scopri come configurare la rete CDN gestita da AEM Cloud Service (Fastly) per l’ottimizzazione su rete edge in LLM Optimizer.
feature: Opportunities
autotag-review: '2026-05-15T17:31:38.650Z'
TQID: 'https://experienceleague.adobe.com/qrCODY3Qg6dDd9QRcaYGdN4YVCgKAsl56UTAVZpsIwE'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: d1956731-2adb-4bb7-8301-2b239254ac72id: e0828736-236a-487b-a478-5a635455eadc
subfeature_v2: id: d23587d6-14d6-4e3f-9ee1-cc18623832e1id: e06fae5f-830b-4222-a469-b5e148d36465
topic_v2: id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
source-git-commit: 7a92587197cf6a9eec6b01bd4eaeeaf1194d3088
workflow-type: tm+mt
source-wordcount: 836
ht-degree: 20%

---


# CDN gestita da AEM Cloud Service (Fastly)

Questa configurazione indirizza il traffico da IA agentica (richieste da bot IA e da agenti utente LLM) al servizio back-end Edge Optimize (`live.edgeoptimize.net`). Le persone e i bot SEO continuano a ricevere come al solito i contenuti trasmessi dalla tua origine. Per verificare la configurazione, al termine dell&#39;installazione, controllare l&#39;intestazione `x-edgeoptimize-request-id` nella risposta.

## Prerequisiti

Per accedere a questa funzione:

- I clienti a pagamento devono avere accesso al profilo di prodotto IMS **Utenti Adobe LLM Optimizer**. Contatta l’amministratore della tua organizzazione per richiedere l’accesso.
  ![Aggiungi utente a un profilo di prodotto](/help/assets/optimize-at-edge/cs-fastly-user-product-profiles.png)
- I clienti di prova devono far parte del gruppo IMS **LLMO Admin**. Se il gruppo non esiste, l’amministratore dell’organizzazione può crearlo e aggiungerti.
  ![Crea gruppo IMS di amministrazione LLMO](/help/assets/optimize-at-edge/cs-fastly-create-ims-group.png)

>[!NOTE]
> Questa funzione non è supportata in Safari o nelle modalità di navigazione in incognito/privata.

## Passaggi per abilitare l’instradamento

Per iniziare a indirizzare il traffico da IA agentica al servizio Edge Optimize:

1. In LLM Optimizer, apri **Configurazione cliente** e seleziona la scheda **Configurazione CDN**.

   ![Passa a Configurazione cliente](/help/assets/optimize-at-edge/cs-fastly-prereq-customer-config-nav.png)

2. Individua la sezione **Distribuire le ottimizzazioni agli agenti di IA**. Fare clic sul pulsante **Abilita**.

   ![Distribuzione ottimizzazioni agli agenti di IA - in sospeso](/help/assets/optimize-at-edge/cs-fastly-enable-button.png)

3. Nella finestra di dialogo di conferma, selezionare **Abilita** per confermare che si desidera abilitare il routing. Se viene visualizzato un errore, fare riferimento alla sezione [Risoluzione dei problemi](#troubleshooting) per risolverlo.

   ![Abilita la finestra di dialogo di conferma del motore di ottimizzazione](/help/assets/optimize-at-edge/cs-fastly-enable-dialog.png)

4. Una volta confermato, il completamento del routing richiede alcuni minuti.

   ![Routing in corso](/help/assets/optimize-at-edge/cs-fastly-enable-button-clicked-routing-in-progress.png)

   Ricarica la pagina dopo 5 minuti per verificare che il routing sia stato completato. Una volta configurato e attivato il routing, lo stato diventa **Completato** con un segno di spunta verde a conferma dell&#39;abilitazione del routing. Non sono richiesti ulteriori interventi da parte tua.

   ![Distribuzione delle ottimizzazioni agli agenti di IA - completata](/help/assets/optimize-at-edge/cs-fastly-disable-button.png)

   Per disabilitare il routing in qualsiasi momento, tornare alla sezione **Distribuisci ottimizzazioni agli agenti AI** nella scheda **Configurazione CDN** e fare clic su **Disabilita**.

Inoltre, se hai bisogno di assistenza per i passaggi precedenti, contatta il team Adobe Account o `llmo-at-edge@adobe.com`.

## Risoluzione dei problemi

Se viene visualizzato un errore durante l&#39;attivazione o la disattivazione del routing, l&#39;aspetto sarà simile al seguente:

![Errore finestra di conferma](/help/assets/optimize-at-edge/cs-fastly-confirmation-dialog-error.png)

Utilizza l’elenco seguente per identificare l’errore e seguire le indicazioni.

1. **L&#39;utente non dispone dell&#39;accesso al prodotto LLMO**

   **Causa:** l&#39;account utente non dispone del contesto di prodotto LLM Optimizer nel profilo Adobe IMS. Questo è necessario per i clienti a pagamento per configurare il routing CDN.

   **Consiglio:** verifica che il tuo amministratore organizzazione ti abbia assegnato il profilo di prodotto **Utenti Adobe LLM Optimizer** in Adobe Admin Console.

2. **Solo i membri del gruppo di amministrazione LLMO possono configurare il routing CDN**

   **Causa:** il tuo account non è membro del gruppo IMS **LLMO Admin**. Questo è necessario per i clienti di prova che devono configurare il routing CDN.

   **Consiglio:** verifica di essere stato aggiunto al gruppo IMS **LLMO Admin** in Adobe Admin Console dall&#39;amministratore organizzazione.

3. **Il tipo di CDN richiesto aem-cs-fastly non corrisponde al CDN rilevato per questo dominio**

   **Causa:** indica che il tipo di rete CDN rilevato per il sito non è *rete CDN gestita AEM Cloud Service (Fastly)*.

   **Consiglio:** verifica che il tuo sito sia gestito tramite CDN gestito da AEM Cloud Service (Fastly).

4. **Errore durante il probe del sito**

   **Causa:** LLM Optimizer non è stato in grado di raggiungere il sito durante la configurazione del routing. Ciò può accadere se il sito non è accessibile, se non è raggiungibile o se la richiesta è scaduta.

   **Consiglio:** Verificare che il sito sia accessibile al pubblico e restituire una risposta valida, quindi riprovare.

5. **Il sito non ha restituito una risposta valida per il probe di routing**

   **Causa:** il sito ha restituito uno stato HTTP imprevisto (non 2xx o 301) quando è stato analizzato durante l&#39;installazione.

   **Consiglio:** Verificare che il sito restituisca una risposta corretta (2xx) per l&#39;URL di base registrato in LLM Optimizer, quindi riprovare.

6. **Autenticazione non riuscita con il servizio IMS upstream**

   **Causa:** La sessione potrebbe essere scaduta o si è verificato un problema di autenticazione con Adobe IMS durante la richiesta di routing.

   **Consiglio:** Esci da LLM Optimizer e accedi di nuovo, quindi prova ad abilitare di nuovo il routing.

Se il problema persiste, contatta il team del tuo account Adobe o `llmo-at-edge@adobe.com`.

## (Facoltativo) Verifica l’installazione

Una volta completata la configurazione di indirizzamento, puoi facoltativamente verificare che il traffico da bot AI sia instradato ad Edge Optimize e che il traffico umano non venga influenzato.

1. **Verifica traffico da bot (deve essere ottimizzato)**

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

2. **Test del traffico umano (non dovrebbe essere interessato)**

   Simula una normale richiesta inserita da una persona nel browser:

   ```
   curl -svo /dev/null https://www.example.com/page.html \
     --header "user-agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36"
   ```

   La risposta non deve contenere l&#39;intestazione `x-edgeoptimize-request-id`. Il contenuto della pagina e il tempo di risposta devono risultare identici rispetto a prima che sia stata abilitata la funzione Ottimizza su rete edge.

3. **Come distinguere tra i due scenari**

   | Intestazione | Traffico da bot (ottimizzato) | Traffico da persone (non interessato da modifiche) |
   |---|---|---|
   | `x-edgeoptimize-request-id` | Presente: contiene un ID di richiesta univoco | Assente |
   | `x-edgeoptimize-fo` | Presente solo in caso di failover (valore: `1`) | Assente |

4. **Verifica stato routing in LLM Optimizer**

   Puoi anche confermare il routing nell’interfaccia utente di LLM Optimizer. Apri **Configurazione del cliente** e seleziona la scheda **Configurazione CDN**. Quando il routing è attivo, nella sezione **Distribuisci ottimizzazioni agli agenti di IA** viene visualizzato **Completato**.

   ![Distribuzione delle ottimizzazioni agli agenti di IA - completata](/help/assets/optimize-at-edge/cs-fastly-disable-button.png)

{{return-to-overview}}
