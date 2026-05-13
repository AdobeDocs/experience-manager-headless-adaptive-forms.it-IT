---
title: Estensione del codice Visual Studio per moduli adattivi headless
description: Estensione del codice Visual Studio per moduli adattivi headless
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: headless, moduli adattivi, estensione codice Visual Studio
index: true
exl-id: 11960e91-6c09-48d4-9d57-37537f808cd4
TQID: https://experienceleague.adobe.com/sf8qkVgbwMf2CGDsATHRYzq6idFQNFv3Os89oiCoiLU
product_v2:
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
source-git-commit: 12f711845becc93305717fb0c95e82355a8e97a5
workflow-type: tm+mt
source-wordcount: 231
ht-degree: 0%

---

# Estensione Microsoft Visual Studio Code per moduli adattivi headless

Se si utilizza Microsoft® Visual Studio Code come IDE (Integrated Development Environment), è possibile utilizzare l&#39;estensione Adaptive Forms per Microsoft Visual Studio Code. L’estensione:

* Aggiunge funzionalità IntelliSense per Forms adattivo a Visual Studio Code.
* Aiuta a convalidare e completare automaticamente la sintassi JSON per i componenti dei moduli adattivi headless.
* Naviga facilmente nella struttura di un modulo adattivo headless tramite un pannello.
* Aiuta a tradurre un modulo adattivo headless.

<!-- 

The extension o easily navigate the structure 

Adobe provides an extension for Microsoft&reg; Visual Studio Code to make it easier for you to navigate structure and develop Headless adaptive forms in Visual Studio Code. The extension adds Adaptive Forms related IntelliSense capabilities and helps auto-complete Headless adaptive forms JSON syntax. It also adds a panel, titled Forms Tree, to help navigate structure of Headless adaptive form. 

-->

## Prerequisiti

* Scaricare e installare [Microsoft Visual Studio Code 1.62.0 o versione successiva](https://code.visualstudio.com/docs/supporting/FAQ#_how-do-i-find-the-version). Se è installata una versione precedente o non è installata alcuna versione, scaricare la versione più recente dal [sito Web Microsoft](https://code.visualstudio.com/docs/setup/setup-overview). Per utilizzare Visual Studio dalla riga di comando in Apple macOS, vedere [Avvio dalla riga di comando](https://code.visualstudio.com/docs/setup/mac#_launching-from-the-command-line).
* Scarica l&#39;estensione [Adaptive Forms Builder](/help/assets/adaptive-form-builder-0.12.0.vsix).

## Installare l’estensione

1. Apri il prompt dei comandi e passa alla directory contenente il file di estensione scaricato, *adaptive-form-builder-[version].vsix*.

1. Esegui il comando seguente per installare l’estensione:

   `code -–install-extension adaptive-form-builder-0.12.0.vsix`

   <br>

   ![Installazione dell&#39;estensione](/help/assets/install-extension.png)


   Per informazioni sui file con estensione vsix, vedere [Guida in linea di Microsoft Visual Studio Code](https://code.visualstudio.com/docs/configure/extensions/extension-marketplace#_install-from-a-vsix).
