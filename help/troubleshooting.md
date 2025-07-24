---
title: Risoluzione dei problemi di Forms adattivo headless
description: Risoluzione dei problemi di Forms adattivo headless
keywords: headless, modulo adattivo, risoluzione dei problemi
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
hide: false
exl-id: bfb7e688-d2be-4aaa-ac9b-147cbd74b516
source-git-commit: 28792fe1690e68cd301a0de2ce8bff53fae1605f
workflow-type: tm+mt
source-wordcount: '127'
ht-degree: 6%

---

# Risoluzione di problemi

## Impossibile distribuire il progetto Archetipo nell’ambiente di sviluppo locale

### Problema  

Quando si utilizzano i comandi `mvn -PautoInstallPackage clean install` o simili per distribuire un progetto Archetipo AEM, la distribuzione del progetto non riesce.

### Motivo

Il problema può essere dovuto a una versione non supportata o a un&#39;installazione danneggiata di `node.js` o `NPM`.

### Soluzione

1. [rimuovi completamente le installazioni presenti di Node.JS](https://khushwantsehgal.wordpress.com/2022/06/28/how-to-remove-node-js-completely-from-windows-10/) dal tuo ambiente.

1. Installa `node.JS 16.13.0` o versione successiva con `NPM`.

1. Riavviare il computer.


## Esecuzione del comando `mvn clean install` non riuscita

### Problema  

Quando si utilizzano i comandi `mvn clean install` o simili per distribuire un progetto Archetipo AEM, l&#39;esecuzione del comando non riesce.

### Motivo

Può accadere se Git non è installato.

### Soluzione

Scarica e installa la [versione più recente di Git](https://git-scm.com/downloads). Se sei un nuovo utente di Git, vedi [Installazione di Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).
