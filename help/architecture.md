---
title: Architettura dei moduli adattivi headless
description: Scopri l’architettura di AEM Forms Headless adaptive Forms e come può aiutarti a creare rapidamente moduli per varie piattaforme. Questo articolo fornisce approfondimenti sul funzionamento di Headless adaptive Forms e su come possono essere integrati con diverse applicazioni per semplificare il processo di creazione dei moduli.
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: headless, modulo adattivo, architettura
hide: false
exl-id: ee7096d8-89e2-41e0-85e7-b26457df96fb
source-git-commit: 28792fe1690e68cd301a0de2ce8bff53fae1605f
workflow-type: tm+mt
source-wordcount: '904'
ht-degree: 0%

---


# Come funziona il modulo adattivo headless?

Un modulo adattivo headless è essenzialmente una struttura JSON (schema) costituita da campi modulo (casella di testo, scelte e molti altri campi) e da regole corrispondenti (logica condizionale) per aggiungere al modulo un comportamento interattivo. Puoi utilizzare le API REST nell’applicazione o nel sito web per richiedere la struttura JSON in hosting ed eseguire il rendering nativo della struttura JSON come modulo nell’app o nel sito web. Un singolo modulo adattivo headless può essere utilizzato per più pagine web e applicazioni senza apportare alcuna modifica specifica all’app o al sito web.

![Funzionamento del modulo adattivo headless](/help/assets/how-headless-adaprive-forms-work.png)

## Architettura {#architecture}

Un’architettura tipica di moduli adattivi headless si basa su un server Adobe Experience Manager Forms che ospita moduli adattivi headless. Le app front-end (web, mobile, JavaScript, chatbot e altro) eseguono il rendering dei moduli per ciascun canale.

L’architettura tipica di una distribuzione di moduli adattivi headless è simile alla seguente:

![Architettura](/help/assets/headless-af-architecture.png)

<!-- 

You can use the React renderer component shipped with Headless adaptive forms to render an Adaptive Form or build your own custom component to natively render a Headless Form in a website or an application or use any UI framework or programming language to build your own components to render your forms.

A typical Headless adaptive forms architecture constitutes an Adobe Experience Manager Server, JSON structure of forms, various frontend apps for channel-specific form renditions.

![Architecture](/help/assets/headless-af-architecture.png) -->

### Componente di un’implementazione di moduli adattivi headless

**Adobe Experience Manager Server**: oltre a fungere da host per i moduli adattivi headless, Adobe Experience Manager fornisce le seguenti funzionalità di back-end:

* API RESTful per elencare, recuperare, precompilare, convalidare, inviare e tenere traccia dello stato di invio dei moduli headless.
* Editor visivo per sviluppare facilmente un modulo adattivo headless.
* Forms Data Model per ricevere o inviare dati a origini dati diverse.
* Un motore per flussi di lavoro per automatizzare attività complesse.

**Moduli adattivi headless**: un modulo adattivo headless è rappresentato come file .json. La struttura JSON definisce i componenti, i vincoli e la struttura di un modulo.

**App front-end**: applicazioni front-end come, SPA (applicazioni a pagina singola), app mobili, app JavaScript, utilizzano moduli adattivi headless (rappresentazione modulo JSON) ed eseguono il rendering del modulo su un client. Puoi utilizzare il componente renderer React fornito con moduli adattivi headless per eseguire il rendering di un modulo adattivo o per creare un componente personalizzato per il rendering nativo dei moduli adattivi headless.

<!-- ### Understanding Headless adaptive forms definition -->



### Strumenti per sviluppatori

In un normale ciclo di sviluppo, puoi iniziare con la creazione e l’hosting di moduli adattivi headless sul server Adobe Experience Manager Forms. Nel secondo passaggio, puoi mappare i componenti dell’interfaccia utente o utilizzare una libreria pubblica di componenti dell’interfaccia utente, ad esempio l’interfaccia utente Materiale di Google o l’interfaccia utente Chakra, per assegnare uno stile ai moduli. Nell’ultimo passaggio, recuperi e visualizzi i moduli adattivi headless nell’applicazione (sito web, app mobile, app JavaScript, applicazioni chat o molte altre superfici).

I seguenti strumenti consentono di creare e integrare moduli adattivi headless nelle applicazioni:

**Forms Web SDK (Client-Side Runtime)**: Forms Web SDK è una libreria JavaScript lato client. Consente di applicare convalide lato client ai campi modulo, mantenere lo stato del modulo e fornisce hook per collegare il modulo al livello dell’interfaccia utente o al componente di cui è stato eseguito il rendering dei moduli adattivi. Consente ai clienti di convalidare i vincoli applicati a vari campi di un modulo e hook per collegare la struttura JSON del modulo al framework dell’interfaccia utente. Forms Web SDK include i seguenti componenti:

