---
title: Domande frequenti su Headless Adaptive Forms
description: Domande frequenti
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: modulo adattivo headless, domande frequenti
index: true
exl-id: 5bfc307d-96a3-4007-b65f-32176ecdb710
source-git-commit: 86129488bec7faed87600a237ac034ca1b601187
workflow-type: tm+mt
source-wordcount: '837'
ht-degree: 0%

---

# Domande frequenti (FAQ) {#headless-adaptive-forms-faq}

## Devo conoscere React.js per utilizzare moduli adattivi headless?

Puoi utilizzare qualsiasi framework, libreria o lingua per eseguire il rendering di moduli adattivi headless e utilizzare le API REST di Adobe per convalidare e inviare i moduli. La libreria AF-core, fornita all’utente preconfigurata, è indipendente dal framework. Le librerie React-Render e React-componet, anch’esse pronte all’uso, sono utili per la tua comodità. Puoi creare componenti personalizzati senza essere limitato a quelli forniti.


<!-- 
## Did Adobe release a new AEM Archetype for Headless adaptive forms?

You can use Archetype 37 with flag `includeFormsheadless` or later flag to create an AEM project with Headless adaptive forms functionality. 

-->

## È necessario disporre di una sandbox Forms as a Cloud Service per utilizzare moduli adattivi headless?

Puoi utilizzare l’app iniziale per iniziare a sviluppare e formattare i moduli adattivi headless. Devi disporre di Forms as a Cloud Service per l’hosting e la distribuzione di moduli adattivi headless insieme alle funzionalità dei moduli back-end.

<!-- 
## Do I need an archetype project to develop Headless adaptive forms?

You can use the starter app to start developing and styling your Headless adaptive forms. Later on, you can use the 
archetype project to deploy the finished Headless adaptive forms and corresponding custom code, created using starter app, to Forms as a Cloud Service environment. The Forms as a Cloud Service environment helps you test and productionize the forms. 
-->

## Dove posso trovare un’anteprima di un modulo adattivo headless? {#storybook-example}

Puoi utilizzare l’app iniziale per eseguire il rendering e l’anteprima di un modulo adattivo headless personalizzato. Puoi anche modificare un esempio di [storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-examples--introduction) per visualizzare in anteprima un modulo adattivo headless.

![](/help/assets/storybook-example.png)

## È possibile utilizzare moduli adattivi headless con framework personalizzati?

I moduli adattivi headless si basano sulla [specifica standard](/help/assets/headless-adaptive-forms-specification.pdf). Puoi estendere la specifica per utilizzarla per creare componenti personalizzati. Ad esempio, componenti per l’interfaccia utente di Chakra, Vue.js e altro ancora.

## I moduli adattivi headless supportano i campi a cascata?

Nei campi a catena, il contenuto del secondo campo dipende dal contenuto scelto nel primo campo. Il [Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/adaptive-form-dynamic-behaviour--options&args=formJson.items[0].fieldType:drop-down;formJson.items[0].minimum:!undefined;formJson.items[0].maximum:!undefined;formJson.items[0].label.value:Choose+number+of+options;formJson.items[0].enum[0]:1;formJson.items[0].enum[1]:2;formJson.items[0].enum[2]:3;formJson.items[1].fieldType:drop-down) fornisce un esempio di campi a catena.

## I moduli adattivi headless consentono la precompilazione dei moduli con dati personalizzati?

I moduli adattivi headless consentono la precompilazione dei moduli con dati personalizzati. Il [Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-examples--prefill-form-with-personalised-data) fornisce un esempio di come precompilare un modulo adattivo headless.

<!--
## Can I use existing Adaptive Forms editor to create a Headless adaptive form?

At this moment, you use the Adaptive Form Editor to specify the JSON structure and set submit action for the forms. Support for drag-and-drop components, applying rules using editor, and more editor-related options would be available later in the beta phase. Keep a watch on release notes.  
-->

## Posso utilizzare moduli adattivi headless con Angular SPA?

Puoi utilizzare il Web SDK per integrare i moduli adattivi headless con l’applicazione a pagina singola di Angular. È indipendente da qualsiasi struttura. È possibile utilizzare React SDK come riferimento.

<!--
## Should the `-r prerelease` switch be used every time to start the AEM SDK instance or only for the first time?

