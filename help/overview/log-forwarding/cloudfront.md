---
title: Inoltro dei registri - CloudFront
description: Scopri come inoltrare i registri CDN da CloudFront al bucket S3 di Adobe per la raccolta dati relativa al traffico da IA agentica in LLM Optimizer.
feature: Agentic Traffic
autotag-review: '2026-05-15T17:43:07.178Z'
TQID: 'https://experienceleague.adobe.com/TXnY-eK1SUuKrlVoGWd2hZO5bjUqEspvyFmcyOuei3Q'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: d1956731-2adb-4bb7-8301-2b239254ac72
subfeature_v2: id: d23587d6-14d6-4e3f-9ee1-cc18623832e1id: e69d5a42-0217-4ca5-9396-a9a826a170da
topic_v2: id: d3cdead0-685a-4489-9250-4bb709942f66id: e1e0219c-f879-479f-8427-888ed2a6e9c2
source-git-commit: 7a92587197cf6a9eec6b01bd4eaeeaf1194d3088
workflow-type: tm+mt
source-wordcount: 466
ht-degree: 100%

---


# Inoltro dei registri: CloudFront {#log-forwarding-cloudfront}

Questa pagina spiega come inoltrare i registri CDN da CloudFront al bucket S3 di Adobe per la raccolta dati relativa al traffico da IA agentica. Per effettuare l’onboarding in LLM Optimizer, utilizza la pagina Configurazione CDN di LLM Optimizer. Al termine del processo di onboarding, segui i passaggi descritti in questa pagina per configurare l’inoltro dei registri nella console della dashboard di CloudFront.

## Passaggio 1: eseguire l’onboarding in LLM Optimizer {#step-1}

Nella pagina LLM Optimizer [https://llmo.now/](https://llmo.now/):

1. Vai alla **Dashboard Configurazione cliente**.

   ![Pulsante Configurazione](/help/overview/assets/log-forwarding/common/config-button.png)

1. Fai clic sulla scheda **Configurazione CDN**.

   ![Scheda Configurazione CDN](/help/overview/assets/log-forwarding/common/cdn-config-tab.png)

1. Fai clic su **Inizia**.

   <!-- ![Onboard CDN button](/help/overview/assets/log-forwarding/common/onboard-cdn-button.png)-->

1. Accanto ad **Attiva analisi traffico IA**, fai clic su **Configura**.

   ![Configura](/help/overview/assets/log-forwarding/common/configure.png)

1. Immetti il tuo ID **account AWS**.

   ![ID account AWS](/help/overview/assets/log-forwarding/cloudfront/cloudfront-aws-account.png)

1. Seleziona **CloudFront (BYOCDN)**.

   ![Seleziona CloudFront](/help/overview/assets/log-forwarding/cloudfront/cloudfront-select.png)

1. Fai clic su **Esegui onboarding**.

   ![Pulsante Esegui onboarding](/help/overview/assets/log-forwarding/common/onboard-button.png)

## Passaggio 2: abilitare la registrazione standard (console CloudFront) {#step-2}

Per abilitare la registrazione standard, dalla [console di gestione AWS](https://aws.amazon.com/it/console/):

1. Accedi alla [console CloudFront](https://console.aws.amazon.com/cloudfront/v4/home) e [aggiorna una distribuzione esistente](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/HowToUpdateDistribution.html#HowToUpdateDistributionProcedure).

1. Apri la scheda **Registrazione**.

1. Scegli **Aggiungi**, quindi seleziona il servizio di ricezione dei registri, in questo caso **Amazon S3**.

1. Per **Destinazione**, seleziona o crea la risorsa. Immetti il **nome del bucket**. Puoi copiare il valore dalla pagina di configurazione CDN di LLM Optimizer.

   ![Nome del bucket CloudFront](/help/overview/assets/log-forwarding/cloudfront/cloudfront-bucket-name.png)

1. Configura **Impostazioni aggiuntive**:

   - **Selezione campo**: scegli i campi del file di log. Consulta i campi obbligatori nella pagina di configurazione CDN di LLM Optimizer.

     ![Selezione campo CloudFront](/help/overview/assets/log-forwarding/cloudfront/cloudfront-field-selection.png)

   - **Partizionamento**: copia il **suffisso del percorso** dalla pagina di configurazione di LLM Optimizer.

     ![Partizionamento di CloudFront](/help/overview/assets/log-forwarding/cloudfront/cloudfront-partitioning.png)

   - **Formato di output**: il formato deve essere JSON.

     ![Formato di output di CloudFront](/help/overview/assets/log-forwarding/cloudfront/cloudfront-output-format.png)

1. Completa i passaggi per aggiornare o creare la distribuzione.

1. Nella pagina **Registri** verifica che, accanto alla distribuzione, sia visualizzato **Abilitata**.

## Abilitare la registrazione standard per la consegna tra account diversi {#cross-account}

L’**account di origine** (con distribuzione CloudFront) invia i registri di accesso all’**account di destinazione** (il bucket S3 visualizzato nella pagina di configurazione CDN di LLM Optimizer). Entrambi gli account devono disporre delle opportune autorizzazioni.

Ad esempio: l’account di origine `111111111111` invia i registri a un bucket S3 nell&#39;account di destinazione `222222222222`. Puoi utilizzare l’[AWS Command Line Interface](https://aws.amazon.com/it/cli/).

>[!NOTE]
>
>Nei comandi sottostanti, sostituisci il valore dell’ARN della destinazione di consegna (`arn:aws:logs:us-east-1:222222222222:delivery-destination:cloudfront-delivery-destination`) con il valore dell’**ARN della destinazione di consegna** dalla pagina di configurazione di LLM Optimizer.

![ARN della destinazione di consegna](/help/overview/assets/log-forwarding/cloudfront/cloudfront-delivery-destination-arn.png)

### Configurare l’account di origine {#source-account}

Successivamente, devi configurare l’account di origine:

1. **Crea un’origine di consegna**: sostituisci il nome e la distribuzione ARN:

   ```bash
   aws logs put-delivery-source --name s3-cf-delivery \
     --resource-arn arn:aws:cloudfront::111111111111:distribution/E1TR1RHV123ABC \
     --log-type ACCESS_LOGS
   ```

1. **Crea la consegna**: collega l’origine alla destinazione; utilizza l’ARN di destinazione del passaggio “Configurare l&#39;account di destinazione”:

   ```bash
   aws logs create-delivery --delivery-source-name s3-cf-delivery \
     --delivery-destination-arn arn:aws:logs:us-east-1:222222222222:delivery-destination:cloudfront-delivery-destination
   ```

1. **Verifica:**

   - Nell’account di **origine**: console CloudFront > your distribution (la tua distribuzione) > scheda **Logging (Registrazione)**. In **Tipo** dovrebbe essere visualizzata la consegna del registro S3 tra account diversi.
   - Nell’account di **destinazione**: console S3 > bucket. In quella cartella dovrebbero essere visualizzati il prefisso (ad esempio, `MyLogPrefix`) e i registri.