* **Processore regole business**: il processore regole business accetta la struttura JSON dei moduli come input, gestisce lo stato dei campi modulo, esegue regole e gestori eventi presenti nel JSON.
* **Binder React**: fornisce collegamenti sul controller per aggiungere lo stato ai componenti modulo. È utile anche nella precompilazione di un modulo.
* **Libreria componenti**: fornisce i componenti Spettro di React e utilizza gli hook nel modulo del Raccoglitore di React per aggiungere lo stato a tali componenti.

Oltre a fornire le API per convalidare i vincoli applicati ai vari campi di un modulo, Forms Web SDK fornisce hook per collegare i moduli adattivi headless al framework dell’interfaccia utente. Fornisce anche un renderer React per moduli adattivi headless per integrare un modulo adattivo headless nell’applicazione. Sono disponibili i seguenti componenti di Web SDK:

* **[@aemforms/af-react-components](https://www.npmjs.com/package/@aemforms/af-react-components)**
* **[@aemforms/af-react-renderer](https://www.npmjs.com/package/@aemforms/af-react-renderer)**
* **[@aemforms/af-core](https://www.npmjs.com/package/@aemforms/af-core)**

Tutti questi componenti sono inclusi in Archetipo AEM. Quando crei un progetto AEM Archetype 37 o successivo per moduli adattivi headless, nel progetto viene inclusa la versione più recente delle librerie elencate sopra.

* **Area di gioco codice**: [Area di gioco codice](https://experienceleague.adobe.com/landing/aem-headless-forms/developer/code.html?lang=it) è un ambiente interattivo progettato per gli sviluppatori per sperimentare, scoprire e testare le funzionalità di Forms adattivo headless.

**Applicazione avviata**: Adobe ha anche rilasciato un&#39;applicazione avviata per aiutarti a iniziare rapidamente con i moduli adattivi headless.

<!-- **View Library (UI Layer)**: A custom form application built in a front-end language. You can use react, Angular, Flutter, NPM, Vue.js, Ionic, BootStrap, or any other language to built front end. You can also use the Headless adaptive forms Super Component, provided out-of-the-box, inside a react application to render a Headless adaptive form. Headless adaptive forms super component makes use of OOTB react spectrum -based form components to render the Headless adaptive form. 

Core-Components: It enables use to render an Adaptive Form using JSON structure. It uses rule grammar to help create dynamic field interactions. The rule grammar is based on [JSON formula](http://github.com/adobe/json-formula/). You can develop your own renderer or embed the React based Adaptive Forms renderer, provided OOTB, in your front-end app to render the form. -->

**Storybook**: [Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/) fornisce una panoramica dei diversi componenti dei moduli adattivi headless. Inoltre, fornisce un elenco di tutti i componenti supportati, con le proprietà e i vincoli corrispondenti.

**Estensione codice Visual Studio**: [Estensione codice Visual Studio](visual-studio-code-extension-for-headless-adaptive-forms.md) per creare una struttura JSON valida. Fornisce il supporto IntelliSense e la convalida per la struttura JSON dei moduli insieme a funzioni comuni come l’aggiunta, l’eliminazione o la ridenominazione di componenti di una struttura JSON.

**API HTTP e JavaScript**: [API HTTP](https://opensource.adobe.com/aem-forms-af-runtime/api/) ti consentono di elencare, recuperare, convalidare, inviare e tenere traccia dello stato di invio dei moduli headless. <!-- URL is 404!! [JS APIs](https://opensource.adobe.com/aem-forms-af-runtime/jsdocs/) helps you use Headless adaptive forms with any JavaScript based UI framework. -->

**Formula JSON**: si tratta di un&#39;implementazione della grammatica dell&#39;espressione forms per eseguire query sulla struttura JSON e creare regole per i moduli adattivi headless. La grammatica è una combinazione di funzioni e operatori simili a fogli di calcolo e [JMESPath](https://jmespath.org/) un linguaggio di query JSON. È possibile utilizzare [playground](https://opensource.adobe.com/json-formula/dist/index.html) per esplorare la sintassi e le funzionalità della formula JSON.

**Specifiche di Forms adattivo versione 2.0**: la specifica di Forms adattivo versione 2.0 fornisce informazioni dettagliate su tutti i componenti, i vincoli e i metodi disponibili per definire i moduli adattivi headless. La specifica è disponibile in formato [PDF](/help/assets/headless-adaptive-forms-specification.pdf).

