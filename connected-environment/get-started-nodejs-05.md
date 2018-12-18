---
title: 'Creare un ambiente di sviluppo Node.js con i contenitori usando Kubernetes nel cloud - Passaggio 5: Chiamare un altro contenitore | Microsoft Docs'
author: johnsta
ms.author: johnsta
ms.date: 02/20/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: Sviluppo rapido Kubernetes con contenitori e microservizi in Azure
keywords: Docker, Kubernetes, Azure, AKS, servizio contenitore di Azure, contenitori
manager: ghogen
ms.openlocfilehash: 5b7065714475ee700fb1a04502a50a4fce0b0e8d
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2018
---
# <a name="get-started-on-connected-environment-with-nodejs"></a>Introduzione a Connected Environment con Node.js

Passaggio precedente: [Eseguire il debug di un contenitore in Kubernetes](get-started-nodejs-04.md)

In questa sezione verrà creato un secondo servizio, `mywebapi`, chiamato da `webfrontend`. Ogni servizio verrà eseguito in contenitori separati. Il debug verrà quindi eseguito su entrambi i contenitori.

![](media/multi-container.png)

## <a name="open-sample-code-for-mywebapi"></a>Aprire il codice di esempio per *mywebapi*
Dovrebbe essere già disponibile il codice di esempio per `mywebapi` per questa guida in una cartella denominata `vsce/samples`. In caso contrario, passare a https://github.com/Azure/vsce e selezionare **Clone or download** (Clona o scarica) per scaricare il repository di GitHub. Il codice per questa sezione è in `vsce/samples/nodejs/getting-started/mywebapi`.

## <a name="run-mywebapi"></a>Eseguire *mywebapi*
1. Aprire la cartella `mywebapi` in una *finestra di Visual Studio Code separata*.
1. Premere F5 e attendere che il servizio venga compilato e distribuito. Al termine dell'operazione verrà visualizzata la barra di debug di Visual Studio Code.
1. Prendere nota dell'URL dell'endpoint, che sarà simile a http://localhost:\<numeroporta\>. **Suggerimento: la barra di stato di Visual Studio Code visualizzerà un URL selezionabile.** Potrebbe sembrare che il contenitore sia in esecuzione in locale, ma in realtà è in esecuzione nell'ambiente di sviluppo in Azure. L'indirizzo localhost viene usato perché `mywebapi` non ha definito alcun endpoint pubblico ed è possibile accedervi solo dall'interno dell'istanza di Kubernetes. Per comodità e per semplificare l'interazione con il servizio privato dal computer locale, Connected Environment crea un tunnel SSH temporaneo al contenitore in esecuzione in Azure.
1. Quando `mywebapi` è pronto, aprire il browser sull'indirizzo localhost. Dovrebbe essere visualizzata una risposta dal servizio `mywebapi` ("Hello from mywebapi").


## <a name="make-a-request-from-webfrontend-to-mywebapi"></a>Effettuare una richiesta da *webfrontend* a *mywebapi*
Si scriverà ora codice in `webfrontend` per effettuare una richiesta a `mywebapi`.
1. Passare alla finestra di Visual Studio Code per `webfrontend`.
1. Aggiungere queste righe di codice all'inizio di `server.js`:
```javascript
var request = require('request');
var propagateHeaders = require('./propagateHeaders');
```

3. *Sostituire* il codice per il gestore GET `/api`. Quando si gestisce una richiesta, questa a sua volta effettua una chiamata a `mywebapi` e quindi restituisce i risultati da entrambi i servizi.

```javascript
app.get('/api', function (req, res) {
    request({
        uri: 'http://mywebapi',
        headers: propagateHeaders.from(req) // propagate headers to outgoing requests
    }, function (error, response, body) {
        res.send('Hello from webfrontend and ' + body);
    });
});
```

Si noti come viene usata l'individuazione del servizio DNS di Kubernetes per fare riferimento al servizio come `http://mywebapi`. **Il codice nell'ambiente di sviluppo verrà eseguito esattamente come nell'ambiente di produzione**.

L'esempio di codice precedente usa un modulo helper denominato `propagateHeaders`. Questo helper è stato aggiunto alla cartella del codice al momento dell'esecuzione di `vsce init`. La funzione `propagateHeaders.from()` propaga intestazioni specifiche da un oggetto http.IncomingMessage esistente in un oggetto intestazioni per una richiesta in uscita. Si vedrà più avanti come questa tecnica favorisca un'esperienza di sviluppo più produttiva negli scenari di lavoro in team.


## <a name="debug-across-multiple-services"></a>Eseguire il debug tra più servizi
1. A questo punto, `mywebapi` dovrebbe essere ancora in esecuzione con il debugger collegato. In caso contrario, premere F5 nel progetto `mywebapi`.
1. Impostare un punto di interruzione nel gestore `/` GET predefinito.
1. Nel progetto `webfrontend` impostare un punto di interruzione prima di inviare una richiesta GET a `http://mywebapi`.
1. Premere F5 nel progetto `webfrontend`.
1. Aprire l'app Web ed eseguire il codice un'istruzione alla volta in entrambi i servizi. L'app Web dovrebbe visualizzare un messaggio concatenato dai due servizi: "Hello from webfrontend and Hello from mywebapi".


Le operazioni per questo passaggio sono completate. È ora disponibile un'applicazione multi-contenitore in cui ogni contenitore può essere sviluppato e distribuito separatamente.

> [!div class="nextstepaction"]
> [Informazioni sullo sviluppo in team](get-started-nodejs-06.md)
