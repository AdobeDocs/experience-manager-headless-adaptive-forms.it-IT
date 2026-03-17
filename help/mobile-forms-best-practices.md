---
title: Best practice per i moduli mobili
description: Per i casi di utilizzo di moduli mobili e offline, crea un’app nativa e recupera le definizioni dei moduli tramite l’API Forms adattiva headless. Approccio consigliato per le applicazioni mobile native.
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: moduli mobili, app nativa, moduli offline, API headless
index: true
exl-id: 6f25039f-61fc-4366-9e17-6b2809162c58
source-git-commit: 86129488bec7faed87600a237ac034ca1b601187
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---

# Best practice per i moduli mobili {#mobile-forms-best-practices}

Per i casi di utilizzo di moduli per dispositivi mobili e offline, l’approccio consigliato è quello di creare un’app nativa e recuperare le definizioni dei moduli tramite l’API Forms adattiva headless. Questo offre il pieno controllo sull’esperienza mobile e garantisce un supporto continuo con l’evolversi delle piattaforme mobili.

## Approccio consigliato {#recommended-approach}

Crea un’app mobile nativa (iOS o Android) che:

1. **Recupera la definizione del modulo headless**. Utilizza le [API Forms adattive headless](https://opensource.adobe.com/aem-forms-af-runtime/api/) per recuperare il modulo JSON on-demand (ad esempio, quando l&#39;utente apre un modulo o vi accede nell&#39;app). Puoi elencare i moduli disponibili e quindi recuperare la definizione del modulo per ID.

2. **Esegue il rendering del modulo nell&#39;app**. Utilizza il framework dell&#39;interfaccia utente preferito (ad esempio, React Native o visualizzazioni native) per eseguire il rendering del modulo dal JSON. Puoi utilizzare Forms Web SDK e i componenti React dei moduli adattivi headless esistenti in cui rientrano nello stack, oppure puoi creare un renderer personalizzato che utilizzi la stessa struttura JSON.

3. **Facoltativamente supporta la modalità offline**. Implementare l&#39;archiviazione locale e la sincronizzazione nell&#39;app. Ad esempio, memorizza nella cache le definizioni dei moduli quando è online, salva le bozze localmente e invia o sincronizza i dati quando il dispositivo è nuovamente online.

Questo approccio mantiene la gestibilità dell’app con il cambiamento di Android e iOS e utilizza la piattaforma Headless Adaptive Forms supportata per l’authoring, la convalida e l’invio di moduli.

## Guida introduttiva {#getting-started}

* [Panoramica dei moduli adattivi headless AEM](overview.md) - Funzionalità e concetti.
* [API per moduli adattivi headless](https://opensource.adobe.com/aem-forms-af-runtime/api/): elenca, recupera, convalida e invia moduli a livello di programmazione.
* [Architettura](architecture.md) - Funzionamento dei moduli adattivi headless e utilizzo delle app front-end.

Per un&#39;integrazione dettagliata, vedere [Creare e pubblicare un modulo headless](create-and-publish-a-headless-form.md) e il [portale per sviluppatori](https://experienceleague.adobe.com/landing/aem-headless-forms/developer.html?lang=it).
