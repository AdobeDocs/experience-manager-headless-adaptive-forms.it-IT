---
title: Abilitare Headless Adaptive Forms su AEM Forms as a Cloud Service
seo-title: Step-by-Step Guide for enabling Headless Adaptive Forms on AEM Forms as a Cloud Service
description: Scopri come abilitare i moduli adattivi headless su AEM Forms as a Cloud Service con la nostra guida dettagliata. Il nostro tutorial illustra la procedura per abilitare facilmente questa potente funzione per il tuo ambiente AEM Forms.
seo-description: Learn how to enable headless adaptive forms on AEM Forms as a Cloud Service with our step-by-step guide. Our tutorial walks you through the process, making it easy to enable this powerful feature for your AEM Forms environment.
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
source-git-commit: 999c3d092d03d7a82363bc94ce79ceb33bf0df7e
workflow-type: tm+mt
source-wordcount: '914'
ht-degree: 0%

---

# Abilitare Headless Adaptive Forms su AEM Forms as a Cloud Service {#enable-headless-adaptive-forms-on-aem-forms-cloud-service}

L’abilitazione di Headless Adaptive Forms su AEM Forms as a Cloud Service consente di iniziare a creare, pubblicare e distribuire Headless Forms utilizzando le istanze di Cloud Service AEM Forms su più canali. Per utilizzare Headless Adaptive Forms è necessario un ambiente abilitato per i Componenti core Forms adattivi.

## Considerazioni

* Quando crei un nuovo programma AEM Forms as a Cloud Service, [Headless Adaptive Forms è già abilitato per i tuoi ambienti](#are-adaptive-forms-core-components-enabled-for-my-environment).

* Se hai un programma Forms as a Cloud Service precedente in cui i Componenti core sono [non abilitati](#enable-components), puoi [aggiungere le dipendenze dei Componenti core Forms adattivi](#enable-headless-adaptive-forms-for-an-aem-forms-as-a-cloud-service-environment) al tuo archivio AEM as a Cloud Service e distribuire l&#39;archivio negli ambienti di Cloud Service per abilitare Forms adattivo headless.

* Se l&#39;ambiente di Cloud Service esistente offre l&#39;opzione per [creare Forms adattivo basato su Componenti core](create-a-headless-adaptive-form.md), i Forms adattativi headless sono già abilitati per l&#39;ambiente e puoi distribuire Forms adattivo basato su Componenti core come moduli headless a canali quali dispositivi mobili, web, app native e servizi che richiedono una rappresentazione headless di Forms adattivo.


>[!NOTE]
>
>
> Adobe fornisce il [kit di avvio adattivo di Forms (app React)](create-and-publish-a-headless-form.md) per aiutare gli sviluppatori a iniziare rapidamente con lo sviluppo di Forms adattivo headless, senza abilitare il Forms adattivo headless nell&#39;ambiente as a Cloud Service AEM Forms. Puoi abilitare il Forms adattivo headless in un ambiente as a Cloud Service Forms in un secondo momento dopo un [intervento pratico rapido con lo sviluppo di moduli headless](create-and-publish-a-headless-form.md).

## Abilitare Headless Adaptive Forms per un ambiente AEM Forms as a Cloud Service

Per abilitare Headless Adaptive Forms per un ambiente AEM Forms as a Cloud Service, effettua le seguenti operazioni, nell’ordine elencato


![](/help/assets/enable-headless-adaptive-forms-on-aem-forms-cloud-service.png)


## 1. Clonare l’archivio as a Cloud Service Git di AEM Forms {#clone-git-repository}

1. Accedi a [Cloud Manager](https://my.cloudmanager.adobe.com/) e seleziona la tua organizzazione e il tuo programma.

1. Passa alla scheda **Pipeline** dalla pagina **Panoramica del programma**, quindi fai clic sul pulsante **Accedi a dati archivio** per accedere e gestire il tuo archivio Git. La pagina include le seguenti informazioni:

   * URL dell’archivio Git di Cloud Manager.
   * Credenziali dell’archivio Git (nome utente e password), nome utente Git.

   Fare clic su **Genera password** per visualizzare o generare la password.

1. Aprire il terminale o il prompt dei comandi sul computer locale ed eseguire il comando seguente:

   ```Shell
   git clone [Git Repository URL]
   ```

   Quando richiesto, immettere le credenziali. L&#39;archivio viene clonato nel computer locale.


## 2. Aggiungere all’archivio Git le dipendenze dei Componenti core adattivi di Forms {#add-adaptive-forms-core-components-dependencies}

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

## 3. Aggiorna il progetto per includere la versione più recente dei Componenti core di Forms:

1. Apri [Cartella progetti Archetipo AEM]/pom.xml per la modifica.


1. Salva e chiudi il file.

## 4. Eseguire il commit degli aggiornamenti nel repository Git ed eseguire la pipeline per distribuire il repository {#Commit-the-updates-to-your-git-repository}

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

1. Dopo il commit dei file nell&#39;archivio Git, [Esegui la pipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html?lang=it).

   Una volta completata l’esecuzione della pipeline, i componenti core Adaptive Forms vengono abilitati per l’ambiente corrispondente. All’ambiente Forms as a Cloud Service vengono inoltre aggiunti un modello Forms adattivo (Componenti core) e un tema Canvas 3.0, che offrono opzioni per personalizzare e creare componenti core basati su Adaptive Forms.


## Domande frequenti {#faq}

### Cosa sono i Componenti core? {#core-components}

I [Componenti core](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=it) sono un insieme di componenti WCM (Web Content Management) standardizzati per l&#39;AEM che consentono di velocizzare i tempi di sviluppo e ridurre i costi di manutenzione dei siti Web.

### Quali sono tutte le funzionalità aggiunte all’abilitazione dei componenti core? {#core-components-capabilities}

Quando i componenti core Adaptive Forms sono abilitati per il tuo ambiente, all’ambiente vengono aggiunti un modello di modulo adattivo basato su Componenti core vuoto e un tema Canvas 3.0. Dopo aver abilitato i componenti core Forms adattivi per il tuo ambiente, puoi:

* Creazione di componenti core basati su Adaptive Forms.
* Creare modelli di moduli adattivi basati su Componenti core.
* Crea temi personalizzati per i modelli di moduli adattivi basati su Componenti core.
* Distribuisci le rappresentazioni JSON del modulo adattivo basato su componenti core a canali quali dispositivi mobili, web, app native e servizi che richiedono la rappresentazione headless di un modulo.

### I componenti core Forms adattivi sono abilitati per il mio ambiente? {#enable-components}

Per verificare che i componenti core Adaptive Forms siano abilitati per il tuo ambiente:

1. [Clona l&#39;archivio as a Cloud Service di AEM Forms](#1-clone-your-aem-forms-as-a-cloud-service-git-repository).

1. Apri il file `[AEM Repository Folder]/all/pom.xml` dell&#39;archivio Git del Cloud Service AEM Forms.

1. Cerca le dipendenze seguenti:

   * core-forms-components-af-core
   * core-forms-components-core
   * core-forms-components-apps
   * core-forms-components-af-apps
   * core-forms-components-examples-apps
   * core-forms-components-examples-content


   ![individua l&#39;artefatto core-forms-components-af-core in all/pom.xml](/help/assets/enable-headless-adaptive-forms-on-aem-forms-cloud-service-locate-core-af-artifact.png)

   Se le dipendenze esistono, i componenti core Adaptive Forms sono abilitati per il tuo ambiente.
