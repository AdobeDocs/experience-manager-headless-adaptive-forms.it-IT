---
title: Utilizzare i componenti di reazione dell’interfaccia utente dei materiali di Google per eseguire il rendering di un modulo headless
description: Scopri come utilizzare i componenti Google Material-UI React per eseguire il rendering di un modulo headless. Questa guida completa illustra i passaggi necessari per creare componenti Forms adattivi headless personalizzati che consentono di mappare e utilizzare i componenti React dell’interfaccia utente dei materiali di Google per assegnare uno stile a un modulo adattivo headless.
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
hide: false
exl-id: 476509d5-f4c1-4d1c-b124-4c278f67b1ef
source-git-commit: 47ac7d03c8c4fa18ac3bdcef04352fdd1cad1b16
workflow-type: tm+mt
source-wordcount: '863'
ht-degree: 0%

---


# Utilizzare una libreria di react personalizzata per eseguire il rendering di un modulo headless

Puoi creare e implementare componenti personalizzati per personalizzare l’aspetto e la funzionalità (Comportamento) dei moduli adattivi headless in base ai requisiti e alle linee guida della tua organizzazione.

Questi componenti hanno due finalità principali: controllare l’aspetto o lo stile dei campi modulo e memorizzare i dati raccolti attraverso questi campi all’interno dell’istanza del modello di modulo. Se questo può sembrare confuso, non preoccuparti: esploreremo questi scopi in modo più dettagliato a breve. Per il momento, concentriamoci sui passaggi iniziali della creazione di componenti personalizzati, del rendering del modulo utilizzando questi componenti e dell’utilizzo di eventi per salvare e inviare dati a un endpoint REST.

In questo tutorial, vengono utilizzati i componenti dell’interfaccia utente di Google Material per dimostrare come eseguire il rendering di un modulo adattivo headless utilizzando i componenti React personalizzati. Tuttavia, non sei limitato a questa libreria e sei libero di utilizzare qualsiasi libreria di componenti React o di sviluppare componenti personalizzati.

Alla conclusione di questo articolo, il modulo _Contattaci_ creato in [Crea e pubblica un modulo headless utilizzando il kit di avvio](create-and-publish-a-headless-form.md) si trasforma nel seguente:

![](assets/headless-adaptive-form-with-google-material-ui-components.png)


I passaggi principali necessari per l’utilizzo dei componenti dell’interfaccia utente Materiale di Google per il rendering di un modulo sono i seguenti:

![](assets/headless-forms-graphics-source-main.svg)

## 1. Installare l’interfaccia utente dei materiali di Google

