---
title: Risoluzione dei problemi di Forms adattivo headless
description: Risoluzione dei problemi di Forms adattivo headless
keywords: headless, modulo adattivo, risoluzione dei problemi
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
index: true
exl-id: bfb7e688-d2be-4aaa-ac9b-147cbd74b516
TQID: https://experienceleague.adobe.com/yjO3VhNmqIAyfnD7daHB7eAEUNmaAjnUgEm0fHc1ArY
product_v2: id: e8f6de9b-cf88-4405-8d10-15efa08c230eid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 12f711845becc93305717fb0c95e82355a8e97a5
workflow-type: tm+mt
source-wordcount: 152
ht-degree: 7%

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