During the limited release program, use the `-r prerelease` switch every time you start the AEM SDK instance. 

## What is AEM Forms add-on (.far file) and how to install it?

Adobe Experience Manager Forms as a Cloud Service feature archive provides tools to create Headless adaptive forms on the local development environment. To install the feature archive, see [Setup development environment](setup-development-environment.md).

## Where do one get the license.properties file from?

You do not require a license.properties file to run AEM Cloud Service SDK. 
-->

## Esiste un plug-in per semplificare lo sviluppo di Headless AF?

Sì: un’estensione codice di Visual Studio consente di creare manualmente moduli adattivi headless in JSON.

## Qual è l’approccio consigliato per i moduli mobili o offline? {#mobile-offline-forms}

Crea una tua app nativa e recupera le definizioni dei moduli tramite l’API Forms adattivo headless. Facoltativamente, puoi implementare il supporto offline (ad esempio, archiviazione locale e sincronizzazione). Consulta [Best practice per i moduli mobili](mobile-forms-best-practices.md) per l&#39;approccio consigliato e i collegamenti alle API.

## Come si utilizzano GraphQL o le API headless con AEM Forms?

AEM Headless Adaptive Forms utilizza **API HTTP/REST**, non GraphQL. L’app richiama queste API per elencare i moduli, recuperare una definizione di modulo (JSON), convalidare, inviare e tenere traccia dello stato di invio. Utilizza le [API HTTP per moduli adattivi headless](https://opensource.adobe.com/aem-forms-af-runtime/api/) per il riferimento completo. Per informazioni sul recupero e il rendering dei moduli, consulta [Architettura](architecture.md) e [Informazioni sui moduli headless](understanding-headless-forms.md).

## Come posso implementare e assegnare uno stile ai moduli headless utilizzando i componenti React in Adobe AEM Forms?

Puoi implementare e assegnare uno stile ai moduli headless utilizzando componenti e CSS React personalizzati (o una libreria dell’interfaccia utente come l’interfaccia utente Materiale). La logica del modulo (stato, convalida e regole) proviene da Forms Web SDK e dal modulo JSON; l’app fornisce l’interfaccia utente che ne esegue il rendering.

* Per assegnare uno stile a un modulo headless con una libreria dell&#39;interfaccia utente React, vedi [Utilizzare una libreria di react personalizzata per eseguire il rendering di un modulo headless](use-google-material-ui-react-components-to-render-a-headless-form.md).
* Per generare e mappare i componenti React personalizzati ai campi modulo, vedi [Utilizzare componenti personalizzati per eseguire il rendering di un modulo headless](developing-for-headless-forms-using-your-own-components.md).

Per concetti quali l&#39;utilizzo di moduli headless, la gestione dello stato e la convalida, vedi [Informazioni sui moduli headless](understanding-headless-forms.md).

## Come posso implementare e personalizzare AEM Forms con CSS, temi, editor di regole e moduli headless personalizzati?

**Moduli headless:** Lo stile e il look-and-feel sono completamente sotto il tuo controllo. Puoi utilizzare i tuoi componenti React (o altri) e il tuo CSS; non sono presenti temi incorporati. Consulta [Utilizzare una libreria di react personalizzata per eseguire il rendering di un modulo headless](use-google-material-ui-react-components-to-render-a-headless-form.md) e [Utilizzare componenti personalizzati per eseguire il rendering di un modulo headless](developing-for-headless-forms-using-your-own-components.md) per implementare e formattare i moduli headless.

**AEM Forms classico (temi, editor di regole, editor visivo):** CSS personalizzato, editor di temi e editor di regole si applicano all&#39;esperienza di authoring di Forms adattivo classico (non headless). Per questi argomenti, consulta la [documentazione di AEM Forms](https://experienceleague.adobe.com/docs/experience-manager-forms.html) su Experience League.

## Un modulo adattivo headless può connettersi a qualsiasi sistema CRM per leggere o scrivere dati?

Puoi utilizzare Microsoft Dynamics e Salesforce per inviare o precompilare un modulo adattivo headless. Oltre ai CRM, i moduli adattivi headless supportano l’invio o la precompilazione tramite endpoint REST, e-mail e azioni di invio personalizzate.
