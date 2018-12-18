---
title: "Creare un ambiente di sviluppo Node.js con i contenitori usando Kubernetes nel cloud - Passaggio 3: Creare un'app Web ASP.NET | Microsoft Docs"
author: johnsta
ms.author: johnsta
ms.date: 02/20/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: Sviluppo rapido Kubernetes con contenitori e microservizi in Azure
keywords: Docker, Kubernetes, Azure, AKS, servizio contenitore di Azure, contenitori
manager: ghogen
ms.openlocfilehash: 26d6753bf17b459c33cd11c46186d272d477fe10
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2018
---
# <a name="get-started-on-connected-environment-with-nodejs"></a>Introduzione a Connected Environment con Node.js

Passaggio precedente: [Creare un ambiente di sviluppo Kubernetes in Azure](get-started-nodejs-02.md)

## <a name="create-a-nodejs-web-app"></a>Creare un'app Web Node.js
Scaricare il codice da GitHub: passare a https://github.com/Azure/vsce e selezionare **Clone or download** (Clona o scarica) per scaricare il repository GitHub nell'ambiente locale. Il codice per questa guida è disponibile in `vsce/samples/nodejs/getting-started/webfrontend`.

[!INCLUDE[](includes/vsce-init.md)]

[!INCLUDE[](includes/ensure-env-created.md)]

[!INCLUDE[](includes/build-and-run-in-k8s-cli.md)]

## <a name="update-a-content-file"></a>Aggiornare un file di contenuto
Connected Environment non significa semplicemente la possibilità di eseguire il codice in Kubernetes, ma si tratta di riuscire a vedere applicate rapidamente e in modo iterativo le modifiche al codice in un ambiente Kubernetes nel cloud.

1. Individuare il file `./public/index.html` e apportare una modifica al codice HTML. Ad esempio, modificare il colore di sfondo della pagina impostando una sfumatura di blu:

```html
<body style="background-color: #95B9C7; margin-left:10px; margin-right:10px;">
```

2. Salvare il file. Alcuni momenti più tardi, nella finestra del terminale verrà visualizzato un messaggio che informa che è stato aggiornato un file nel contenitore in esecuzione.
1. Passare al browser e aggiornare la pagina. Dovrebbe essere visibile il colore aggiornato.

Cosa è successo? Le modifiche apportate ai file di contenuto, come HTML e CSS, non richiedono il riavvio del processo Node.js, quindi un comando `vsce up` attivo sincronizzerà automaticamente qualsiasi file di contenuto modificato direttamente nel contenitore in esecuzione in Azure, offrendo così un modo rapido per visualizzare le modifiche al contenuto.

### <a name="test-from-a-mobile-device"></a>Eseguire test da un dispositivo mobile
Se si apre l'app Web in un dispositivo mobile, si noterà che l'interfaccia utente non viene visualizzata correttamente in un dispositivo di piccole dimensioni.

Per risolvere questo problema, verrà aggiunto un tag META `viewport`:
1. Aprire il file `./public/index.html`
1. Aggiungere un tag META `viewport` nell'elemento `head` esistente:

```html
<head>
    <!-- Add this line -->
    <meta name="viewport" content="width=device-width, initial-scale=1">
</head>
```

1. Salvare il file.
1. Aggiornare il browser del dispositivo. Il rendering dell'app Web dovrebbe essere ora corretto. 

Questo è un esempio di come alcuni problemi semplicemente non vengono trovati fino a quando non si eseguono test nei dispositivi in cui è previsto l'uso di un'app. Con Visual Studio Connected Environment è possibile eseguire rapidamente iterazioni del codice e convalidare le modifiche apportate nei dispositivi di destinazione.

## <a name="update-a-code-file"></a>Aggiornare un file di codice
L'aggiornamento dei file di codice sul lato server richiede un po' più di lavoro, perché un'app Node.js deve essere riavviata.

1. Nella finestra del terminale premere `Ctrl+C` (per arrestare `vsce up`).
1. Aprire il file di codice denominato `server.js` e modificare il messaggio di saluto del servizio: 

```javascript
res.send('Hello from webfrontend running in Azure!');
```

3. Salvare il file.
1. Eseguire `vsce up` nella finestra del terminale. 

Viene così ricompilata l'immagine del contenitore e ridistribuito il grafico Helm. Ricaricare la pagina del browser per visualizzare le modifiche del codice applicate.


Esiste però un *metodo ancora più rapido* per lo sviluppo del codice, che verrà presentato nella prossima sezione. 
> [!div class="nextstepaction"]
> [Eseguire il debug di un contenitore in Kubernetes](get-started-nodejs-04.md)
