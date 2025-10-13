---
title: Opportunità di ottimizzazione
description: Scopri come utilizzare la dashboard delle opportunità per rilevare automaticamente come migliorare il sito al fine di aumentare la visibilità del marchio.
source-git-commit: a699f8f3c50f77d07f29cd354fd1ef8e6eed8ff9
workflow-type: tm+mt
source-wordcount: '668'
ht-degree: 0%

---


# Opportunità di ottimizzazione

Le opportunità di ottimizzazione vengono rilevate automaticamente in base a informazioni che mostrano dove è possibile migliorare la presenza sul sito e quella esterna, per aumentare la visibilità del brand nella ricerca basata su intelligenza artificiale.

Queste ottimizzazioni includono correzioni su pagina (aggiunta di contenuti strutturati, canonici o riepiloghi), adeguamenti tecnici (sblocco dei crawler di IA o risoluzione di errori) e influenza il contenuto su siti autorevoli di terze parti. Affrontare queste opportunità di ottimizzazione aiuta il tuo marchio ad essere rappresentato accuratamente e a essere citato più probabilmente in risposte generative.

![Opportunità di ottimizzazione](/help/dashboards/assets/oport.png)

## Dashboard opportunità

Le opportunità di ottimizzazione presentate nel dashboard vengono prioritizzate in base alle lacune del lettore, agli argomenti relativi alle tendenze e ai dati sulle prestazioni e presentate come un elenco. Puoi cercare un’opportunità specifica utilizzando il campo di ricerca. Inoltre, le opportunità sono raggruppate per tag ed è possibile fare clic direttamente su un tag per mostrare tutte le opportunità raggruppate sotto tale tag.

Facendo clic su **Dettagli** verrà aperta una finestra separata in cui vengono fornite ulteriori informazioni e indicazioni aggiuntive.

## opportunità supportate

Di seguito è riportata una tabella delle opportunità attualmente supportate:

| Opportunità | Tipo | Problemi identificati | Correggi suggerimenti |
|---------|----------|----------|----------|
| Riepiloga paragrafi lunghi | Contenuto (nel sito) | Rileva i paragrafi che superano le soglie di lunghezza consigliate. Mostra gli URL interessati e frammenti di testo di dimensioni eccessive. | Creare riassunti o dividere testo lungo in sezioni più brevi e digitalizzabili. |
| Consigliare contenuti strutturati (FAQ) | Contenuto (nel sito) | Rileva i prompt a popolarità elevata senza le voci di domanda corrispondenti. Mostra i prompt correlati, le categorie e gli URL interessati. | Aggiungi blocchi di schema di domande frequenti con risposte concise per far corrispondere le query comuni. |
| Rileva hreflang mancante | Contenuto (nel sito) | Segnala le pagine prive di attributi hreflang. Fornisce gli URL interessati e la copertura prevista per lingua/area geografica. | Implementa tag hreflang per indicare le versioni localizzate corrette. |
| Rileva Canonici Mancanti | Contenuto (nel sito) | Cerca le pagine senza tag canonici o con tag in conflitto. Elenca URL interessati e duplicati. | Aggiungi tag canonici che puntano alla versione preferita di ogni pagina. Assicurati di utilizzare in modo coerente le diverse varianti. |
| Rileva intestazioni vuote | Contenuto (nel sito) | Segnala le pagine in cui sono presenti tag di intestazione ma non contengono testo. Mostra URL e posizione di tag vuoti. | Aggiungi testo descrittivo alle intestazioni che riflettono il contenuto al di sotto di esse. |
| Rileva titoli duplicati | Contenuto (nel sito) | Esegue la scansione dei tag di intestazione di HTML e contrassegna le intestazioni ripetute. Mostra gli URL interessati e i frammenti di testo duplicati. | Modifica le intestazioni in modo che siano univoche e mantieni la gerarchia (H1 → H2 → H3). Unire o rinominare sezioni duplicate. |
| Rileva traffico agente bloccato | GEO tecnico | Analizza i registri CDN per le richieste bloccate da agenti di intelligenza artificiale noti (ad esempio, GPTBot, PerplexityBot). Segnala gli URL e gli agenti interessati. | Se necessario, aggiorna robots.txt o le configurazioni server per consentire l’accesso ai crawler di IA supportati. |
| Rileva problemi 404s / 403s / 5xx | GEO tecnico | Esegue il monitoraggio dei registri CDN per le risposte di errore. Segnala la frequenza, gli URL interessati e gli hit stimati persi. | Correggi i collegamenti interrotti, aggiorna le autorizzazioni e risolvi i problemi lato server in modo che il contenuto chiave restituisca 200 risposte. |
| Recupero visibilità dei contenuti (accesso anticipato) | GEO tecnico | Segnala le pagine in cui il contenuto critico è nascosto dagli agenti di intelligenza artificiale. Mostra gli URL interessati e il contenuto previsto che può essere recuperato. | Esegui il pre-rendering delle pagine in modo che sia disponibile più contenuto per gli agenti di intelligenza artificiale senza esecuzione di JavaScript. |

### Opportunità di visibilità del ripristino dei contenuti {#recover-contet}

Come indicato in precedenza, l’opportunità di visibilità dei contenuti contrassegna le pagine in cui i contenuti chiave vengono persi per gli agenti AI a causa del rendering lato client. Per ogni pagina identificata, mostra esattamente quale contenuto manca dalla vista dell’agente di intelligenza artificiale, aiutandoti a individuare i vuoti di visibilità. È inoltre supportato da una funzionalità di pre-rendering basata su server perimetrali che può distribuire più contenuti HTML al traffico di agenti senza richiedere modifiche al sistema di gestione dei contenuti (CMS). Questa funzionalità è attualmente in fase di accesso anticipato e richiede la configurazione da parte del team LLM Optimizer. Contatta `llmo-at-edge@adobe.com` per attivare l&#39;opportunità di visibilità dei contenuti.

### Strumenti aggiuntivi

Il controllo di visibilità [LLM](https://chromewebstore.google.com/detail/is-your-webpage-citable/jbjngahjjdgonbeinjlepfamjdmdcbcc) è un&#39;estensione di Chrome che consente di visualizzare esattamente la quantità di contenuto della pagina Web a cui i moduli LLM possono accedere e ciò che rimane nascosto. Progettato come strumento diagnostico indipendente e gratuito, non richiede alcuna licenza o configurazione del prodotto. Con un solo clic, gli utenti possono valutare la leggibilità automatica di qualsiasi sito, visualizzando un confronto affiancato tra ciò che gli agenti di intelligenza artificiale visualizzano e ciò che gli utenti umani vedono. Inoltre, stima la quantità di contenuto che può essere recuperata utilizzando LLM Optimizer.
