---
title: Creare moduli efficaci utilizzando i componenti core e headless
seo-title: Build Engaging Forms Using Core Components and Headless
description: Creare moduli efficaci utilizzando i componenti core e headless
seo-description: Build Engaging Forms Using Core Components and Headless
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
topic-tags: develop
hide: true
exl-id: 07a71aac-de38-4839-b8d6-b47c3f575eb3
source-git-commit: 999c3d092d03d7a82363bc94ce79ceb33bf0df7e
workflow-type: tm+mt
source-wordcount: '2130'
ht-degree: 58%

---

# Costruire Forms coinvolgenti utilizzando componenti core e headless Forms adattivo su AEM 6.5 Forms {#build-engaging-forms-using-core-components-and-headless}

## Panoramica del workshop {#lab-overview}

In questo workshop pratico imparerai:

Come utilizzare AEM Forms per creare facilmente Forms adattivo utilizzando i Componenti core più recenti che sono coerenti con AEM Sites, abilitare esperienze di acquisizione dati omnicanale distribuendo Forms adattivo come moduli headless per web, dispositivi mobili e chat. Inoltre, puoi imparare le best practice relative allo stile, alle personalizzazioni e allo sviluppo front-end.

## Elementi principali da ricordare {#key-takeaways}

* **Agilità dell’azienda**: in qualità di utente aziendale, posso creare facilmente un’esperienza con i moduli per più canali.

* **Più controllo per gli sviluppatori front-end**: in qualità di sviluppatore front-end, posso controllare l’esperienza dell’utente finale utilizzando moduli headless.

* **Velocità di sviluppo**: in qualità di sviluppatore, posso personalizzare i componenti Sites e Forms in modo facile e coerente.

## Prima di iniziare {#pre-requisites}

Per usare queste mani sul laboratorio:

* Installa la [versione più recente di Git](https://git-scm.com/downloads). Se sei un nuovo utente di Git, vedi [Installazione di Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).

* Installa [Node.js 16.13.0 o versione successiva](https://nodejs.org/it/download/). Se hai poca esperienza con Node.js, consulta [Come installare Node.js](https://nodejs.dev/en/learn/how-to-install-nodejs).

* [Abilita Forms adattivo headless](enable-headless-adaptive-forms-and-core-components.md) nell&#39;ambiente Forms AEM 6.5.

* Installa [Microsoft Visual Studio Code](https://code.visualstudio.com/download) o qualsiasi editor di testo normale. Esempi in un documento utilizzano Microsoft Visual Studio Code.

## Lezione 1 {#lesson-1}

### Obiettivo {#lesson-1-objectives}

Acquisisci familiarità con l’ambiente Forms AEM 6.5.

### Contesto della lezione {#lesson-1-context}

In questa lezione imparerai a conoscere il Forms AEM 6.5 navigando nell’interfaccia utente di.

### Esercizio {#lesson-1-excercise}

1. Apri il browser e immetti l’URL dell’ambiente di authoring. Ad esempio:
   [https://localhost:4502](https://localhost:4502).

1. Dopo aver effettuato l’accesso, passa all’interfaccia utente di AEM Forms. Fai clic su **Moduli**.

   ![](/help/assets/screenshot2028113829.png){width="50%" align="left"}

1. Fai clic su **Moduli e documenti**. Ignora eventuali messaggi a comparsa relativi a preferenze o informazioni.

   ![](/help/assets/screenshot2028113929.png){width="50%" align="left"}

   Vengono visualizzati tutti i moduli disponibili.

   ![](/help/assets/screenshot2028114029.png){width="50%" align="left"}

## Lezione 2

### Obiettivo

Crea un modulo adattivo utilizzando i Componenti core più recenti, configura e invia il modulo.

### Contesto della lezione

In questa lezione, in qualità di utente aziendale, crei un modulo adattivo per più canali come web, mobile e chat utilizzando l’editor di Forms adattivo con componenti core predefiniti standardizzati per l’acquisizione dei dati.

### Esercizio

1. Crea un endpoint di invio per il modulo:

   1. Apri <https://requestbin.com/> in una nuova scheda del browser.
      ![](/help/assets/screenshot2028114329.png){width="50%" align="left"}

   1. Fai clic su **Crea un bin pubblico** e copia l’URL dell’endpoint.
      ![](/help/assets/screenshot202023-03-0120at206.10.0020pm.png){width="50%" align="left"}

   Questo particolare endpoint funge da esempio per l’invio e la visualizzazione dei dati. Nella produzione effettiva, puoi utilizzare il tuo endpoint o le tue origini dati per memorizzare i dati acquisiti.

1. Creare un modulo adattivo:

   1. Nella scheda del browser utilizzata nella lezione 1, passa all&#39;interfaccia Web di AEM Forms e passa a **Forms** > **Forms e documenti**.

   1. Fai clic su **Crea** e seleziona Modulo adattivo.
      ![](/help/assets/creating-adaptive-form-6-5.png){width="50%" align="left"}

   1. Seleziona il modello **Vuoto con Componenti core** dalla schermata di selezione del modello come mostrato di seguito e fai clic su **Avanti**.
      ![](/help/assets/creating-adaptive-form-6-5-select-blank-template.png){width="50%" align="left"}

   1. Specifica `Contact us` come **Titolo** del modulo. Assicurarsi che il **Nome** del modulo sia `contact-us`.
      ![](/help/assets/creating-adaptive-form-65-specify-title.png){width="50%" align="left"}

   1. Fai clic su **Crea**. Viene visualizzata una finestra di dialogo.

   1. Nella finestra di dialogo, fai clic su **Modifica**. Il modulo viene aperto nell’editor di moduli adattivi. Ignorare eventuali finestre a comparsa o finestre di dialogo per informazioni o preferenze.

   1. Apri il browser Componenti e trascina il componente Pannello al centro dello schermo.

      ![](/help/assets/lab65-add-panel.png){width="50%" align="left"}

   1. Trascina i componenti dal browser Componenti per creare un modulo simile al seguente:

      ![](/help/assets/contact-us-headless-adaptive-form.png){width="50%" align="left"}


   1. Apri il Browser contenuti, fai clic sull&#39;icona delle proprietà del Contenitore della Guida e apri la scheda **Invio**. Seleziona l&#39;azione di invio **Invia all&#39;endpoint REST**, seleziona l&#39;opzione **Abilita richiesta POST** e specifica l&#39;endpoint REST creato nella lezione 2 nella casella di testo **URL per richiesta POST**, quindi fai clic sull&#39;icona **Fine**.

      ![](/help/assets/configure-submit-action.png){width="50%" align="left"}

1. Publish e modulo adattivo:

   1. Apri l&#39;interfaccia utente AEM, passa a **Forms** > **Forms e documenti**. Selezionare il modulo creato nel passaggio precedente e fare clic su **Publish**.

   1. Nella finestra di dialogo Publish Assets, fai clic su **Publish**. Viene visualizzato il messaggio di operazione riuscita.

## Lezione 3

### Obiettivo

Aggiornare gli stili utilizzando le best practice di sviluppo front-end.

### Contesto della lezione

In questa lezione, in qualità di sviluppatore front-end, imparerai come aggiornare facilmente lo stile per il modulo adattivo creato in precedenza.

### Esercizio

Configurazione dell’archivio locale del tema:

1. Apri il prompt o la shell dei comandi con i diritti di amministratore:

   ![](/help/assets/screenshot2028115829.png){width="50%" align="left"}

1. Al prompt dei comandi utilizzare il comando seguente per passare alla cartella `c:\git`.

   ```Shell
   cd git
   ```

   Se la cartella non esiste, utilizzare il comando `md git` per crearla.

1. Per clonare il codice di front-end del tema, utilizza il comando seguente:

   ```Shell
   git clone -b WKND https://github.com/adobe/aem-forms-theme-canvas
   ```

1. Per passare alla directory **aem-forms-theme-canvas** e aprire Visual Studio Code, utilizza il seguente comando nell’ordine elencato.

   ```Shell
   cd aem-forms-theme-canvas
   code .
   ```

   ![](/help/assets/screenshot2028126029.png){width="50%" align="left"}

1. Seleziona **Considera affidabili gli autori di tutti i file presenti nella cartella principale** e fai clic su **Sì, considero affidabili gli autori**.

   ![](/help/assets/screenshot2028116229.png){width="50%" align="left"}

1. Rinominare il file `env_template` in .env.  Per rinominare il file, fai clic con il pulsante destro del mouse sul file **env_template** e seleziona l’opzione **Rinomina**.

   ![](/help/assets/screenshot2028116429.png){width="30%" align="left"}

   </br>

   ![](/help/assets/screenshot2028116529.png){width="50%" align="left"}

1. Imposta i seguenti valori per le variabili nel file .env e salva il file:

   * **URL_AEM**: specificare l&#39;URL di un&#39;istanza **publish**. Ad esempio `https://localhost:4502/`

   * **AEM_ADAPTIVE_FORM**: specificare il nome del modulo. Esempio: `contact-us`.

   </br>

   ![](/help/assets/lab65-theme-environment-variable.png)


1. Nella finestra del prompt dei comandi esegui il comando seguente:

   ```Shell
   npm install
   ```

   ![](/help/assets/screenshot2028117029.png)

   >[!NOTE]
   >
   > * Se ricevi un messaggio che chiede di aggiornare npm tramite il comando `npm notice Run npm nstall -g npm@9.6.0`, ignora il messaggio.
   > * Non eseguire altri comandi npm a meno che non sia indicato nella cartella di lavoro.

1. Ora, per visualizzare l’anteprima del modulo, esegui il comando seguente.

   ```Shell
   npm run live
   ```

   ![](/help/assets/screenshot2028117229.png)

   Una volta eseguito il comando precedente, attendi il messaggio `webpack compiled`. Il modulo viene visualizzato in una scheda del browser.

   >[!NOTE]
   >
   >Se, dopo l’esecuzione del comando `npm run live`, nel browser viene visualizzata una schermata vuota per più di 3-4 minuti, cambia `localhost` nell’URL del browser con 127.0.0.1 e premi **Invio**.


   ![](/help/assets/contact-us-headless-adaptive-form-with-canvas-theme.png){width="50%" align="left"}


1. In Visual Studio Code, apri il file `PROJECT\src\site\_variables.scss`. Nota che il colore `$error` è una tonalità di rosso.

   ![](/help/assets/screenshot2028120729.png){width="50%" align="left"}

1. Nel browser, invia il modulo per visualizzare il colore rosso nel campo **Nome**.

   ![](/help/assets/error-color-before.png)

1. Imposta il colore di **$error** su **#5736eb** e salva il file.

1. Aggiorna il browser e invia il modulo. Nota che il colore dell’errore è stato modificato anche nel campo del nome.

   ![](/help/assets/error-color-after.png)

1. Nel prompt dei comandi, premi **CTRL+C**, immetti **Y** e premi il tasto **Invio** per interrompere il processo npm. È importante interrompere il server npm in modo che non entri in conflitto con il successivo set di esercizi.
1. Chiudi le finestre di Visual Studio Code e il prompt dei comandi.

## Lezione 4

### Obiettivo

Eseguire il rendering del modulo per web/mobile e altre interfacce come modulo headless.

### Contesto della lezione

In questa lezione, come sviluppatore front-end, imparerai a eseguire il rendering del modulo adattivo creato in precedenza come modulo headless utilizzando il framework di progettazione dello spettro di react.

### Esercizio

Configurazione dell’archivio locale utilizzando il progetto iniziale di React:

1. Apri il prompt dei comandi utilizzando i diritti di amministratore.

   ![](/help/assets/screenshot2028115829.png){width="30%" align="left"}

1. Al prompt dei comandi utilizzare il comando seguente per passare alla cartella `c:\git`.

   ```Shell
   cd git
   ```

1. Utilizza il seguente comando per clonare il progetto iniziale React modulo adattivo:

   ```Shell
   git clone https://github.com/adobe/react-starter-kit-aem-headless-forms
   ```

   ![](/help/assets/screenshot2028117329.png)

1. Per passare alla directory **react-starter-kit-aem-headless forms** e aprire Visual Studio Code, utilizza i comandi seguenti nell’ordine elencato.

   ```Shell
   cd react-starter-kit-aem-headless-forms
   
   code .
   ```

   ![](/help/assets/screenshot2028117529.png)


   Si apre la finestra di Visual Studio Code.

   ![](/help/assets/screenshot2028117429.png){width="50%" align="left"}

Per eseguire il rendering del modulo in hosting nell’ambiente di pubblicazione:

1. Rinomina il file env_template in file .env. Per rinominarlo, fai clic con il pulsante destro del mouse sul file **env_template** e seleziona l’opzione **Rinomina**.

   ![](/help/assets/screenshot2028117629.png){width="30%" align="left"}

   ![](/help/assets/screenshot2028117729.png)

1. Imposta i seguenti valori per le variabili nel file .env. Dopo aver aggiornato le variabili, salva il file.

   * **URL_AEM**: specifica l&#39;URL dell&#39;ambiente di pubblicazione. Ad esempio `https://localhost:4503/`

   * **AEM_FORM_PATH**: specifica il percorso del modulo adattivo creato nella lezione precedente. Ad esempio `/content/forms/af/contact-us/`

   </br>

   ![](/help/assets/lab65-starter-kit-environment-variable.png)

1. Apri la finestra dei comandi, assicurati di essere nella directory **react-starter-kit-aem-headless forms** ed esegui il comando seguente:

   ```Shell
   npm install
   ```

   ![](/help/assets/screenshot2028118029.png)


1. Nella finestra del prompt dei comandi esegui il comando seguente:

   ```Shell
   npm start
   ```

   ![](/help/assets/lab65-starter-kit-start.png)

   Il comando precedente avvia un server di sviluppo locale che eseguirà il rendering della definizione del modulo recuperata da AEM in modo headless utilizzando la libreria front-end di React Spectrum.

   >[!NOTE]
   >
   > 
   > Se, dopo l’esecuzione del comando `npm start`, nel browser viene visualizzata una schermata vuota per più di 3-4 minuti, cambia `localhost` nell’URL del browser con 127.0.0.1 e premi **Invio**.

   ![](/help/assets/headless-adaptive-form-lab.png)

Apporta le modifiche al modulo sul server come utente aziendale e visualizza le modifiche riprodotte automaticamente nel modulo headless.

1. Apri l’interfaccia di gestione di AEM Forms nel browser. Ad esempio, [http://localhost:4502/aem/forms.html/content/dam/formsanddocuments](http://localhost:4502/aem/forms.html/content/dam/formsanddocuments).

1. Selezionare il modulo **Contattaci** e fare clic su **Modifica.** apre il modulo nell&#39;editor di Forms adattivo.


1. Selezionare il campo **Contatto** e fare clic sull&#39;icona **Modifica (icona a forma di matita)** nella barra degli strumenti. Se la barra degli strumenti a comparsa non è visibile, passa alla modalità Modifica facendo clic sul pulsante **Modifica** in alto a destra, a sinistra del pulsante **Anteprima**.

   ![](/help/assets/change-field-title.png){width="50%" align="left"}

1. Cambia l&#39;etichetta in **Mobile Number**. Fai clic su uno spazio vuoto nel modulo per salvare le modifiche apportate.

Pubblichiamo il modulo aggiornato per propagare le modifiche all’ambiente di pubblicazione.

1. Nella scheda dell&#39;interfaccia di gestione di AEM Forms, seleziona il modulo Contattaci e fai clic su **Annulla pubblicazione**. Se non viene visualizzato il pulsante **Annulla pubblicazione**, vai al passaggio 3 per pubblicare le modifiche direttamente.


1. Fai clic su **Annulla pubblicazione**. Fai clic su **Chiudi** nella rispettiva finestra di dialogo.

1. Dopo l&#39;aggiornamento del browser, selezionare il modulo Contattaci e fare clic su **Publish**.


1. Fai clic su **Pubblica**. Fai clic su **Chiudi** nella rispettiva finestra di dialogo.

1. Aggiorna la scheda del browser con il modulo headless visualizzato. L&#39;etichetta del numero di contatto è stata modificata in Numero cellulare.

   ![](/help/assets/headless-adaptive-form.png)

1. Apri la finestra del prompt dei comandi utilizzata per avviare il progetto **react-starter-kit-aem-headless forms**, premi **CTRL+C**, quindi 
immetti **Y** e premi il tasto Invio per terminare il processo npm. È importante interrompere il server npm in modo che non entri in conflitto con il successivo set di esercizi.

1. Chiudi le finestre di Visual Studio Code e il prompt dei comandi.


## Lezione 5

### Obiettivo

Eseguire il rendering del modulo come modulo headless utilizzando l’interfaccia utente Google Material

### Contesto della lezione

In questa lezione, in qualità di sviluppatore front-end, imparerai a eseguire il rendering del modulo adattivo creato in precedenza come modulo headless tramite l’interfaccia utente Materiale di Google.

### Esercizio

Imposta l’archivio locale utilizzando il progetto iniziale dell’interfaccia utente Material:

1. Apri il prompt dei comandi utilizzando i diritti di amministratore.

   ![](/help/assets/screenshot2028115829.png){width="30%" align="left"}

1. Al prompt dei comandi utilizzare il comando seguente per passare alla cartella `c:\git`.

   ```Shell
   cd git
   ```

1. Esegui i seguenti comandi nell’ordine elencato per creare una cartella denominata “mui” e passa alla cartella “mui” utilizzando i seguenti comandi:

   ```Shell
   mkdir mui
   
   cd mui
   ```

1. Utilizza il seguente comando per clonare il progetto iniziale React modulo adattivo:

   ```Shell
   git clone -b mui-lab https://github.com/adobe/react-starter-kit-aem-headless-forms
   ```

   ![](/help/assets/screenshot2028126529.png)

1. Per passare alla cartella **react-starter-kit-aem-headless forms** e aprire il codice in Visual Studio Code, utilizza il comando seguente nell&#39;ordine elencato:

   ```Shell
   cd react-starter-kit-aem-headless-forms
   
   code .
   ```

   ![](/help/assets/screenshot2028126829.png)

Per eseguire il rendering del modulo in hosting nell’ambiente di pubblicazione:

1. Rinomina il file **env_template** in file **.env**. Per rinominarlo, fai clic con il pulsante destro del mouse sul file **env_template** e seleziona **Rinomina**.

   ![](/help/assets/screenshot2028126629.png){width="30%" align="left"}

1. Imposta i seguenti valori per le variabili nel file .env. Dopo aver aggiornato le variabili, salva il file. Utilizza la combinazione di tasti **CTRL+S** per salvare il file.

   * **URL_AEM**: specifica l&#39;URL dell&#39;ambiente di pubblicazione. Ad esempio, [https://localhost:4503](https://localhost:4503)

   * **AEM_FORM_PATH**: specifica il percorso del modulo adattivo creato nella lezione precedente. Ad esempio, /content/forms/af/contact-us/


1. Apri la finestra dei comandi, assicurati di essere nella directory **react-starter-kit-aem-headless forms** ed esegui il comando seguente:

   ```Shell
   npm install
   ```

   ![](/help/assets/screenshot2028127029.png)

1. Nella finestra del prompt dei comandi esegui il comando seguente:

   ```Shell
   npm start
   ```

   ![](/help/assets/lab65-mui-starter-kit-start.png)

   Il comando avvia un server di sviluppo locale ed esegue il rendering della definizione del modulo recuperata dall’AEM in modo headless utilizzando la libreria front-end dell’interfaccia utente dei materiali di Google.

   >[!NOTE]
   >
   >Se, dopo l’esecuzione del comando `npm start`, nel browser viene visualizzata una schermata vuota per più di 3-4 minuti, cambia `localhost` nell’URL del browser con 127.0.0.1 e premi **Invio**.

   ![](/help/assets/google-mui-form.png)

## Lezione 6

### Obiettivo

Creare un aspetto alternativo del modulo headless utilizzando le varianti dei componenti dell’interfaccia utente Material

### Contesto della lezione

In questa lezione, in qualità di sviluppatore front-end, imparerai a creare una rappresentazione alternativa di diversi componenti utilizzando l’interfaccia utente Materiale per il modulo adattivo creato in precedenza dall’utente aziendale.

### Esercizio

Aggiorna la variante dei componenti nel progetto headless. Per modificare la variante del componente di inserimento testo dell’interfaccia utente Material in `OutlinedInput`:

1. In Visual Code, passa al componente di inserimento testo aprendo il file `index.tsx` in `src/components/textinput/index.tsx`.

1. Aggiungi `//` all’inizio della riga di codice 104. Converte la riga in un commento.

   ```Shell
   //const Cmp = \'outlined\' === appliedCssClassNames ? OutlinedInput: Input;
   ```

1. Aggiungi quanto segue alla riga 105 per utilizzare una variante diversa del componente e salva il file. Utilizza la combinazione di tasti **CTRL+S** per salvare il file.

   ```Shell
   const Cmp = OutlinedInput;
   ```

   ![](/help/assets/aem65-lab-code-update.png)

   È necessario utilizzare le maiuscole corrette per la variante “OutlineInput”; in caso contrario la compilazione avrà esito negativo. La compilazione dell’ambiente di sviluppo locale inizia automaticamente nel prompt dei comandi. Attendi che venga visualizzato il seguente messaggio:

   `webpack 5.75.0 compiled with 3 warnings in 6659 ms`
   `inside proxy req`
   `setting new origin header`

1. Se la pagina nel browser non si aggiorna automaticamente, aggiornala per visualizzare il componente di input di testo con una variante diversa.

   ![](/help/assets/screenshot2028127729.png){width="50%" align="left"}


   Questa modifica viene applicata agli utenti finali senza alcuna modifica alla definizione del modulo nel server di AEM Forms ed è specifica per il canale headless in esame. Per esempio, un canale web in questo workshop.

   ![](/help/assets/aem65-lab-mui-style-update.png)


1. Chiudi le finestre di Visual Studio Code e il prompt dei comandi.

## Domande frequenti (FAQ)

+++ I Componenti core sono disponibili al pubblico?

Sì, i componenti core Adaptive Forms sono disponibili con Forms AEM 6.5 e Forms come Cloud Service. Per utilizzare i componenti core Adaptive Forms è necessario AEM Forms 6.5 Service Pack 16 o versione successiva.

+++

+++ I moduli headless richiedono una licenza separata?

No, i moduli headless utilizzano la stessa metrica del valore di licenza, numero di invii dei moduli.

+++




## Passaggi successivi

Ora che hai imparato a creare Forms adattivo e a distribuirlo a più canali utilizzando moduli headless, dovresti provare a mettere in atto le nuove competenze. Buon lavoro, e continua a creare e distribuire esperienze eccezionali con acquisizione dati, per i tuoi utenti finali ovunque si trovano e su larga scala!

## Riferimenti

* [Introduzione ai componenti core per moduli adattivi](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=it)

* [Creare un modulo adattivo utilizzando i componenti core](https://experienceleague.corp.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/creating-adaptive-form-core-components.html?lang=it)

* [Aggiornare lo stile per moduli adattivi basati su componenti core](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/using-themes-in-core-components.html?lang=it)

* [Forms adattivo headless](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html?lang=it)

* [Utilizzo dello starter kit Headless React](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/get-started/create-and-publish-a-headless-form.html?lang=it)
