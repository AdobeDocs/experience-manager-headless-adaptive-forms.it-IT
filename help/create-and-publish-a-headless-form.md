---
title: Creare e pubblicare un modulo headless con Adobe Experience Manager Adaptive Forms | Guida dettagliata
description: Scopri come creare e pubblicare un modulo headless utilizzando i moduli adattivi di Adobe Experience Manager in questa guida dettagliata. Scopri i vantaggi di passare alla modalità headless e semplificare il processo di creazione dei moduli. Inizia a creare moduli dinamici e reattivi che funzionano perfettamente tra i dispositivi con Adobe Experience Manager Headless Adaptive Forms.
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
hide: false
exl-id: cd7c7972-376c-489f-a684-f479d92c37e7
source-git-commit: 28792fe1690e68cd301a0de2ce8bff53fae1605f
workflow-type: tm+mt
source-wordcount: '990'
ht-degree: 0%

---



# Creare e visualizzare in anteprima un modulo headless tramite un’app React {#introduction}

<!-- Missing image ALT image tags -->

Il kit di avvio ti aiuta a iniziare rapidamente a utilizzare un’app React. Puoi sviluppare e utilizzare moduli adattivi headless in un Angular, in Vanilla JS e in altri ambienti di sviluppo di tua scelta.

Iniziare con moduli adattivi headless è molto semplice e veloce. Clona il progetto React pronto, installa le dipendenze ed esegui il progetto. Hai un modulo adattivo headless integrato in un’app React in esecuzione. Puoi utilizzare il progetto React di esempio per generare e testare moduli adattivi headless prima di distribuirli in un ambiente di produzione.

Iniziamo:

>[!NOTE]
>
>
> Questa guida introduttiva utilizza un’app React. Puoi utilizzare liberamente la tecnologia o il linguaggio di programmazione di tua scelta per utilizzare i moduli adattivi headless.

## Prima di iniziare {#pre-requisites}

Per creare ed eseguire un&#39;app React, è necessario che nel computer sia installato quanto segue:

