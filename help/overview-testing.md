---
title: Panoramica dei moduli adattivi headless AEM
description: AEM Forms Headless Adaptive Forms fornisce un modo rapido ed efficiente per creare moduli per varie piattaforme, tra cui CMS headless o headful, applicazioni React, applicazioni a pagina singola (SPA), app web, app mobili, Amazon Alexa, Google Assistant, WhatsApp e altro ancora. Con Headless Adaptive Forms puoi semplificare la procedura di creazione dei moduli, semplificando così la raccolta dei dati dagli utenti su diversi dispositivi e piattaforme.
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: CMS headless, moduli adattivi, interfaccia utente headless, CMS headful, assistenti vocali, alexa, chatbot, architettura WhatsApp
hide: true
hidefromtoc: true
exl-id: f6a383ea-684b-479d-a15f-8ebced75635e
source-git-commit: 1f70e2bb0e5f12e8ee5d948ef1d3cd2935f2274f
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 13%

---

# Introduzione

Adobe Experience Manager (AEM) Headless Adaptive Forms è una soluzione per la creazione e la gestione di moduli web headless all’interno della piattaforma Adobe Experience Manager. Questa funzione consente alle organizzazioni di creare, pubblicare e gestire moduli interattivi a cui è possibile accedere e con cui interagire tramite API, anziché tramite un’interfaccia utente grafica tradizionale. Il Forms adattivo headless dell’AEM offre maggiore flessibilità e scalabilità nello sviluppo e nella distribuzione dei moduli, nonché una migliore esperienza utente grazie alla possibilità di adattare la progettazione e la funzionalità dei moduli alle esigenze specifiche. Utilizzando le funzionalità dell’AEM e la tecnologia headless, questa soluzione fornisce una piattaforma solida per la creazione, la gestione e l’implementazione di moduli web per vari casi d’uso e applicazioni.

![Genera ed esegui il rendering nativo di un modulo in qualsiasi sito Web, applicazione o interazione non visiva](/help/assets/headless-forms-for-any-device.jpeg)

I moduli adattivi headless consentono di:

