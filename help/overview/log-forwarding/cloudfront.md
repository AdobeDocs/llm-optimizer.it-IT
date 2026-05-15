---
title: Inoltro log - CloudFront
description: Scopri come inoltrare i registri CDN da CloudFront al bucket S3 di Adobe per la raccolta di dati sul traffico agente in LLM Optimizer.
feature: Agentic Traffic
autotag-review: '2026-05-15T17:43:07.178Z'
TQID: 'https://experienceleague.adobe.com/TXnY-eK1SUuKrlVoGWd2hZO5bjUqEspvyFmcyOuei3Q'
product_v2:
  - id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2:
  - id: d1956731-2adb-4bb7-8301-2b239254ac72
subfeature_v2:
  - id: d23587d6-14d6-4e3f-9ee1-cc18623832e1
  - id: e69d5a42-0217-4ca5-9396-a9a826a170da
topic_v2:
  - id: d3cdead0-685a-4489-9250-4bb709942f66
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
source-git-commit: 7a92587197cf6a9eec6b01bd4eaeeaf1194d3088
workflow-type: tm+mt
source-wordcount: 466
ht-degree: 0%

---


# Inoltro registro: CloudFront {#log-forwarding-cloudfront}

Questa pagina spiega come inoltrare i registri CDN da CloudFront al bucket S3 di Adobe per la raccolta di dati sul traffico agente. Per effettuare l’onboarding in LLM Optimizer, utilizza la pagina Configurazione CDN di LLM Optimizer. Al termine del processo di onboarding, segui i passaggi descritti in questa pagina per configurare l’inoltro dei registri nella console della dashboard di CloudFront.

## Passaggio 1: onboarding in LLM Optimizer {#step-1}

Nella pagina LLM Optimizer [https://llmo.now/](https://llmo.now/):

1. Vai a **Dashboard configurazione cliente**.

   ![Pulsante Configurazione](/help/overview/assets/log-forwarding/common/config-button.png)

1. Fare clic sulla scheda **Configurazione CDN**.

   ![Scheda Configurazione CDN](/help/overview/assets/log-forwarding/common/cdn-config-tab.png)

1. Fai clic su **Inizia**.

   <!-- ![Onboard CDN button](/help/overview/assets/log-forwarding/common/onboard-cdn-button.png)-->

1. Accanto a **Attiva analisi traffico IA**, fai clic su **Configura**.

   ![Configura](/help/overview/assets/log-forwarding/common/configure.png)

1. Immetti l&#39;**account AWS** ID.

   ![ID account AWS](/help/overview/assets/log-forwarding/cloudfront/cloudfront-aws-account.png)

1. Selezionare **CloudFront (BYOCDN)**.

   ![Seleziona CloudFront](/help/overview/assets/log-forwarding/cloudfront/cloudfront-select.png)

1. Fare clic su **Onboard**.

   ![Pulsante Onboard](/help/overview/assets/log-forwarding/common/onboard-button.png)

## Passaggio 2: abilitare la registrazione standard (console CloudFront) {#step-2}

Per abilitare la registrazione standard, dalla [console di gestione AWS](https://aws.amazon.com/console/):

1. Accedi alla [console CloudFront](https://console.aws.amazon.com/cloudfront/v4/home) e [aggiorna una distribuzione esistente](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/HowToUpdateDistribution.html#HowToUpdateDistributionProcedure).

1. Apri la scheda **Registrazione**.

1. Scegli **Aggiungi**, quindi seleziona il servizio per la ricezione dei registri, in questo caso **Amazon S3**.

1. Per **Destinazione**, seleziona o crea la risorsa. Immetti il **nome bucket**. Puoi copiare il valore dalla pagina di configurazione CDN di LLM Optimizer.

   ![Nome bucket CloudFront](/help/overview/assets/log-forwarding/cloudfront/cloudfront-bucket-name.png)

1. Configura **Impostazioni aggiuntive**:

   - **Selezione campo** — scegliere i campi del file di log. Consulta i campi obbligatori nella pagina di configurazione CDN di LLM Optimizer.

     ![Selezione campo CloudFront](/help/overview/assets/log-forwarding/cloudfront/cloudfront-field-selection.png)

   - **Partizionamento** — copia il **suffisso percorso** dalla pagina di configurazione di LLM Optimizer.

     ![Partizionamento di CloudFront](/help/overview/assets/log-forwarding/cloudfront/cloudfront-partitioning.png)

   - **Formato di output**. Il formato deve essere JSON.

     ![Formato di output CloudFront](/help/overview/assets/log-forwarding/cloudfront/cloudfront-output-format.png)

1. Completa i passaggi per aggiornare o creare la distribuzione.

1. Nella pagina **Registri**, verifica che **Abilitato** sia visualizzato accanto alla distribuzione.

## Abilita registrazione standard per la consegna tra account diversi {#cross-account}

L&#39;**account di origine** (con distribuzione CloudFront) invia i registri di accesso all&#39;**account di destinazione** (il bucket S3 visualizzato nella pagina di configurazione CDN di LLM Optimizer). Entrambi gli account devono disporre delle autorizzazioni appropriate.

Ad esempio: l&#39;account di origine `111111111111` invia i registri a un bucket S3 nell&#39;account di destinazione `222222222222`. È possibile utilizzare [AWS Commad Line Interface](https://aws.amazon.com/cli/).

>[!NOTE]
>
>Nei comandi seguenti, sostituire il valore ARN della destinazione di consegna (`arn:aws:logs:us-east-1:222222222222:delivery-destination:cloudfront-delivery-destination`) con il valore di **ARN della destinazione di consegna** dalla pagina di configurazione di LLM Optimizer.

![ARN destinazione consegna](/help/overview/assets/log-forwarding/cloudfront/cloudfront-delivery-destination-arn.png)

### Configurare l’account sorgente {#source-account}

Successivamente, devi configurare l’account di origine:

1. **Crea un&#39;origine di consegna**. Sostituire il nome e la distribuzione ARN:

   ```bash
   aws logs put-delivery-source --name s3-cf-delivery \
     --resource-arn arn:aws:cloudfront::111111111111:distribution/E1TR1RHV123ABC \
     --log-type ACCESS_LOGS
   ```

1. **Creare la consegna** - collegare l&#39;origine alla destinazione; utilizzare l&#39;ARN di destinazione dal passaggio &quot;Configurare l&#39;account di destinazione&quot;:

   ```bash
   aws logs create-delivery --delivery-source-name s3-cf-delivery \
     --delivery-destination-arn arn:aws:logs:us-east-1:222222222222:delivery-destination:cloudfront-delivery-destination
   ```

1. **Verifica:**

   - Nell&#39;account **source**: console CloudFront > distribuzione > scheda **Registrazione**. In **Type** dovresti vedere la consegna del registro tra account diversi S3.
   - Nell&#39;account **destinazione**: console S3 > bucket. Dovresti visualizzare il prefisso (ad esempio, `MyLogPrefix`) e i registri in quella cartella.
