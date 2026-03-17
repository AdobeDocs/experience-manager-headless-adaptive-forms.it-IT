---
title: Guida introduttiva di Headless Adaptive Forms
description: Guida introduttiva di Headless Adaptive Forms
keywords: modulo adattivo, tutorial, headless
hide: true
source-git-commit: 86129488bec7faed87600a237ac034ca1b601187
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---


# Guida introduttiva di Headless Adaptive Forms

Questa esercitazione fornisce un framework end-to-end per creare un modulo adattivo headless. Il tutorial è organizzato in un caso d’uso e più guide. Ogni guida ti aiuta ad apprendere e aggiungere nuove funzioni al modulo adattivo headless creato in questa esercitazione. Hai un modulo adattivo headless funzionante dopo ogni guida. Al termine di questa esercitazione, dovresti essere in grado di effettuare le seguenti operazioni:

* Creare un modulo adattivo headless
* Aggiungere regole business al modulo
* Utilizza l’interfaccia utente dei materiali di Google per assegnare uno stile al modulo
* Precompilare il modulo
* Incorporare il modulo in una pagina Web

Scoprirai anche l’architettura, gli artefatti disponibili e la struttura JSON dei moduli adattivi headless.

**Il percorso inizia con l&#39;apprendimento del caso d&#39;uso**:

Raya Tan, membro del Dipartimento degli Esteri di un paese noto per le sue bellezze naturali e per la sua fiorente economia del turismo, supervisiona la distribuzione dei visti ai turisti. Questi moduli sono disponibili sul sito web del dipartimento, sulle app native per dispositivi mobili e in formato PDF, con diverse opzioni linguistiche tra cui i turisti possono scegliere. Tuttavia, la gestione e la scalabilità di questi moduli su piattaforme e tecnologie diverse può essere problematica.

Per migliorare l&#39;efficienza e la flessibilità della procedura di richiesta del visto, il Dipartimento degli affari esteri ha deciso di adottare un approccio ai moduli adattativi headless. Questa architettura disaccoppiata separa il front-end dal back-end, consentendo una maggiore personalizzazione e scalabilità. Il reparto pianifica l’utilizzo dei componenti React dell’interfaccia utente di Google Material per migliorare l’esperienza utente dei moduli. Utilizzerà anche funzionalità back-end come le seguenti:

* Firme digitali
* Integrazione dei dati
* Gestione dei processi aziendali
* Documento record
* Analisi dell’utilizzo

La forma più popolare tra i turisti è il modulo &quot;Contattaci&quot;, che viene utilizzato per porre varie domande e richieste. Di conseguenza, il Dipartimento degli affari esteri ha scelto di iniziare ad applicare con questo modulo l’approccio ai moduli adattivi headless. Questa esercitazione ti guida attraverso il processo di creazione del modulo Contattaci utilizzando questa nuova architettura. Il risultato finale è simile al seguente:

![Contatta il modulo adattivo headless per gli Stati Uniti](assets/contact-us-headless-adaptive-forms.png)