* Installa la [versione più recente di Git](https://git-scm.com/downloads). Se sei un nuovo utente di Git, vedi [Installazione di Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).

* Installa [Node.js 16.13.0 o versione successiva](https://nodejs.org/it/download/). <!-- URL is 404!! If you are new to Node.js, see [How to install Node.js](https://nodejs.dev/en/learn/how-to-install-nodejs). -->

## Introduzione

Una volta soddisfatti i requisiti, eseguire i passaggi seguenti per iniziare:

1. [Configurare il kit di avvio per moduli adattivi headless](#setup)

1. [Anteprima del modulo adattivo headless incluso nel kit di avvio](#preview)

1. [Crea ed esegui il rendering del tuo modulo adattivo headless](#custom)



## &#x200B;1. Configurare il kit di avvio per moduli adattivi headless {#install}

Il kit di avvio è un’app React con un modulo adattivo headless di esempio e le librerie corrispondenti. Utilizza il kit per sviluppare e testare i moduli headless adattivi e i corrispondenti componenti React. Esegui i seguenti comandi per configurare il kit di avvio per moduli adattivi headless:

1. Apri il prompt dei comandi ed esegui il comando seguente:

   ```shell
   git clone https://github.com/adobe/react-starter-kit-aem-headless-forms
   ```

   Il comando crea una directory denominata **react-starter-kit-aem-headless-forms** nella posizione corrente e clona l&#39;app iniziale Headless Adaptive Forms React. Oltre alle configurazioni e all’elenco delle dipendenze necessarie per il rendering del modulo, la directory include i seguenti contenuti importanti:

   * **Modulo di esempio**: il kit di avvio include un modulo di richiesta di prestito di esempio. Per visualizzare il modulo (definizione modulo) incluso nell&#39;app, aprire il file `/react-starter-kit-aem-headless-forms/form-definations/form-model.json`.
   * **Componenti React di esempio**: il kit di avvio include componenti react di esempio per Testo formattato e Dispositivo di scorrimento. Questa guida ti aiuta a creare componenti personalizzati utilizzando questi componenti Testo formattato e Cursore.
   * **Mappings.ts**: il file mappings.ts consente di mappare i componenti personalizzati con i campi modulo. Ad esempio, mappa un campo stepper numerico con un componente di valutazione.
   * **Configurazioni dell&#39;ambiente**: le configurazioni dell&#39;ambiente consentono di scegliere se eseguire il rendering di un modulo incluso nel kit di avvio o recuperare un modulo da un server AEM Forms.

   ![](/help/assets/getting-started-starter-kit-content.png)

   >[!NOTE]
   >
   > 
   > Esempi nei documenti sono basati su VSCode. Puoi utilizzare qualsiasi editor di codice di testo normale.


1. Passa alla directory **react-starter-kit-aem-headless-forms** ed esegui il seguente comando per installare le dipendenze:

   ```shell
   npm install
   ```

   Il comando scarica ogni pacchetto e libreria necessari per generare ed eseguire l’app, incluse le librerie di moduli adattivi headless (@aemforms/af-react-renderer, @aemforms/af-react-components, @adobe/react-spectrum). Quindi esegue le convalide e salva i dati in modo permanente per ogni istanza del modulo.


   ![](/help/assets/install-react-app-starter-kit.png)


## &#x200B;2. Anteprima del modulo adattivo headless {#preview}

Dopo aver configurato il kit di avvio, puoi visualizzare in anteprima il modulo adattivo headless di esempio e sostituirlo con un modulo personalizzato. Puoi anche configurare il kit di avvio per recuperare un modulo da un server AEM Forms. Per visualizzare l&#39;anteprima del modulo

1. Rinominare il file `env_template` in `.env`. Inoltre, l&#39;opzione USE_LOCAL_JSON è impostata su true.

   ![](/help/assets/rename-env-file.png)

   <!-- The options in the .env file help you configure source of the forms definantion (.JSON):
    *  To source forms definantion (.JSON) from an AEM Server, set USE_LOCAL_JSON option to false, use the AEM_URL option to specify URL  of your AEM Server, and set the AEM_FORM_PATH option to path of your adaptive form.
    *  To source forms definantion (.JSON) form-model.json file included in the starter-kit, set USE_LOCAL_JSON option to false. -->

1. Utilizza il seguente comando per eseguire l’app:

   ```shell
     npm start
   ```


   Questo comando avvia un server di sviluppo locale e apre il modulo adattivo headless di esempio, incluso nell’app iniziale, nel browser Web predefinito.

   ![Modulo Headless Di Esempio](assets/sample-headless-adaptive-form.png)

   Tutto pronto! Ora puoi iniziare a sviluppare un modulo adattivo headless personalizzato.

   <!--  As you know, in a headless form the form data and logic are separate from the presentation layer and can be used by any client that can make HTTP requests, such as a mobile app, a static site, or a different web application. The form is often managed and stored on a server, which serves as the backend for the form. The client sends requests to the server to retrieve the form, submit data, and receive updated form data. This allows for greater flexibility and integration with different technologies. You can store and retrive a Headless Adaptive form on an AEM Server  -->

## &#x200B;3. Crea ed esegui il rendering del tuo modulo adattivo headless{#custom}

Un modulo adattivo headless rappresenta il modulo e i relativi componenti, come campi e pulsanti, in formato JSON (JavaScript Object Notation). Il vantaggio di utilizzare il formato JSON è che può essere facilmente analizzato e utilizzato da vari linguaggi di programmazione, rendendolo un modo pratico per scambiare dati modulo tra i sistemi. Per visualizzare il modulo adattivo headless di esempio incluso nell&#39;app, apri il file `/react-starter-kit-aem-headless-forms/form-definations/form-model.json`.

Creiamo un modulo `Contact Us` con quattro campi: &quot;Nome&quot;, &quot;E-mail&quot;, &quot;Numero di contatto&quot; e &quot;Messaggio&quot;. I campi sono definiti come oggetti (elementi) all’interno del JSON e ogni oggetto (elemento) ha proprietà come tipo, etichetta, nome e obbligatorio. Il modulo include anche un pulsante di tipo &quot;invia&quot;. Ecco il JSON per il modulo.


```JSON
{
  "afModelDefinition": {
    "adaptiveform": "0.10.0",
    "items": [
      {
        "fieldType": "text-input",
        "label": {
          "value": "Name"
        },
        "name": "name"
      },
      {
        "fieldType": "text-input",
        "format": "email",
        "label": {
          "value": "Email"
        },
        "name": "email"
      },
      {
        "fieldType": "text-input",
        "format": "phone",
        "pattern": "[0-9]{10}",
        "label": {
          "value": "Contact Number"
        },
        "name": "Phone"
      },
      {
        "fieldType": "multiline-input",
        "label": {
          "value":"Message"
        },
        "name": "message"
      },
      {
        "fieldType": "button",
        "label":{
          "value": "Submit"
        },
        "name":"submit",
        "events":{
          "click": "submitForm()"
        }
      }
    ],
    "action": "https://eozrmb1rwsmofct.m.pipedream.net",
    "description": "Contact Us",
    "title": "Contact Us",
    "metadata": {
      "grammar": "json-formula-1.0.0",
      "version": "1.0.0"
    }
  }
}
```

>[!NOTE]
>
> * L&#39;attributo &quot;afModelDefinition&quot; è necessario solo per le applicazioni React e non fa parte della definizione del modulo.
> * Puoi creare a mano il modulo JSON o utilizzare l&#39;[editor di moduli adattivi di AEM (editor di WYSIWYG per moduli adattivi)](create-a-headless-adaptive-form.md) per creare e distribuire il modulo JSON. In un ambiente di produzione, si utilizza AEM Forms per distribuire il modulo JSON, per saperne di più in seguito.
> * L’esercitazione utilizza https://pipedream.com/ per verificare l’invio dei moduli. Per ricevere i dati da un modulo adattivo headless utilizzi endpoint personali o di terze parti approvati dall’organizzazione.


Per eseguire il rendering del modulo, sostituisci il modulo JSON `/react-starter-kit-aem-headless-forms/form-definations/form-model.json` headless adattivo di esempio con il JSON indicato sopra, salva il file e attendi che lo starter-kit compili e aggiorni il modulo.

![Sostituisci il modulo adattivo headless JSON `/react-starter-kit-aem-headless-forms/form-definations/form-model.json` di esempio con il modulo adattivo headless JSON](assets/render-custom-headless-adaptive-form.png) personalizzato

<!-- Your form is ready. Let's add some validations and make "Name", "Email", and "Message" fields mandatory. -->

Il rendering del modulo adattivo headless è stato eseguito correttamente.


## Bonus

Imposta il titolo della pagina Web che ospita il modulo su `Contact Us | WKND Adventures and Travel`. Per modificare il titolo, aprire il file _react-starter-kit-aem-headless-forms/public/index.html_ per la modifica e impostare il titolo.

![](assets/contact-us-headless-adaptive-forms-updated-title.png)


## Passaggio successivo

Per impostazione predefinita, il kit di avvio utilizza i componenti Spectrum[ di ](https://spectrum.adobe.com/)Adobe per eseguire il rendering del modulo. Puoi creare e utilizzare componenti personalizzati o di terze parti. Ad esempio, utilizzando l’interfaccia utente Materiale di Google o l’interfaccia utente Chakra.

[utilizziamo l&#39;interfaccia utente di Google Material](use-google-material-ui-react-components-to-render-a-headless-form.md) per eseguire il rendering del modulo `Contact Us`.




