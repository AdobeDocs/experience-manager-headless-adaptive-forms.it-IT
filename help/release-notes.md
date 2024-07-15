---
title: Panoramica dei moduli adattivi headless AEM
description: Panoramica dei moduli adattivi headless AEM.
hide: true
exl-id: cd7c7972-376c-489f-a684-f479d92c37e7
source-git-commit: 0127f8ddede38083f0932b0e8d7efdd0dd77c3a6
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 3%

---


# Note sulla versione

Benvenuti in Experience Manager Headless moduli adattivi versione precedente per l’adozione. Continua a leggere per risorse e istruzioni su come iniziare e sfruttare al meglio la versione.

Puoi utilizzare i moduli adattivi headless di Adobe Experience Manager per creare applicazioni Forms utilizzando framework dell’interfaccia utente front-end come React, Angular e altro ancora e utilizzare Adaptive Forms Web SDK per funzionalità come la gestione dello stato, la convalida e le integrazioni con vari altri punti di contatto.

La versione precedente di Adobe consente di accedere all&#39;utilizzo di moduli adattivi headless in un [ambiente di sviluppo locale](setup-development-environment.md). Puoi utilizzare l’ambiente di sviluppo locale per generare e testare moduli adattivi headless.

I moduli adattivi headless vengono costantemente migliorati. Per rimanere aggiornato sugli sviluppi più recenti, visita questa pagina regolarmente. Questa pagina fornisce informazioni sull’accesso in anteprima, sulle versioni più recenti, sulle nuove funzioni, sui miglioramenti, sulle correzioni di bug, sulle funzionalità obsolete, su istruzioni speciali e sui piani futuri di modifica.

<!-- 

## July 2022 (v0.22.1)

### New features

* Introduced the `validateFormData` API. It validates all the components against the rules and constraints an returns the list of errors. The validation takes place on the server.
* Introduced the `FormLoad` event.
* Introduced the `importData` and `exportData`.
* You can now dynamically add or remove items, that expect unqiue values, from a repeatable panel. You can use the `minItems` and `maxitems` constraint to set limit of item.
* You can now use constraint to set maximum file upload size, accepted file types, minimum files, and maximum files to upload.

### Improvements and bug fixes

* The service was executing some event handlers twice. The issue is fixed.
* Fixing Data Generation with different values of dataRef, name and type.

<!-- ### React Renderer component -->

## Artefatti disponibili a partire dalla prima versione dell’utente

Nel percorso per portare all’utente i moduli adattivi headless di Adobe Experience Manager, nella prima versione sono disponibili i seguenti artefatti:

### AEM FORMS AS A CLOUD SERVICE SDK

AEM Forms as a Cloud Service SDK per aiutarti a creare, archiviare e recuperare moduli adattivi headless. Consente inoltre di precompilare, convalidare le regole lato server e inviare servizi per moduli adattivi headless.

### Forms Web SDK

Forms Web SDK fornisce le API per convalidare i vincoli applicati ai vari campi di un modulo e gli hook per collegare la struttura JSON del modulo al framework dell’interfaccia utente. Fornisce anche React Renderer&#x200B; per moduli adattivi headless, per facilitare l’integrazione di un modulo adattivo headless nell’applicazione. Sono disponibili i seguenti componenti di Web SDK:

* **[@aemforms/af-react-components](https://www.npmjs.com/package/@aemforms/af-react-components)**
* **[@aemforms/af-react-renderer](https://www.npmjs.com/package/@aemforms/af-react-renderer)**
* **[@aemforms/af-core](https://www.npmjs.com/package/@aemforms/af-core)**

<!-- npm i --save @aemforms/af-react-components @aemforms/af-react-renderer @aemforms/af-core -->

#### Storybook

[Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/) fornisce una panoramica dei diversi componenti dei moduli adattivi headless. Inoltre, fornisce un elenco di tutti i componenti supportati, con le proprietà e i vincoli corrispondenti.

### Componente core Forms

<!-- Forms components are the structural elements that constitute the content of the form being authored. These components provide various form fields and ability to customize those fields. -->

I componenti core sono un set di componenti WCM (Web Content Management) standardizzati che consentono di velocizzare i tempi di sviluppo e ridurre i costi di manutenzione dei moduli. Il componente Contenitore Forms è un componente core. Consente di incorporare ed eseguire il rendering di una struttura JSON di moduli adattivi headless nell’editor Forms adattivo di Forms as a Cloud Service SDK.

### Specifiche di Adaptive Forms V2

La specifica dei moduli adattivi headless fornisce informazioni dettagliate su tutti i componenti, i vincoli e i metodi disponibili per definire i moduli adattivi headless. La specifica è disponibile in formato [PDF](/help/assets/Headless-Adaptive-Form-Specification.pdf).

### API HTTP e JS

[API HTTP](https://opensource.adobe.com/aem-forms-af-runtime/api/) ti consentono di elencare, recuperare, convalidare, inviare e tenere traccia dello stato di invio dei moduli headless. [API JS](https://opensource.adobe.com/aem-forms-af-runtime/jsdocs/) consente di utilizzare moduli adattivi headless con qualsiasi framework di interfaccia utente basato su JavaScript.

### Estensione codice di Visual Studio

[Estensione del codice Visual Studio](visual-studio-code-extension-for-headless-adaptive-forms.md) per creare una struttura JSON valida. Fornisce il supporto IntelliSense e la convalida per la struttura JSON dei moduli insieme a funzioni comuni come l’aggiunta, l’eliminazione o la ridenominazione di componenti di una struttura JSON.

<!-- ## What's next

The following features would be available in upcoming releases:

* HTTP APIs to invoke a business logic.
* Server-side capabilities (Prefill, server-side validation, generating Document of Record (DoR), Submitting to a Form Data Model or using Form Data Models for creating rules, and more).
* Continuous improvements to specifications and Headless adaptive form runtime.
* Use  Adaptive Forms editor for easier management and authoring Headless adaptive forms.
-->