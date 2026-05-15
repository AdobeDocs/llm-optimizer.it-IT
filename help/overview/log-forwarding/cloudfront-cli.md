---
title: Inoltro log - CloudFront (AWS CLI)
description: Inoltra i registri CDN di CloudFront al bucket S3 di Adobe utilizzando AWS CLI per la configurazione e le operazioni di consegna.
feature: Agentic Traffic
autotag-review: '2026-05-15T17:42:44.992Z'
TQID: 'https://experienceleague.adobe.com/NoVv3qv1RbtqAWGMPYC1Rz4wO-5Au1yL2e8tRKd9Hao'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: d1956731-2adb-4bb7-8301-2b239254ac72
subfeature_v2: id: d23587d6-14d6-4e3f-9ee1-cc18623832e1id: e69d5a42-0217-4ca5-9396-a9a826a170da
topic_v2: id: d3cdead0-685a-4489-9250-4bb709942f66id: e1e0219c-f879-479f-8427-888ed2a6e9c2
source-git-commit: 7a92587197cf6a9eec6b01bd4eaeeaf1194d3088
workflow-type: tm+mt
source-wordcount: 379
ht-degree: 0%

---


# Inoltro log: CloudFront (AWS CLI) {#log-forwarding-cloudfront-cli}

Questa pagina illustra come inoltrare i registri CDN da CloudFront al bucket S3 di Adobe per la raccolta di dati sul traffico agente. Per effettuare l’onboarding in LLM Optimizer, utilizza la pagina Configurazione CDN di LLM Optimizer. Al termine del processo di onboarding, segui i passaggi forniti in questa pagina per configurare l&#39;inoltro dei registri utilizzando [AWS Command Line Interface](https://aws.amazon.com/cli/) in [Passaggio 2](#step-2-cli).

>[!NOTE]
>
> In questa guida viene illustrato come configurare l&#39;inoltro dei registri utilizzando l&#39;[interfaccia della riga di comando di AWS](https://aws.amazon.com/cli/). Se desideri configurare l&#39;inoltro del registro utilizzando la **interfaccia utente di CloudFront**, consulta [Inoltro del registro: CloudFront](/help/overview/log-forwarding/cloudfront.md).

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

<!--  ![AWS Account ID](/help/overview/assets/log-forwarding/cloudfront/cloudfront-aws-account.png)-->

1. Selezionare **CloudFront (BYOCDN)**.

   ![Seleziona CloudFront](/help/overview/assets/log-forwarding/cloudfront/cloudfront-select.png)

1. Fare clic su **Onboard**.

<!-- ![Onboard button](/help/overview/assets/log-forwarding/common/onboard-button.png)-->

## Passaggio 2: configurare l’inoltro del registro CDN con AWS CLI {#step-2-cli}

Imposta l’inoltro del registro CDN con AWS CLI come segue:

### Configurare le credenziali CLI di AWS

Configura le credenziali CLI di AWS MAC. Aprire ~/.aws/credentials e immettere i valori per le variabili seguenti:

```text
[LLMO]
aws_access_key_id=<VALUE_OF_ACCESS_KEY_ID>
aws_secret_access_key=<VALUE_OF_SECRET_KEY>
aws_session_token=<ONLY_IF_USING_SECURITY_TOKEN_SERVICE> ## Optional
```

### Verifica la connessione

Esegui il comando seguente per verificare la connessione:

```bash
aws sts get-caller-identity --profile LLMO
```

Esempio di output di successo:

```bash
aws sts get-caller-identity --profile LLMO
{
    "UserId": "AxxxxxxxxxxxP:user",
    "Account": "012345678912",
    "Arn": "arn:aws:sts::012345678912:assumed-role/klam-master-role-BatlY3dnPVinQLC/user"
}
```

### Inizializzare le variabili

Sostituisci `REPLACEME123@AdobeOrg` con l&#39;ID organizzazione Adobe IMS ed esegui il comando seguente. L&#39;ID di output di questo comando verrà indicato come `TRANSFORM_IMS_ID`.

```bash
echo "REPLACEME123@AdobeOrg" | sed 's/@AdobeOrg$//' | tr '[:upper:]' '[:lower:]'
```

Immettere i valori per `CUSTOMER`, `CDN_ID`, `ACCT1` e `TRANSFORM_IMS_ID` seguendo le istruzioni di seguito, quindi eseguire i comandi dal terminale.

```bash
export PROFILE1=LLMO
export REGION1=us-east-1
export CUSTOMER=<CUSTOMER_NAME> ## No Space, user letters,numbers and dash
export CDN_ID=<YOUR_CLOUDFRONT_DISTRIBUTION_ID>
export ACCT1=<YOUR_AWS_ACCOUNT_NUMBER>
export DELIVERY_DEST_ARN=arn:aws:logs:us-east-1:640168421876:delivery-destination:cdn-logs-<TRANSFORM_IMS_ID>-ams  ## Replace TRANSFORM_IMS_ID with the output of the command above
```

<!--Use the **Delivery destination ARN** and org values from the LLM Optimizer CDN configuration page if they differ from the pattern above.-->

### Creare l’origine di consegna

Dallo stesso terminale in cui è stato eseguito il passaggio 3, eseguire il comando seguente:

```bash
aws logs put-delivery-source --name llmo-cf-${CUSTOMER}-${CDN_ID} \
  --profile $PROFILE1 --region $REGION1 \
  --resource-arn arn:aws:cloudfront::${ACCT1}:distribution/${CDN_ID} \
  --log-type ACCESS_LOGS
```

>[!IMPORTANT]
>
>Se si verifica il seguente errore, cercare l&#39;origine di consegna esistente: *Si è verificato un errore (ConflictException) durante la chiamata dell&#39;operazione PutDeliverySource: questo ResourceId è già stato utilizzato in un altro Source di consegna in questo account.*
>
>Per cercare l’origine di consegna esistente, esegui questo comando:
>
>```bash
>aws logs describe-delivery-sources --region us-east-1 \
>--query "deliverySources[?contains(resourceArns[0], '<CDN DistributionID>')]"
>```
>
>Nel comando successivo, utilizza il nome dell’origine di consegna dai risultati del comando precedente.

### Creare la configurazione della consegna

```bash
aws logs create-delivery \
  --profile "$PROFILE1" --region "$REGION1" \
  --delivery-source-name "llmo-cf-${CUSTOMER}-${CDN_ID}" \
  --delivery-destination-arn $DELIVERY_DEST_ARN \
  --s3-delivery-configuration '{"suffixPath":"/{yyyy}/{MM}/{dd}/{HH}"}' \
  --record-fields 'date' 'time' 'x-edge-location' 'cs-method' 'cs(Host)' 'cs-uri-stem' 'sc-status' 'cs(Referer)' 'cs(User-Agent)' 'time-to-first-byte' 'sc-content-type' 'x-host-header'
```

&lt;!—Allinea `--record-fields` e `--s3-delivery-configuration` con l&#39;elenco dei campi e il suffisso del percorso visualizzati nella pagina di configurazione CDN di LLM Optimizer se cambiano la documentazione o i valori dei prodotti.—>
