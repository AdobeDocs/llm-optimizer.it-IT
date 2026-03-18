---
title: Panoramica sull’inoltro del registro BYOCDN
description: Scopri come inoltrare i registri CDN dal provider al bucket S3 di Adobe per la raccolta di dati sul traffico agente in LLM Optimizer.
feature: Agentic Traffic
source-git-commit: a1ba7684ccef9baf3452cc158fc0d6a12aa7adb8
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 3%

---


# Panoramica sull’inoltro del registro BYOCDN {#cdn-log-forwarding}

L’inoltro dei registri per una rete CDN gestita dal cliente (BYOCDN) è il processo di invio dei registri di accesso alla rete CDN al bucket Amazon S3 di Adobe, in modo che LLM Optimizer possa raccogliere e analizzare i dati del traffico agente. Senza l&#39;inoltro del registro CDN, il dashboard [Traffico agente](/help/dashboards/agentic-traffic.md) non può visualizzare le metriche.

Le guide fornite di seguito seguono lo stesso flusso di lavoro in due fasi:

1. **Onboarding in LLM Optimizer** — registra il tuo CDN nella pagina [Configurazione CDN](/help/dashboards/customer-configuration.md) per generare le credenziali S3 e i dettagli del percorso necessari.
2. **Configura la tua rete CDN**. Utilizza questi dettagli per creare un processo di inoltro log (o caricare manualmente i registri) nella console del provider CDN.

## Provider CDN {#cdn-providers}

Segui la guida corrispondente per il provider CDN.

| Fornitore CDN | Guida |
|---|---|
| Akamai | [Visualizza guida](/help/overview/log-forwarding/akamai.md) |
| Cloudflare | [Visualizza guida](/help/overview/log-forwarding/cloudflare.md) |
| CloudFront | [Visualizza guida](/help/overview/log-forwarding/cloudfront.md) |
| Fastly | [Visualizza guida](/help/overview/log-forwarding/fastly.md) |
| Imperva | [Visualizza guida](/help/overview/log-forwarding/imperva.md) |
| Altro (CDN manuale/non supportato) | [Visualizza guida](/help/overview/log-forwarding/other.md) |

>[!NOTE]
>
>Se il provider CDN non è elencato in precedenza, utilizza la guida **Altro (CDN manuale/non supportato)** relativa ai caricamenti manuali, agli script ad hoc e a qualsiasi CDN non supportato in modalità nativa.