* creare moduli multi-canale di alta qualità nel linguaggio di programmazione desiderato
* integrare in modo nativo i moduli nelle app desktop e per dispositivi mobili, nei siti web e nelle applicazioni chat
* riutilizzare i componenti proprietari dell’interfaccia utente con le applicazioni di Forms
* sfrutta la potenza di [Adobe Experience Manager Forms](https://experienceleague.adobe.com/docs/experience-manager-65/forms/getting-started/introduction-aem-forms.html)

Inoltre, puoi sviluppare i tuoi componenti per eseguire il rendering di un modulo utilizzando qualsiasi framework di interfaccia utente e linguaggio di programmazione a tua scelta. Puoi anche utilizzare i componenti React disponibili come predefiniti per il rendering di un modulo adattivo headless.

<!-- 

## Key Features

<table style="width:100%;">
  <tr>
    <td style="width:33.33%;">
      <div style="width: 250px; border: 1px solid #ccc; border-radius: 8px;">
        <img src="/help/assets/01-overview-responsive-forms.jpeg" alt="Card Image 1" style="width:33.33; height: auto;">
        <div style="padding: 20px;">
          <h2 style="margin-top: 0;">Responsive Forms</h2>
          <p>The adaptive form feature enables you to create a single source for a form that automatically sizes and re-flows on mobile devices.</p>
        </div>
      </div>
    </td>
    <td style="width:33.33%;">
      <div style="width: 250px; border: 1px solid #ccc; border-radius: 8px; ">
        <img src="/help/assets/01-overview-responsive-forms.jpeg" alt="Card Image 1" style="width:33.33; height: auto;">
        <div style="padding: 20px;">
          <h2 style="margin-top: 0;">Communication API</h2>
          <p>The adaptive form feature enables you to create a single source for a form that automatically sizes and re-flows on mobile devices.</p>
        </div>
      </div>
    </td>
    <td style="width:33.33%;">
      <div style="width: 250px; border: 1px solid #ccc; border-radius: 8px; ">
        <img src="/help/assets/02-overview-backend-systems.jpeg" alt="Card Image 2" style="width:33.33; height: auto;">
        <div style="padding: 20px;">
          <h2 style="margin-top: 0;">Business Process Management</h2>
          <p>Integrate RDBMS, OData, Or Microsoft SOAP services, as well as protocols like Swagger 2.0 to connect to just about anything.</p>
        </div>
      </div>
    </td>
  </tr>
  <tr>
    <td style="width:33.33%;">
      <div style="width: 250px; border: 1px solid #ccc; border-radius: 8px; ">
        <img src="/help/assets/03-overview-save-and-resume.jpeg" alt="Card Image 3" style="width:33.33; height: auto;">
        <div style="padding: 20px;">
          <h2 style="margin-top: 0;">Save and resume forms</h2>
          <p>Allow clients to save in-progress forms and return later to complete them, even on another device.</p>
        </div>
      </div>
    </td>
    <td style="width:33.33%;">
      <div style="width: 250px; border: 1px solid #ccc; border-radius: 8px; ">
        <img src="/help/assets/04-overview-search.jpeg" alt="Card Image 1" style="width:33.33; height: auto;">
        <div style="padding: 20px;">
          <h2 style="margin-top: 0;">Forms Search and Discovery</h2>
          <p>Let customers easily find relevant forms based on a simple search query, tags, filters, and even geolocation — on any device through a personalized portal, with or without authentication.
          </p>
        </div>
      </div>
    </td>
      <td style="width:33.33%;">
      <div style="width: 250px; border: 1px solid #ccc; border-radius: 8px; ">
        <img src="/help/assets/04-overview-search.jpeg" alt="Card Image 1" style="width:33.33; height: auto;">
        <div style="padding: 20px;">
          <h2 style="margin-top: 0;">Forms Search and Discovery</h2>
          <p>Let customers easily find relevant forms based on a simple search query, tags, filters, and even geolocation — on any device through a personalized portal, with or without authentication.
          </p>
        </div>
      </div>
    </td>
  </tr>
  <tr>
    <td style="width:33.33%;">
      <div style="width: 250px; border: 1px solid #ccc; border-radius: 8px; ">
        <img src="/help/assets/05-overview-analytics.jpeg" alt="Card Image 2" style="width:33.33; height: auto;">
        <div style="padding: 20px;">
          <h2 style="margin-top: 0;">Form analytics and reporting</h2>
          <p>Out-of-the-box, customizable dashboards make it easy to apply analytics to forms to gain insight for actionable areas of improvement.</p>
        </div>
      </div>
    </td>
    <td style="width:33.33%;">
      <div style="width: 250px; border: 1px solid #ccc; border-radius: 8px; ">
        <img src="/help/assets/06-overview-business-process.jpeg" alt="Card Image 3" style="width:33.33; height: auto;">
        <div style="padding: 20px;">
          <h2 style="margin-top: 0;">Business Process Management</h2>
          <p>Route application submissions through customized workflows and a centralized dashboard for review, approval, and digital signatures by back-office employees — even when employees are on the go on a mobile device.
          </p>
        </div>
      </div>
    </td>
  </tr>
</table>




<div style="display: flex; flex-wrap: wrap; justify-content: space-between; margin: 20px;">
    <div style="width: 30%; margin-bottom: 20px; border: 1px solid #ccc; border-radius: 5px; padding: 20px; box-sizing: border-box;">
        <img src="/help/assets/01-overview-responsive-forms.jpeg" alt="Icon 1" style="width: 50px; height: 50px;">
        <h2 style="margin-top: 10px;">Heading 1</h2>
        <p>Description 1</p>
    </div>
    <div style="width: 30%; margin-bottom: 20px; border: 1px solid #ccc; border-radius: 5px; padding: 20px; box-sizing: border-box;">
        <img src="/help/assets/02-overview-backend-systems.jpeg" alt="Icon 2" style="width: 50px; height: 50px;">
        <h2 style="margin-top: 10px;">Heading 2</h2>
        <p>Description 2</p>
    </div>
    <div style="width: 30%; margin-bottom: 20px; border: 1px solid #ccc; border-radius: 5px; padding: 20px; box-sizing: border-box;">
        <img src="/help/assets/03-overview-save-and-resume.jpeg" alt="Icon 3" style="width: 50px; height: 50px;">
        <h2 style="margin-top: 10px;">Heading 3</h2>
        <p>Description 3</p>
    </div>
        <div style="width: 30%; margin-bottom: 20px; border: 1px solid #ccc; border-radius: 5px; padding: 20px; box-sizing: border-box;">
        <img src="/help/assets/04-overview-search.jpeg" alt="Icon 1" style="width: 50px; height: 50px;">
        <h2 style="margin-top: 10px;">Heading 1</h2>
        <p>Description 1</p>
    </div>
    <div style="width: 30%; margin-bottom: 20px; border: 1px solid #ccc; border-radius: 5px; padding: 20px; box-sizing: border-box;">
        <img src="/help/assets/05-overview-analytics.jpeg" alt="Icon 2" style="width: 50px; height: 50px;">
        <h2 style="margin-top: 10px;">Heading 2</h2>
        <p>Description 2</p>
    </div>
    <div style="width: 30%; margin-bottom: 20px; border: 1px solid #ccc; border-radius: 5px; padding: 20px; box-sizing: border-box;">
        <img src="/help/assets/06-overview-business-process.jpeg" alt="Icon 3" style="width: 50px; height: 50px;">
        <h2 style="margin-top: 10px;">Heading 3</h2>
        <p>Description 3</p>
    </div>
    <!-- Add more cards as needed -->
</div>




<div style="display: flex; flex-wrap: wrap; justify-content: space-between; margin: 20px;">
    <div style="width: 30%; margin-bottom: 20px; border: 1px solid #ccc; border-radius: 5px; padding: 20px; box-sizing: border-box;">
        <img src="/help/assets/01-overview-responsive-forms.jpeg" alt="Immagine 1" style="width: 100%; border-radius: 5px;">
        <h2 style="margin-top: 10px;">Intestazione 1</h2>
        <p>Descrizione 1</p>
    </div>
    <div style="width: 30%; margin-bottom: 20px; border: 1px solid #ccc; border-radius: 5px; padding: 20px; box-sizing: border-box;">
        <img src="/help/assets/02-overview-backend-systems.jpeg" alt="Immagine 2" style="width: 100%; border-radius: 5px;">
        <h2 style="margin-top: 10px;">Intestazione 2</h2>
        <p>Descrizione 2</p>
    </div>
    <div style="width: 30%; margin-bottom: 20px; border: 1px solid #ccc; border-radius: 5px; padding: 20px; box-sizing: border-box;">
        <img src="/help/assets/03-overview-save-and-resume.jpeg" alt="Immagine 3" style="width: 100%; border-radius: 5px;">
        <h2 style="margin-top: 10px;">Intestazione 3</h2>
        <p>Descrizione 3</p>
    </div>
    <!-- Add more cards as needed -->
</div>

-->

## Chi può utilizzare moduli adattivi headless? {#who-can-use-headless-adaptive-forms}

Qualsiasi sviluppatore front-end che ha familiarità con i moderni framework JavaScript può utilizzare moduli adattivi headless. Gli sviluppatori possono sfruttare la loro esperienza esistente in linguaggi front-end come React per creare esperienze di acquisizione dati di classe enterprise.

Per sviluppare moduli adattivi headless non è necessaria alcuna conoscenza preventiva di Adobe Experience Manager.

<!-- 
## How to join the early adopter program? {#how-to-join-early-adopter-forms}

The service is available for AEM Forms as a Cloud Service and AEM 6.5.16.0 Forms or later On-Premise term customers and Adobe-Managed Service enterprise customers. Send an email to [headlessadaptiveforms@adobe.com](mailto:headlessadaptiveforms@adobe.com) from your official email ID to join the early adopter program. 

-->
