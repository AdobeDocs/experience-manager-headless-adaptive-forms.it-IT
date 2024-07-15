---
title: Domande frequenti
description: Domande frequenti
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: modulo adattivo headless, domande frequenti
hide: false
exl-id: 5bfc307d-96a3-4007-b65f-32176ecdb710
source-git-commit: 47ac7d03c8c4fa18ac3bdcef04352fdd1cad1b16
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 1%

---

# Domande frequenti {#headless-adaptive-forms-faq}

## Devo conoscere React.js per utilizzare moduli adattivi headless?

Puoi utilizzare qualsiasi framework, libreria o lingua per eseguire il rendering di moduli adattivi headless e utilizzare le nostre API REST per convalidare e inviare i moduli. La libreria AF-core, fornita OOTB, è indipendente dal framework. Le librerie React-Render e React-component, fornite OOTB, sono utili per la tua comodità. Puoi sviluppare componenti personalizzati e utilizzarli senza limitazioni.

<!-- 
## Did Adobe release a new AEM Archetype for Headless adaptive forms?

You can use Archetype 37 with flag `includeFormsheadless` or later flag to create an AEM project with Headless adaptive forms functionality. 

-->

## È necessario Forms as a Cloud Service Sandbox per utilizzare moduli adattivi headless?

Puoi utilizzare l’app iniziale per iniziare a sviluppare e formattare i moduli adattivi headless. È necessario che Forms as a Cloud Service ospiti e distribuisca moduli adattivi headless insieme alle funzionalità dei moduli back-end.

<!-- ## Do I need an archetype project to develop Headless adaptive forms?

You can use the starter app to start developing and styling your Headless adaptive forms. Later on, you can use the 
archetype project to deploy the finished Headless adaptive forms and corresponding custom code, created using starter app, to Forms as a Cloud Service environment. The Forms as a Cloud Service environment helps you test and productionize the forms. -->

## Dove posso trovare un’anteprima di un modulo adattivo headless? {#storybook-example}

Puoi utilizzare l’app iniziale per eseguire il rendering e l’anteprima di un modulo adattivo headless personalizzato. Puoi anche modificare un esempio di [storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-examples--introduction) per visualizzare in anteprima un modulo adattivo headless.

![](/help/assets/storybook-example.png)

## È possibile utilizzare moduli adattivi headless con framework personalizzati?

I moduli adattivi headless si basano sulla [specifica standard](/help/assets/Headless-Adaptive-Form-Specification.pdf). Puoi estendere la specifica per utilizzarla per creare componenti personalizzati. Ad esempio, componenti per l’interfaccia utente di Chakra, Vue.js e altro ancora.

## I moduli adattivi headless supportano i campi a cascata?

Nei campi a catena, il contenuto del secondo campo dipende dal contenuto scelto nel primo campo. Il [Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/adaptive-form-dynamic-behaviour--options&amp;args=formJson.items[0].fieldType:drop-down;formJson.items[0].minimum:!undefined;formJson.items[0].maximum:!undefined;formJson.items[0].label.value:Choose+number+of+options;formJson.items[0].enum[0]:1;formJson.items[0].enum[1]:2;formJson.items[0].enum[2]:3;formJson.items[1].fieldType:drop-down) fornisce un esempio di campi a catena.

## I moduli adattivi headless consentono la precompilazione dei moduli con dati personalizzati?

I moduli adattivi headless consentono la precompilazione dei moduli con dati personalizzati. Il [Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-examples--prefill-form-with-personalised-data) fornisce un esempio di come precompilare un modulo adattivo headless.

<!-- >
## Can I use existing Adaptive Forms editor to create a Headless adaptive form?

At this moment, you use the Adaptive Form Editor to specify the JSON structure and set submit action for the forms. Support for drag-and-drop components, applying rules using editor, and more editor-related options would be available later in the beta phase. Keep a watch on release notes.  -->

## Posso utilizzare moduli adattivi headless con Angular SPA?

Puoi utilizzare l’SDK per web per integrare i moduli adattivi headless con Angular SPA. È indipendente da qualsiasi struttura. Puoi utilizzare l’SDK di React come riferimento.

<!-- ## Should the `-r prerelease` switch be used every time to start the AEM SDK instance or only for the first time?

During the limited release program, use the `-r prerelease` switch every time you start the AEM SDK instance. 

## What is AEM Forms add-on (.far file) and how to install it?

Adobe Experience Manager Forms as a Cloud Service feature archive provides tools to create Headless adaptive forms on the local development environment. To install the feature archive, see [Setup development environment](setup-development-environment.md).

<!-- 
## Where do one get the license.properties file from?

You do not require a license.properties file to run AEM Cloud Service SDK. 

-->

## Esiste un plug-in per semplificare lo sviluppo di Headless AF?

Sì, è disponibile un&#39;estensione per Microsoft Visual Studio Code. Fornisce un modo pratico per creare manualmente i moduli adattivi JSON headless.

## Un modulo adattivo headless può connettersi a qualsiasi sistema CRM per leggere o scrivere dati?

Puoi utilizzare Microsoft Dynamics e Salesforce per inviare o precompilare un modulo adattivo headless. Oltre ai CRM, i moduli adattivi headless supportano l’invio o la precompilazione tramite endpoint REST, e-mail e azioni di invio personalizzate.
