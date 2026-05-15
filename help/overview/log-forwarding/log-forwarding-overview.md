---
title: Panoramica sull’inoltro del registro BYOCDN
description: Scopri come inoltrare i registri CDN dal provider al bucket S3 di Adobe per la raccolta di dati sul traffico agente in LLM Optimizer.
feature: Agentic Traffic
autotag-review: '2026-05-15T17:53:26.846Z'
TQID: 'https://experienceleague.adobe.com/EPQ6GBjNXpIwYTuzj1xDKkIzuFLOWFPmu0lqSGUAX3I'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: a0b5a505-2fd7-4c3d-b61c-b557fb6f0558id: d1956731-2adb-4bb7-8301-2b239254ac72
subfeature_v2: id: d23587d6-14d6-4e3f-9ee1-cc18623832e1
topic_v2: id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: 564171851fdccee43afd233da143d66182464889
workflow-type: tm+mt
source-wordcount: 215
ht-degree: 2%

---


# Panoramica sull’inoltro del registro BYOCDN {#cdn-log-forwarding}

L’inoltro dei registri per una rete CDN gestita dal cliente (BYOCDN) è il processo di invio dei registri di accesso alla rete CDN al bucket Amazon S3 di Adobe, in modo che LLM Optimizer possa raccogliere e analizzare i dati del traffico agente. Senza l&#39;inoltro del registro CDN, il dashboard [Traffico agente](/help/dashboards/agentic-traffic.md) non può visualizzare le metriche.

Le guide fornite di seguito seguono lo stesso flusso di lavoro in due fasi:

1. **Onboarding in LLM Optimizer** — registra il tuo CDN nella pagina [Configurazione CDN](/help/dashboards/customer-configuration.md) per generare le credenziali S3 e i dettagli del percorso necessari.
2. **Configura la tua rete CDN**. Utilizza questi dettagli per creare un processo di inoltro log (o caricare manualmente i registri) nella console del provider CDN. Per CloudFront, puoi utilizzare la console o completare la configurazione della consegna solo con **AWS CLI**; vedi [CloudFront (AWS CLI)](/help/overview/log-forwarding/cloudfront-cli.md).

## Provider CDN {#cdn-providers}

Segui la guida corrispondente per il provider CDN.

| Fornitore CDN | Guida |
|---|---|
| Akamai | [Visualizza guida](/help/overview/log-forwarding/akamai.md) |
| Cloudflare | [Visualizza guida](/help/overview/log-forwarding/cloudflare.md) |
| CloudFront (console) | [Visualizza guida](/help/overview/log-forwarding/cloudfront.md) |
| CloudFront (AWS CLI) | [Visualizza guida](/help/overview/log-forwarding/cloudfront-cli.md) |
| Fastly | [Visualizza guida](/help/overview/log-forwarding/fastly.md) |
| Imperva | [Visualizza guida](/help/overview/log-forwarding/imperva.md) |
| Altro (CDN manuale/non supportato) | [Visualizza guida](/help/overview/log-forwarding/other.md) |

>[!NOTE]
>
>Se il provider CDN non è elencato in precedenza, utilizza la guida **Altro (CDN manuale/non supportato)** relativa ai caricamenti manuali, agli script ad hoc e a qualsiasi CDN non supportato in modalità nativa.
