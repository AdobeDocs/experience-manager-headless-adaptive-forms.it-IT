---
title: Creare moduli efficaci utilizzando i componenti core e headless
seo-title: Build Engaging Forms Using Core Components and Headless
description: Creare moduli efficaci utilizzando i componenti core e headless
seo-description: Build Engaging Forms Using Core Components and Headless
topic-tags: develop
exl-id: ef99ffe9-4a37-4f0a-a4d3-78976c92220f
source-git-commit: bcc51bcae3b26cf20e7c0b5b75935bf69a991731
workflow-type: tm+mt
source-wordcount: '2452'
ht-degree: 85%

---

# Creare Forms coinvolgenti utilizzando componenti core e Forms adattivo headless in AEM Forms as a Cloud Service {#build-engaging-forms-using-core-components-and-headless}

## Panoramica del workshop {#lab-overview}

In questo workshop pratico imparerai:

come utilizzare AEM Forms per creare facilmente moduli adattivi utilizzando i componenti core più recenti, coerenti con AEM Sites, per rendere possibili esperienze di acquisizione dei dati omnicanale grazie alla distribuzione di moduli adattivi come moduli headless al web, ai mobile e alle chat. Inoltre, puoi imparare le best practice relative allo stile, alle personalizzazioni e allo sviluppo front-end.

## Elementi principali da ricordare {#key-takeaways}

* **Agilità dell’azienda**: in qualità di utente aziendale, posso creare facilmente un’esperienza con i moduli per più canali.

* **Più controllo per gli sviluppatori front-end**: in qualità di sviluppatore front-end, posso controllare l’esperienza dell’utente finale utilizzando moduli headless.

* **Velocità di sviluppo**: in qualità di sviluppatore, posso personalizzare i componenti Sites e Forms in modo facile e coerente.

## Prerequisiti {#prerequisites}

Per usare queste mani sul laboratorio:

* Installa la [versione più recente di Git](https://git-scm.com/downloads). Se sei un nuovo utente di Git, vedi [Installazione di Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).

* Installa [Node.js 16.13.0 o versione successiva](https://nodejs.org/it/download/). Se hai poca esperienza con Node.js, consulta [Come installare Node.js](https://nodejs.org/en/learn/getting-started/how-to-install-nodejs).

* [Abilita i componenti core adattivi di Forms](enable-headless-adaptive-forms-and-core-components-on-forms-cloud-service.md) per l&#39;ambiente AEM Forms as a Cloud Service.

* Installa [Microsoft Visual Studio Code](https://code.visualstudio.com/download) o qualsiasi editor di testo normale. Esempi in un documento utilizzano Microsoft Visual Studio Code.



## Lezione 1 {#lesson-1}

### Obiettivo {#lesson-1-objectives}

Acquisisci familiarità con l’ambiente di AEM Forms as a Cloud Service.

### Contesto della lezione {#lesson-1-context}

In questa lezione imparerai a conoscere l’ambiente di AEM Forms as a Cloud Service navigando nell’interfaccia utente.

### Esercizio {#lesson-1-excercise}

1. Apri il browser e immetti l’URL dell’ambiente di authoring di Cloud Service. Ad esempio:
   [https://author-p105303-e986623.adobeaemcloud.com/ui#/aem/aem/start.html](https://author-p105303-e986623.adobeaemcloud.com/ui%23/aem/aem/start.html)

1. Accedi all’ambiente di authoring del Cloud Service.
   ![](/help/assets/screenshot2028113829.png){width="50%" align="left"}

1. Per passare all&#39;interfaccia utente di AEM Forms, fare clic su **Forms > Forms &amp; Documents**.



   ![](/help/assets/screenshot2028113929.png){width="50%" align="left"}

   Ignora eventuali popup relativi a preferenze o informazioni. Vengono visualizzati tutti i moduli disponibili.


## Lezione 2

### Obiettivo

Crea un modulo adattivo utilizzando i componenti core più recenti, configuralo e invialo.

### Contesto della lezione

In questa lezione, in qualità di utente aziendale, verrà creato un modulo adattivo per più canali, come web, dispositivi mobili e chat, utilizzando l’authoring di moduli adattivi con componenti core standard predefiniti per l’acquisizione dei dati.

### Esercizio

1. Crea un endpoint di invio per il modulo:

   1. Apri <https://requestbin.com/> in una nuova scheda del browser.
   1. Fai clic su **Crea un bin pubblico** e copia l’URL dell’endpoint.
      ![](/help/assets/screenshot2028114329.png){width="50%" align="left"}

      ![](/help/assets/screenshot202023-03-0120at206.10.0020pm.png){width="50%" align="left"}

1. Crea un modulo adattivo utilizzando l’interfaccia della procedura guidata:

   1. Nella scheda del browser utilizzata nella lezione 1, vai all’interfaccia web di AEM Forms as Cloud Service e passa a moduli e documenti.
      ![](/help/assets/screenshot2028114029.png)

   1. Fai clic su **Crea** e seleziona Modulo adattivo.
      ![](/help/assets/screenshot2028114629.png)

   1. Seleziona il modello **Vuoto con i componenti core** dalla schermata di selezione del modello come mostrato di seguito:
      ![](/help/assets/screenshot202023-03-0120at206.09.1520pm.png)

   1. Fai clic sulla scheda **Stile** e seleziona il tema **wknd-theme** come mostrato di seguito:
      ![](/help/assets/screenshot202023-03-0120at206.09.2320pm.png)

   1. Fai clic sulla scheda **Invio**, seleziona la scheda **Invia all&#39;endpoint REST** e specifica il contenitore pubblico nel campo **URL per la richiesta POST**, come illustrato di seguito:
      ![](/help/assets/screenshot202023-03-0120at206.09.5320pm.png)

   1. Fai clic su **Crea**. Specifica un nome e un titolo per il modulo. Ad esempio, **registrazione**. Fai clic su **Crea**.

   1. Viene aperto l’editor di moduli adattivi. Chiudi eventuali pop-up o finestre di dialogo relativi a preferenze o informazioni. Fai clic sul browser Componenti nella barra a sinistra e aggiungi i componenti **Intestazione** e **Piè di pagina** rispettivamente all&#39;inizio e alla fine del modulo vuoto.
      ![](/help/assets/screenshot2028121929.png)

   1. Trascina i componenti dal browser Componenti per creare un modulo simile al seguente:

      ![](/help/assets/screenshot2028115129.png){width="50%" align="left"}

1. Aggiungi convalide al modulo:

   1. Fai clic sul componente **Numero di telefono** in modo da visualizzare il menu a comparsa. Fai clic sull’**icona a forma di chiave inglese** nel menu per configurare il campo.

   1. Apri la **scheda convalide**, contrassegna il campo come **Obbligatorio** e fai clic su **Fine**. Viene visualizzato il messaggio di operazione riuscita.
      ![](/help/assets/screenshot2028123529.png){width="50%" align="left"}

      ![](/help/assets/screenshot2028123629.png){width="50%" align="left"}

1. Visualizzare l&#39;anteprima e inviare il modulo.

   1. Fai clic su **Anteprima** per visualizzare l’anteprima del modulo dal punto di vista dell’utente finale.

   1. Compila il modulo con dati fittizi.

   1. Invia il modulo.
      ![](/help/assets/screenshot2028125729.png)

   1. Nella scheda Raccoglitore richieste, controlla i dati inviati.
      ![](/help/assets/screenshot2028125829.png)

1. Aggiungi interattività al modulo con le regole:

   1. Fai clic sulla **Seleziona la casella per ricevere il 5% di sconto** del componente. Sulla barra degli strumenti delle opzioni fare clic sull&#39;icona Regole. Viene visualizzata l’opzione Editor regole.

   1. Crea una regola: quando l&#39;opzione **Seleziona la casella per ricevere il 5% di sconto** è selezionata, le opzioni per l&#39;applicazione della carta di credito sono disabilitate.

1. Publish il modulo.

   1. Aprire l&#39;interfaccia di gestione di AEM Forms, ad esempio `https://author-p105303-e986623.adobeaemcloud.com/ui%23/aem/aem/forms.html/content/dam/formsanddocuments`, e selezionare il modulo.

   1. Fai clic su **Pubblica**.

      ![](/help/assets/screenshot2028115629.png)

      Viene visualizzato il messaggio di operazione riuscita.

      ![](/help/assets/screenshot2028115729.png)

      L’URL di pubblicazione del modulo sarà simile a `https://publish-p105303-e986623.adobeaemcloud.com/content/forms/af/registration.html`.

   1. Per visualizzare il modulo pubblicato, sostituisci l’ID del programma (pXXXXXX) e l’ID dell’ambiente (eXXXXXX) nell’URL precedente con l’ID 
del tuo ambiente.

## Lezione 3

### Obiettivo

Aggiornare gli stili utilizzando le best practice di sviluppo front-end.

### Contesto della lezione

In questa lezione, in qualità di sviluppatore front-end, ti verrà illustrato come aggiornare facilmente lo stile del modulo adattivo creato in precedenza.

### Esercizio

Configurazione dell’archivio locale del tema:

1. Apri il prompt o la shell dei comandi con i diritti di amministratore:

   ![](/help/assets/screenshot2028115829.png){width="50%" align="left"}

1. Sul prompt dei comandi, utilizza il comando seguente per passare alla cartella **c:\git**

   ```Shell
   cd c:\git
   ```

1. Per clonare il codice di front-end del tema, utilizza il comando seguente:

   ```Shell
   git clone -b WKND https://github.com/adobe/aem-forms-theme-canvas
   ```


1. Per passare alla directory **aem-forms-theme-canvas** e aprire Visual Studio Code, utilizza il seguente comando nell’ordine elencato.

   ```Shell
   cd aem-forms-theme-canvas
   code .
   ```

   ![](/help/assets/screenshot2028126029.png)

1. Seleziona **Considera affidabili gli autori di tutti i file presenti nella cartella principale** e fai clic su **Sì, considero affidabili gli autori**.

   ![](/help/assets/screenshot2028116229.png){width="50%" align="left"}

1. Per eseguire il rendering del modulo ospitato nell’ambiente di pubblicazione del cloud service, rinomina il file `env_template`.  Per rinominare il file, fai clic con il pulsante destro del mouse sul file **env_template** e seleziona l’opzione **Rinomina**.

   ![](/help/assets/screenshot2028116429.png){width="50%" align="left"}

   </br>

   ![](/help/assets/screenshot2028116529.png){width="50%" align="left"}

1. Imposta i seguenti valori per le variabili nel file .env e salva il file:

   * **AEM_URL**: specifica l’ambiente di pubblicazione del cloud service. Ad esempio `https://publish-p105303-e986623.adobeaemcloud.com/`

   * **AEM_ADAPTIVE_FORM**: specifica il percorso del modulo. Ad esempio, se il percorso del modulo è `/content/forms/af/registration`, il valore di questa variabile sarà `registration`.

     ![](/help/assets/screenshot2028116429.png){width="50%" align="left"}

1. Creare un utente locale nell’ambiente AEM.

   >[!NOTE]
   > Per creare un utente locale:
   > Vai a `AEM Home` > `Tools` > `Security` > `Users`
   > Assicurati che l’utente sia membro del gruppo forms-users.


1. Nella finestra del prompt dei comandi esegui il comando seguente:

   ```Shell
   npm install
   ```

   ![](/help/assets/screenshot2028117029.png)

   >[!NOTE]
   >
   > * Se viene visualizzato un messaggio in cui viene richiesto di aggiornare npm tramite il comando `npm notice Run npm nstall -g npm@9.6.0`, ignorare il messaggio.
   > * Non eseguire altri comandi npm a meno che non sia indicato nella cartella di lavoro.

1. Ora, per visualizzare l’anteprima del modulo, esegui il comando seguente.

   ```Shell
   npm run live
   ```

   ![](/help/assets/screenshot2028117229.png)

   Una volta eseguito il comando precedente, attendere il messaggio `webpack compiled` e si viene reindirizzati a una pagina di accesso AEM.

1. Fare clic su **Accedi localmente (solo attività amministratore)** nella pagina di accesso AEM.
1. Immettere le credenziali per l&#39;utente locale creato e il modulo verrà visualizzato in una scheda del browser.

   >[!NOTE]
   >
   >Se, dopo l’esecuzione del comando `npm run live`, nel browser viene visualizzata una schermata vuota per più di 3-4 minuti, cambia `localhost` nell’URL del browser con 127.0.0.1 e premi **Invio**.


   ![](/help/assets/screenshot2028115129.png){width="50%" align="left"}


1. In Visual Studio Code, apri il file `PROJECT\src\site\_variables.scss`. Nota che il colore `$error` è una tonalità di rosso.

   ![](/help/assets/screenshot2028120729.png){width="50%" align="left"}

1. Nel browser, invia il modulo per visualizzare il colore rosso nel campo **Nome**.

   ![](/help/assets/screenshot2028120829.png)

1. Imposta il colore di **$error** su **#5736eb** e salva il file.

   ![](/help/assets/screenshot2028120729.png){width="50%" align="left"}

1. Aggiorna il browser e invia il modulo. Nota che il colore dell’errore è stato modificato anche nel campo del nome.

   ![](/help/assets/screenshot2028121129.png)

1. Nel prompt dei comandi, premi **CTRL+C**, immetti **Y** e premi il tasto **Invio** per interrompere il processo npm. È importante interrompere il server npm in modo che non entri in conflitto con il successivo set di esercizi.
1. Chiudi le finestre di Visual Studio Code e il prompt dei comandi.

## Lezione 4

### Obiettivo

Eseguire il rendering del modulo per web/mobile e altre interfacce come modulo headless.

### Contesto della lezione

In questa lezione, in qualità di sviluppatore front-end, ti verrà illustrato come eseguire il rendering del modulo adattivo creato in precedenza come modulo headless utilizzando il framework di progettazione di React Spectrum.

### Esercizio

Configurazione dell’archivio locale utilizzando il progetto iniziale di React:

1. Apri il prompt dei comandi utilizzando i diritti di amministratore.

   ![](/help/assets/screenshot2028115829.png){width="50%" align="left"}

1. Sul prompt dei comandi utilizza il comando seguente per passare alla cartella **c:\git**

   ```Shell
   cd c:\git
   ```

1. Per clonare il progetto iniziale di React del modulo adattivo, utilizza il comando seguente:

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

Per eseguire il rendering del modulo ospitato nell’ambiente di pubblicazione del cloud service:

1. Rinomina il file env_template in file .env. Per rinominarlo, fai clic con il pulsante destro del mouse sul file **env_template** e seleziona l’opzione **Rinomina**.

   ![](/help/assets/screenshot2028117629.png){width="50%" align="left"}

   ![](/help/assets/screenshot2028117729.png)

1. Imposta i seguenti valori per le variabili nel file .env. Dopo aver aggiornato le variabili, salva il file.

   * **AEM_URL**: specifica l’URL dell’ambiente di pubblicazione del cloud service. Ad esempio `https://publish-p105303-e986623.adobeaemcloud.com`

   * **AEM_FORM_PATH**: specifica il percorso del modulo adattivo creato nella lezione precedente. Ad esempio `/content/forms/af/registration/`

     ![](/help/assets/screenshot202023-03-0820at202.49.1820pm.png)

1. Apri la finestra dei comandi, assicurati di essere nella directory react-starter-kit-aem-headless-forms ed esegui il seguente comando:

   ```Shell
   npm install
   ```

   ![](/help/assets/screenshot2028118029.png)


1. Nella finestra del prompt dei comandi esegui il comando seguente:

   ```Shell
   npm start
   ```

   ![](/help/assets/screenshot2028118129.png)

   Il comando precedente avvia un server di sviluppo locale che eseguirà il rendering della definizione del modulo recuperata da AEM in modo headless utilizzando la libreria front-end di React Spectrum.

   >[!NOTE]
   >
   > 
   > Se, dopo l’esecuzione del comando `npm start`, nel browser viene visualizzata una schermata vuota per più di 3-4 minuti, cambia `localhost` nell’URL del browser con 127.0.0.1 e premi **Invio**.

   ![](/help/assets/screenshot2028118229.png)

Verifichiamo l’esecuzione delle regole in questo modulo headless:

1. Scegli l’opzione **Seleziona la casella per ricevere il 5% di sconto**. L’opzione successiva per la richiesta della carta di credito è disabilitata.

   ![](/help/assets/screenshot2028126229.png)

1. Deseleziona **Seleziona la casella per ricevere il 5% di sconto** per abilitare l’opzione della carta di credito.

   ![](/help/assets/screenshot2028126329.png)

Apporta le modifiche al modulo sul server come utente aziendale e visualizza le modifiche riprodotte automaticamente nel modulo headless.

1. Apri l’interfaccia di gestione di AEM Forms nel browser. Ad esempio: [https://author-p105303-e986623.adobeaemcloud.com/ui#/aem/aem/forms.html/content/dam/formsanddocuments](https://author-p105303-e986623.adobeaemcloud.com/ui%23/aem/aem/forms.html/content/dam/formsanddocuments).

1. Selezionare il modulo **contactus** e fare clic su **Modifica.** Il modulo viene aperto nell’editor di moduli adattivi.


1. Seleziona il campo **Numero di telefono** e fai clic sull’**icona Modifica (a forma di matita)** nella barra degli strumenti. Se la barra degli strumenti a comparsa non è visibile, passa alla modalità Modifica facendo clic sul pulsante **Modifica** in alto a destra, a sinistra del pulsante **Anteprima**.

   ![](/help/assets/screenshot2028119629.png)

1. Cambia l’etichetta in Numero cellulare. Fai clic su uno spazio vuoto nel modulo per salvare le modifiche apportate.

   ![](/help/assets/screenshot2028119729.png)

Pubblichiamo il modulo aggiornato per propagare le modifiche all’ambiente di pubblicazione.

1. Nella scheda dell’interfaccia di gestione di AEM Forms, seleziona il modulo di registrazione e fai clic su **Annulla pubblicazione**. Se non viene visualizzato il pulsante **Annulla pubblicazione**, vai al passaggio 3 per pubblicare le modifiche direttamente.

1. Fai clic su **Annulla pubblicazione**. Fai clic su **Chiudi** nella rispettiva finestra di dialogo.

1. Dopo l’aggiornamento del browser, seleziona il modulo di registrazione e fai clic su **Pubblica**.

1. Fai clic su **Pubblica**. Fai clic su **Chiudi** nella rispettiva finestra di dialogo.

1. Aggiorna la scheda del browser con il modulo headless visualizzato. Nota che l’etichetta del numero di telefono è stata modificata in Numero cellulare.

   ![](/help/assets/screenshot2028120529.png)

1. Apri la finestra del prompt dei comandi utilizzata per avviare il progetto **react-starter-kit-aem-headless forms**, premi **CTRL+C**, quindi 
immetti **Y** e premi il tasto Invio per terminare il processo npm. È importante interrompere il server npm in modo che non entri in conflitto con il successivo set di esercizi.

1. Chiudi le finestre di Visual Studio Code e il prompt dei comandi.


## Lezione 5

### Obiettivo

Eseguire il rendering del modulo come modulo headless utilizzando l’interfaccia utente Google Material

### Contesto della lezione

In questa lezione, in qualità di sviluppatore front-end, ti verrà illustrato come eseguire il rendering del modulo adattivo creato in precedenza come modulo headless utilizzando l’interfaccia utente Google Material.

### Esercizio

Imposta l’archivio locale utilizzando il progetto iniziale dell’interfaccia utente Material:

1. Apri il prompt dei comandi utilizzando i diritti di amministratore.

   ![](/help/assets/screenshot2028115829.png){width="50%" align="left"}


1. Al prompt dei comandi, utilizza il comando seguente per passare alla cartella **c:\git**:

   ```Shell
   cd c:\git
   ```

1. Esegui i seguenti comandi nell’ordine elencato per creare una cartella denominata “mui” e passa alla cartella “mui” utilizzando i seguenti comandi:

   ```Shell
   mkdir mui
   
   cd mui
   ```

1. Per clonare il progetto iniziale di React del modulo adattivo, utilizza il comando seguente:

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

Per eseguire il rendering del modulo ospitato nell’ambiente di pubblicazione del cloud service:

1. Rinomina il file **env_template** in file **.env**. Per rinominarlo, fai clic con il pulsante destro del mouse sul file **env_template** e seleziona **Rinomina**.

   ![](/help/assets/screenshot2028126629.png){width="50%" align="left"}

1. Imposta i seguenti valori per le variabili nel file .env. Dopo aver aggiornato le variabili, salva il file. Utilizza la combinazione di tasti **CTRL+S** per salvare il file.

   * **AEM_URL**: specifica l’URL dell’ambiente di pubblicazione del cloud service. Ad esempio: [https://publish-p105303-e986623.adobeaemcloud.com](https://publish-p105303-e986623.adobeaemcloud.com/)

   * **AEM_FORM_PATH**: specifica il percorso del modulo adattivo creato nella lezione precedente. Ad esempio, /content/forms/af/registration/

     ![](/help/assets/screenshot2028126929.png)

1. Apri la finestra dei comandi, assicurati di essere nella directory **react-starter-kit-aem-headless forms** ed esegui il comando seguente:

   ```Shell
   npm install
   ```

   ![](/help/assets/screenshot2028127029.png)

1. Nella finestra del prompt dei comandi esegui il comando seguente:

   ```Shell
   npm start
   ```

   ![](/help/assets/screenshot2028127129.png)

   Il comando avvia un server di sviluppo locale che esegue il rendering della definizione del modulo recuperata da AEM in modo headless utilizzando la libreria front-end 
dell’interfaccia utente Google Material.

   >[!NOTE]
   >
   >Se, dopo l’esecuzione del comando `npm start`, nel browser viene visualizzata una schermata vuota per più di 3-4 minuti, cambia `localhost` nell’URL del browser con 127.0.0.1 e premi **Invio**.

   ![](/help/assets/screenshot2028127229.png)

1. Per valutare l’esecuzione della stessa logica di business nella rappresentazione del modulo:

   Fai clic su **Seleziona la casella per ricevere il 5% di sconto**. L’opzione successiva **Desideri richiedere il modulo per la carta di credito della società We.Finance?** viene disattivata.

   ![](/help/assets/screenshot2028127329.png){width="50%" align="left"}

## Lezione 6

### Obiettivo

Creare un aspetto alternativo del modulo headless utilizzando le varianti dei componenti dell’interfaccia utente Material

### Contesto della lezione

In questa lezione, in qualità di sviluppatore front-end, ti verrà illustrato come creare una rappresentazione alternativa di componenti diversi utilizzando l’interfaccia utente Material per il modulo adattivo creato in precedenza dall’utente aziendale.

### Esercizio

Aggiorna la variante dei componenti nel progetto headless. Per modificare la variante del componente di inserimento testo dell’interfaccia utente Material in `OutlinedInput`:

1. In Visual Code, passa al componente di inserimento testo aprendo il file `index.tsx` in `src/components/textinput/index.tsx`.

1. Aggiungi `//` all’inizio della riga di codice 103. Converte la riga in un commento.

   ```Shell
   //const Cmp = \'outlined\' === appliedCssClassNames ? OutlinedInput: Input;
   ```

1. Aggiungi quanto segue alla riga 104 per utilizzare una variante diversa del componente e salva il file. Utilizza la combinazione di tasti **CTRL+S** per salvare il file.

   ```Shell
   const Cmp = OutlinedInput;
   ```

   ![](/help/assets/screenshot2028127629.png)

   È necessario utilizzare le maiuscole corrette per la variante “OutlineInput”; in caso contrario la compilazione avrà esito negativo. La compilazione dell’ambiente di sviluppo locale inizia automaticamente nel prompt dei comandi. Attendi che venga visualizzato il seguente messaggio:

   `webpack 5.75.0 compiled with 3 warnings in 6659 ms`
   `inside proxy req`
   `setting new origin header`

1. Se la pagina nel browser non si aggiorna automaticamente, aggiornala per visualizzare il componente di input di testo con una variante diversa.

   ![](/help/assets/screenshot2028127729.png)


   Questa modifica viene applicata agli utenti finali senza alcuna modifica alla definizione del modulo nel server di AEM Forms ed è specifica per il canale headless in esame. Per esempio, un canale web in questo workshop.

   ![](/help/assets/screenshot2028127529.png){width="50%" align="left"}


1. Chiudi le finestre di Visual Studio Code e il prompt dei comandi.

## Domande frequenti (FAQ)

+++ La procedura guidata per moduli adattivi è disponibile pubblicamente?

Sì, è disponibile in AEM Forms as Cloud Service.

+++


+++ I componenti core sono disponibili pubblicamente?

Sì, i componenti core per moduli adattivi sono disponibili in AEM Forms as Cloud Service.

+++

+++ I moduli headless sono disponibili pubblicamente?

Sì, i moduli headless sono disponibili in AEM Forms as Cloud Service.

+++

+++ I moduli headless richiedono una licenza separata?

No, i moduli headless utilizzano la stessa metrica del valore di licenza, numero di invii dei moduli.

+++

+++ I componenti core e i moduli headless sono disponibili in AEM Forms 6.5?

Sì, sia i componenti core per moduli adattivi che i moduli headless sono disponibili in AEM Forms 6.5 Service Pack 16 e versioni successive.

+++


## Passaggi successivi

Ora che hai imparato a creare i moduli adattivi e a distribuirli su più canali utilizzando moduli headless, puoi provare a mettere in pratica le tue nuove competenze. Buon lavoro, e continua a creare e distribuire esperienze eccezionali con acquisizione dati, per i tuoi utenti finali ovunque si trovano e su larga scala!

## Riferimenti

* [Introduzione ai componenti core per moduli adattivi](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=it)

* [Creare un modulo adattivo utilizzando i componenti core](https://experienceleague.corp.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/creating-adaptive-form-core-components.html?lang=it)

* [Aggiornare lo stile per moduli adattivi basati su componenti core](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/using-themes-in-core-components.html?lang=it)

* [Moduli adattivi headless](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html?lang=it)

* [Utilizzo dello starter kit Headless React](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/get-started/create-and-publish-a-headless-form.html?lang=it)