Per impostazione predefinita, il kit di avvio utilizza i componenti Spectrum](https://spectrum.adobe.com/) di [Adobe. Impostiamolo per utilizzare [l&#39;interfaccia utente dei materiali di Google](https://mui.com/):

1. Verificare che il kit di avvio non sia in esecuzione. Per arrestare il kit di avvio, apri il terminale, passa a **react-starter-kit-aem-headless-forms** e premi Ctrl-C (lo stesso avviene su Windows, Mac e Linux).

   Non tentare di chiudere il terminale. La chiusura del terminale non arresta il kit di avvio.

1. Esegui il comando seguente:

```shell
    
    npm install @mui/material @emotion/react @emotion/styled --force
    
```

Installa le librerie npm dell’interfaccia utente di Google Material e aggiunge le librerie alle dipendenze dei kit di avvio. È ora possibile utilizzare i componenti dell’interfaccia utente Materiale per eseguire il rendering dei componenti del modulo.


## 2. Creare componenti React personalizzati

Creiamo un componente personalizzato che sostituisce il componente predefinito [immissione testo](https://spectrum.adobe.com/page/text-field/) con il componente [Campo di testo interfaccia utente materiale Google](https://mui.com/material-ui/react-text-field/).

È necessario un componente separato per ogni tipo di componente ([fieldType](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-json-properties-fieldtype--text-input) o :type) utilizzato in una definizione di modulo headless. Ad esempio, nel modulo Contattaci creato nella sezione precedente, i campi Nome, E-mail e Telefono di tipo `text-input` ([fieldType: &quot;text-input&quot;](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/docs/adaptive-form-components-text-input-field--def)) e il campo del messaggio è di tipo `multiline-input` ([&quot;fieldType&quot;: &quot;multiline-input&quot;](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/docs/reference-json-properties-fieldtype--multiline-input)).


Creiamo un componente personalizzato per sovrapporre tutti i campi modulo che utilizzano la proprietà [fieldType: &quot;text-input&quot;](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/docs/adaptive-form-components-text-input-field--def) con il componente [Material UI Text Field](https://mui.com/material-ui/react-text-field/).


Per creare il componente personalizzato e mappare il componente personalizzato con la proprietà [fieldType](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/docs/adaptive-form-components-text-input-field--def):

1. Apri la directory **react-starter-kit-aem-headless-forms** in un editor di codice e passa a `\react-starter-kit-aem-headless-forms\src\components`.


1. Crea una copia della cartella **slider** o **richtext** e rinomina la cartella copiata in **materialtextfield**. Slider e richtext sono due esempi di componenti personalizzati disponibili nell’app iniziale. Puoi utilizzarli per creare componenti personalizzati.

   ![Componente personalizzato materialtextfield in VSCode](/help/assets/richtext-custom-component-in-vscode.png)

1. Apri il file `\react-starter-kit-aem-headless-forms\src\components\materialtextfield\index.tsx` e sostituisci il codice esistente con il codice seguente. Questo codice restituisce ed esegue il rendering di un componente [Google Material UI Text Field](https://mui.com/material-ui/react-text-field/).

```JavaScript
 
     import React from 'react';
     import {useRuleEngine} from '@aemforms/af-react-renderer';
     import {FieldJson, State} from '@aemforms/af-core';
     import { TextField } from '@mui/material';
     import Box from '@mui/material/Box';
     import { richTextString } from '@aemforms/af-react-components';
     import Typography from '@mui/material/Typography';


     const MaterialtextField = function (props: State<FieldJson>) {

         const [state, handlers] = useRuleEngine(props);

         return(

         <Box>
             <Typography component="legend">{state.visible ? richTextString(state?.label?.value): ""} </Typography>
             <TextField variant="filled"/>
         </Box>

         )
     }

     export default MaterialtextField;
```


La parte `state.visible` controlla se il componente è impostato per essere visibile. In caso affermativo, l&#39;etichetta del campo viene recuperata e visualizzata utilizzando `richTextString(state?.label?.value)`.

![](/help/assets/material-text-field.png)


Il componente personalizzato `materialtextfield` è pronto. Impostiamo questo componente personalizzato in modo da sostituire tutte le istanze di [fieldType: &quot;text-input&quot;](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/docs/adaptive-form-components-text-input-field--def) con il campo di testo dell&#39;interfaccia utente di Google Material.

## 3. Mappatura del componente personalizzato con campi modulo headless

Il processo di utilizzo di componenti libreria di terze parti per il rendering dei campi modulo è noto come mappatura. Mappa ogni ([fieldType](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-json-properties-fieldtype--text-input)) al componente corrispondente della libreria di terze parti.

Tutte le informazioni relative alla mappatura vengono aggiunte al file `mappings.ts`. L&#39;istruzione `...mappings` nel file `mappings.ts` fa riferimento alle mappature predefinite, che sovrappongono ([fieldType](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-json-properties-fieldtype--text-input) o :type) con i componenti [Adobe Spectrum](https://spectrum.adobe.com/page/text-field/).

Per aggiungere la mappatura per il componente `materialtextfield`, creato nell&#39;ultimo passaggio:

1. Aprire il file `mappings.ts`.

1. Aggiungere la seguente istruzione di importazione per includere il componente `materialtextfield` nel file `mappings.ts`:


   ```JavaScript
       import MaterialtextField from "../components/materialtextfield";
   ```

1. Aggiungere l&#39;istruzione seguente per associare `text-input` al componente materialtextfield.


   ```JavaScript
       "text-input": MaterialtextField
   ```

   Il codice finale del file è simile al seguente:

   ```JavaScript
         import { mappings } from "@aemforms/af-react-components";
         import MaterialtextField from "../components/materialtextfield";
   
   
         const customMappings: any = {
           ...mappings,
           "text-input": MaterialtextField
        };
        export default customMappings;
   ```

1. Salva ed esegui l’app. Viene eseguito il rendering dei primi tre campi del modulo utilizzando [Campo di testo interfaccia utente materiale Google](https://mui.com/material-ui/react-text-field/):

   ![](assets/material-text-field-form-rendetion.png)


   Allo stesso modo, puoi creare componenti personalizzati per i campi messaggio (&quot;fieldType&quot;: &quot;multi-line-input&quot;) e valutazione del servizio (&quot;fieldType&quot;: &quot;number-input&quot;). Puoi clonare il seguente archivio Git per i componenti personalizzati del messaggio e valutare i campi del servizio:

   [https://github.com/singhkh/react-starter-kit-aem-headless-forms](https://github.com/singhkh/react-starter-kit-aem-headless-forms)

## Passaggio successivo

Il rendering del modulo con i componenti personalizzati che utilizzano l’interfaccia utente Materiale di Google è stato eseguito correttamente. Hai provato a inviare il modulo facendo clic sul pulsante Invia (mappato con il componente corrispondente dell’interfaccia utente di Google Material)? In caso contrario, prova.

Il modulo invia i dati a un&#39;origine dati? No? Non preoccuparti. Questo perché il modulo non è configurato per comunicare con la libreria runtime.

Come configurare il modulo per comunicare con esso? Presto sarà disponibile un articolo che spiegherà tutto nel dettaglio. Continua a seguirci!
