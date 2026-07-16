---
title: Panoramica sull’inoltro dei registri BYOCDN
description: Scopri come inoltrare i registri CDN dal tuo provider al bucket S3 di Adobe per la raccolta di dati sul traffico da IA agentica in LLM Optimizer.
feature: Agentic Traffic
autotag-review: '2026-07-15T18:07:52.453Z'
TQID: 'https://experienceleague.adobe.com/iN1Tm-7j2FTQ1UodWvCZpOSy0FnQEyMkBMZIL9z3t38'
product_v2:
  - id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2:
  - id: d1956731-2adb-4bb7-8301-2b239254ac72
  - id: ef4e63f5-cb4d-462d-bf9a-1f617edf2a3a
  - id: e0828736-236a-487b-a478-5a635455eadc
subfeature_v2:
  - id: d23587d6-14d6-4e3f-9ee1-cc18623832e1
  - id: dd952468-5202-43af-a365-6e0d2e67a703
  - id: e06fae5f-830b-4222-a469-b5e148d36465
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: d3cdead0-685a-4489-9250-4bb709942f66
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 2705cf26faea9c09817bbdcec4b4c531552df7ba
workflow-type: tm+mt
source-wordcount: 215
ht-degree: 100%

---


# Panoramica sull’inoltro dei registri BYOCDN {#cdn-log-forwarding}

L’inoltro dei registri di una CDN gestita dal cliente (BYOCDN) è il processo di invio dei registri di accesso alla CDN al bucket Amazon S3 di Adobe, affinché LLM Optimizer possa raccogliere e analizzare i dati relativi al traffico da IA agentica. Senza l’inoltro del registro CDN, la dashboard [Traffico da IA agentica](/help/dashboards/agentic-traffic.md) non può visualizzare metriche.

Le guide fornite di seguito seguono lo stesso flusso di lavoro in due fasi:

1. **Onboarding in LLM Optimizer**: registra la tua CDN nella pagina [Configurazione CDN](/help/dashboards/customer-configuration.md) per generare le credenziali S3 necessarie e i dettagli del percorso.
2. **Configura la tua CDN**: utilizza questi dettagli per creare un processo di inoltro dei registri (o caricare manualmente i registri) nella console del provider CDN. Per CloudFront, puoi utilizzare la console o completare la configurazione della consegna solo con **AWS CLI**; consulta [CloudFront (AWS CLI)](/help/overview/log-forwarding/cloudfront-cli.md).

## Provider CDN {#cdn-providers}

Segui la guida corrispondente al tuo provider CDN.

| Fornitore CDN | Guida |
|---|---|
| Akamai | [Visualizza guida](/help/overview/log-forwarding/akamai.md) |
| Cloudflare | [Visualizza guida](/help/overview/log-forwarding/cloudflare.md) |
| CloudFront (console) | [Visualizza guida](/help/overview/log-forwarding/cloudfront.md) |
| CloudFront (AWS CLI) | [Visualizza guida](/help/overview/log-forwarding/cloudfront-cli.md) |
| Fastly | [Visualizza guida](/help/overview/log-forwarding/fastly.md) |
| Imperva | [Visualizza guida](/help/overview/log-forwarding/imperva.md) |
| Altro (CDN manuale/non supportata) | [Visualizza guida](/help/overview/log-forwarding/other.md) |

>[!NOTE]
>
>Se il provider CDN non è elencato in precedenza, utilizza la guida per **Altro (CDN manuale/non supportata)** relativa ai caricamenti manuali, agli script ad hoc e a qualsiasi CDN non supportata in modalità nativa.
