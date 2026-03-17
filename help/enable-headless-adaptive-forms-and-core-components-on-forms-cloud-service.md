---
title: Abilitare Forms adattivo headless su AEM Forms as a Cloud Service
description: Guida dettagliata per abilitare i moduli adattivi headless in AEM Forms as a Cloud Service, semplificando la configurazione e l’attivazione nell’ambiente.
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin
level: Beginner, Intermediate
contentOwner: Khushwant Singh
docset: CloudService
hide: true
hidefromtoc: true
exl-id: 7afff771-1296-4162-84c5-c8266b94af2f
source-git-commit: 86129488bec7faed87600a237ac034ca1b601187
workflow-type: tm+mt
source-wordcount: '943'
ht-degree: 6%

---

# Abilitare Forms adattivo headless su AEM Forms as a Cloud Service {#enable-headless-adaptive-forms-on-aem-forms-cloud-service}

L’abilitazione di Headless Adaptive Forms su AEM Forms as a Cloud Service consente di iniziare a creare, pubblicare e distribuire Headless Forms utilizzando le istanze AEM Forms Cloud Service su più canali. Per utilizzare Headless Adaptive Forms è necessario un ambiente abilitato per i Componenti core Forms adattivi.

## Considerazioni

* Quando crei un nuovo programma AEM Forms as a Cloud Service, [Headless Adaptive Forms è già abilitato per i tuoi ambienti](#are-adaptive-forms-core-components-enabled-for-my-environment).

* Se esegui un programma Forms as a Cloud Service precedente in cui i Componenti core sono [non abilitati](#enable-components), prima [aggiungi le dipendenze dei Componenti core Forms adattivi](#enable-headless-adaptive-forms-for-an-aem-forms-as-a-cloud-service-environment) all&#39;archivio Cloud Service. Distribuisci l’archivio aggiornato in ogni ambiente per abilitare i moduli adattivi headless.

* Se l&#39;ambiente Cloud Service ti consente già di [creare moduli adattivi basati su Componenti core](create-a-headless-adaptive-form.md), i moduli adattivi headless verranno abilitati automaticamente. Puoi quindi distribuire tali moduli come esperienze headless a dispositivi mobili, web, app native o a qualsiasi servizio che li richieda.

>[!NOTE]
>
>
> Adobe fornisce un [kit di avvio (app React)](create-and-publish-a-headless-form.md) per Forms adattivo per aiutare gli sviluppatori a iniziare rapidamente con lo sviluppo di Forms adattivo headless, senza abilitare il Forms adattivo headless nell&#39;ambiente AEM Forms as a Cloud Service. Puoi abilitare il Forms adattivo headless in un ambiente Forms as a Cloud Service in un secondo momento, dopo [aver sviluppato moduli headless](create-and-publish-a-headless-form.md).

## Abilitare Headless Adaptive Forms per un ambiente AEM Forms as a Cloud Service

Per abilitare Headless Adaptive Forms per un ambiente AEM Forms as a Cloud Service, effettua le seguenti operazioni, nell’ordine elencato

<!-- Missing image ALT tag -->
![](/help/assets/enable-headless-adaptive-forms-on-aem-forms-cloud-service.png)


## &#x200B;1. Clonare l’archivio Git di AEM Forms as a Cloud Service {#clone-git-repository}

1. Accedi a [Cloud Manager](https://my.cloudmanager.adobe.com/) e seleziona la tua organizzazione e il tuo programma.

1. Passa alla scheda **Pipeline** dalla pagina **Panoramica del programma**.

1. Fai clic sul pulsante **Accedi a dati archivio** per accedere e gestire il tuo archivio Git. La pagina include le seguenti informazioni:

   * URL dell’archivio Git di Cloud Manager.
   * Credenziali dell’archivio Git (nome utente e password), nome utente Git.

   Fare clic su **Genera password** per visualizzare o generare la password.

1. Aprire il terminale o il prompt dei comandi sul computer locale ed eseguire il comando seguente:

   ```Shell
   git clone [Git Repository URL]
   ```

   Quando richiesto, immettere le credenziali. L&#39;archivio viene clonato nel computer locale.


## &#x200B;2. Aggiungere le dipendenze dei componenti core di Forms adattivi all’archivio Git {#add-adaptive-forms-core-components-dependencies}

1. Apri la cartella dell’archivio Git in un editor di codice di testo normale. Ad esempio, Codice VS.
1. Apri il file `[AEM Repository Folder]\pom.xml` per la modifica.
1. Sostituire le versioni dei componenti `core.forms.components.version`, `core.forms.components.af.version` e `core.wcm.components.version` con le versioni specificate nella [documentazione dei componenti core](https://github.com/adobe/aem-core-forms-components). Se il componente non esiste, aggiungi questi componenti.

   ```XML
   <!-- Replace the version with the latest released version at https://github.com/adobe/aem-core-forms-components/tags -->
   
   <properties>
       <core.forms.components.version>2.0.14</core.formscomponents.version>
       <core.forms.components.af.version>2.0.14</core.forms.components.af.version>  
       <core.wcm.components.version>2.21.2</core.wcmcomponents.version>
   </properties>
   ```

   ![Menzionare la versione più recente dei componenti core di Forms](/help/assets/latest-forms-component-version.png)

1. Nella sezione delle dipendenze del file `[AEM Repository Folder]\pom.xml`, aggiungere le dipendenze seguenti e salvare il file.

   ```XML
       <!-- WCM Core Component Examples Dependencies -->
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.apps</artifactId>
               <type>zip</type>
               <version>${core.wcm.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.content</artifactId>
               <type>zip</type>
               <version>${core.wcm.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.config</artifactId>
               <version>${core.wcm.components.version}</version>
               <type>zip</type>
           </dependency>    
           <!-- End of WCM Core Component Examples Dependencies -->
           <!-- Forms Core Component Dependencies -->
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-core</artifactId>
               <version>${core.forms.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-apps</artifactId>
               <version>${core.forms.components.version}</version>
               <type>zip</type>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-af-core</artifactId>
               <version>${core.forms.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-af-apps</artifactId>
               <version>${core.forms.components.version}</version>
               <type>zip</type>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-examples-apps</artifactId>
               <type>zip</type>
               <version>${core.forms.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-examples-content</artifactId>
               <type>zip</type>
               <version>${core.forms.components.version}</version>
           </dependency>
   <!-- End of AEM Forms Core Component Dependencies -->
   ```

1. Apri il file `[AEM Repository Folder]/all/pom.xml` per la modifica. Aggiungere le dipendenze seguenti nella sezione `<embeddeds>` e salvare il file.

   ```XML
   <!-- WCM Core Component Examples Dependencies -->
   
   <!-- inside plugin config of filevault-package-maven-plugin -->  
   <!-- embed wcm core components examples artifacts -->
   
   <embedded>
       <groupId>com.adobe.cq</groupId>
       <artifactId>core.wcm.components.examples.ui.apps</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.cq</groupId>
       <artifactId>core.wcm.components.examples.ui.content</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.cq</groupId>
       <artifactId>core.wcm.components.examples.ui.config</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   <!-- embed forms core components artifacts -->
   <embedded>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-af-apps</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/application/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-af-core</artifactId>
       <target>/apps/${appId}-vendor-packages/application/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-examples-apps</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-examples-content</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   ```

   >[!NOTE]
   >
   >
   >  Sostituisci `${appId}` con il tuo appId.
   >
   >  Per trovare `${appId}`, nel file `[AEM Repository Folder]/all/pom.xml`, cerca il termine `-packages/application/install`. Il testo prima del termine `-packages/application/install` è `${appId}`. Il codice seguente, ad esempio, `myheadlessform` è `${appId}`.
   >
   >   ```
   >             <embedded>
   >                     <groupId>com.myheadlessform</groupId>
   >                     <artifactId>myheadlessform.ui.apps<artifactId>
   >                     <type>zip</type>
   >                   <target>/apps/myheadlessform-packages/application install</target>
   >             </embedded>
   >   ```

1. Nella sezione `<dependencies>` del file `[AEM Repository Folder]/all/pom.xml`, aggiungere le dipendenze seguenti e salvare il file:

   ```XML
           <!-- Other existing dependencies -->
           <!-- wcm core components examples dependencies -->
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.apps</artifactId>
               <type>zip</type>
           </dependency>
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.config</artifactId>
               <type>zip</type>
               </dependency>
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.content</artifactId>
               <type>zip</type>
           </dependency>
               <!-- forms core components dependencies -->
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-af-apps</artifactId>
               <type>zip</type>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-examples-apps</artifactId>
               <type>zip</type>
           </dependency>
               <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-examples-content</artifactId>
               <type>zip</type>
           </dependency>
   ```

1. Apri `[AEM Repository Folder]/ui.apps/pom.xml` per la modifica. Aggiungere la dipendenza `af-core bundle` e salvare il file.

   ```XML
       <dependency>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-af-core</artifactId>
       </dependency>
   ```

   >[!NOTE]
   >
   >Assicurati che i seguenti artefatti dei Componenti core adattivi di Forms non siano inclusi nel progetto.
   >
   > `<dependency>`
   >
   >   `<groupId>com.adobe.aem</groupId>`
   >   `<artifactId>core-forms-components-apps</artifactId>`
   >
   > `</dependency>`
   >
   > e
   >
   > `<dependency>`
   >
   >   `<groupId>com.adobe.aem</groupId>`
   >   `<artifactId>core-forms-components-core</artifactId>`
   >
   > `</dependency>`


1. Salva e chiudi il file.

## &#x200B;3.  Aggiorna il progetto per includere la versione più recente dei Componenti core di Forms:

1. Apri la [cartella dei progetti Archetipo AEM]/pom.xml per la modifica.


1. Salva e chiudi il file.

## &#x200B;4. Eseguire il commit degli aggiornamenti nel repository Git ed eseguire una pipeline per distribuire il repository {#Commit-the-updates-to-your-git-repository}

1. Per eseguire il commit del codice nell’archivio Git:
   1. Aprire il terminale o il prompt dei comandi.
   1. Passa a `[AEM Repository Folder]` ed esegui i seguenti comandi nell&#39;ordine elencato

      ```Shell
      git add pom.xml
      git add all/pom.xml
      git add ui.apps/pom.xml
      git commit -m "Added dependencies for Adaptive Forms Core Components"
      git push origin
      ```

1. Dopo il commit dei file nell&#39;archivio Git, [Esegui la pipeline](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-manager/content/using/code-deployment).

   Una volta eseguita correttamente la pipeline, i componenti core Adaptive Forms vengono abilitati per l’ambiente corrispondente. Inoltre, all’ambiente Forms as a Cloud Service vengono aggiunti un modello Forms adattivo (Componenti core) e un tema Canvas 3.0, che offrono opzioni per personalizzare e creare componenti core basati su Adaptive Forms.


## Domande frequenti {#faq}

### Quali sono i Componenti core? {#core-components}

I [Componenti core](https://experienceleague.adobe.com/it/docs/experience-manager-core-components/using/introduction) sono un insieme di componenti WCM (Web Content Management) standardizzati di AEM che consentono di velocizzare i tempi di sviluppo e ridurre i costi di manutenzione dei siti Web.

### Quali sono tutte le funzionalità aggiunte all’abilitazione dei componenti core? {#core-components-capabilities}

Quando i componenti core Adaptive Forms sono abilitati per il tuo ambiente, all’ambiente vengono aggiunti un modello di modulo adattivo basato su Componenti core vuoto e un tema Canvas 3.0. Dopo aver abilitato i componenti core Forms adattivi per il tuo ambiente, puoi:

* Creazione di componenti core basati su Adaptive Forms.
* Creare modelli di moduli adattivi basati su Componenti core.
* Crea temi personalizzati per i modelli di moduli adattivi basati su Componenti core.
* Distribuisci le rappresentazioni JSON del modulo adattivo basato su componenti core a canali quali dispositivi mobili, web, app native e servizi che richiedono la rappresentazione headless di un modulo.

### I componenti core Forms adattivi sono abilitati per il mio ambiente? {#enable-components}

Per verificare che i componenti core Adaptive Forms siano abilitati per il tuo ambiente:

1. [Clona l&#39;archivio AEM Forms as a Cloud Service](#1-clone-your-aem-forms-as-a-cloud-service-git-repository).

1. Apri il file `[AEM Repository Folder]/all/pom.xml` dell&#39;archivio Git di AEM Forms Cloud Service.

1. Cerca le dipendenze seguenti:

   * core-forms-components-af-core
   * core-forms-components-core
   * core-forms-components-apps
   * core-forms-components-af-apps
   * core-forms-components-examples-apps
   * core-forms-components-examples-content


   ![individua l&#39;artefatto core-forms-components-af-core in all/pom.xml](/help/assets/enable-headless-adaptive-forms-on-aem-forms-cloud-service-locate-core-af-artifact.png)

   Se le dipendenze esistono, i componenti core Adaptive Forms sono abilitati per il tuo ambiente.
