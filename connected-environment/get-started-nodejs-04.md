---
title: 'Creare un ambiente di sviluppo Node.js con i contenitori usando Kubernetes nel cloud - Passaggio 4: Eseguire il debug di un contenitore in Kubernetes | Microsoft Docs'
author: johnsta
ms.author: johnsta
ms.date: 02/20/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: Sviluppo rapido Kubernetes con contenitori e microservizi in Azure
keywords: Docker, Kubernetes, Azure, AKS, servizio contenitore di Azure, contenitori
manager: ghogen
ms.openlocfilehash: 8dca016f3a3feb2d1fb10a80695b82e531e48a74
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2018
---
# <a name="get-started-on-connected-environment-with-nodejs"></a>Introduzione a Connected Environment con Node.js

Passaggio precedente: [Creare un contenitore Node.js in Kubernetes](get-started-nodejs-03.md)

[!INCLUDE[](includes/debug-intro.md)]

[!INCLUDE[](includes/init-debug-assets-vscode.md)]


## <a name="select-the-vsce-debug-configuration"></a>Selezionare la configurazione di debug VSCE
1. Per aprire la visualizzazione di debug, fare clic sull'icona Debug nella **barra attività** sul lato di Visual Studio Code.
1. Selezionare **Avvia programma (VSCE)** come configurazione di debug attiva.

![](media/debug-configuration-nodejs.png)

> [!Note]
> Se non vengono visualizzati comandi di Connected Environment nel riquadro comandi, assicurarsi di aver [installato l'estensione di Visual Studio Code per Connected Environment](get-started-nodejs-01.md#get-kubernetes-debugging-for-vs-code).

## <a name="debug-the-container-in-kubernetes"></a>Eseguire il debug del contenitore in Kubernetes
Premere **F5** per eseguire il debug del codice in Kubernetes.

Come con il comando `up`, il codice viene sincronizzato con l'ambiente di sviluppo all'avvio del debug e un contenitore viene compilato e distribuito in Kubernetes. Questa volta, naturalmente, il debugger è collegato al contenitore remoto.

[!INCLUDE[](includes/tip-vscode-status-bar-url.md)]

Impostare un punto di interruzione in un file di codice sul lato server, ad esempio all'interno di `app.get('/api'...` in `server.js`. Aggiornare la pagina del browser oppure premere il pulsante 'Say It Again'. Si raggiungerà il punto di interruzione e sarà possibile eseguire il codice un'istruzione alla volta.

È possibile accedere in modo completo alle informazioni di debug, proprio come se il codice fosse eseguito in locale, ad esempio stack di chiamate, variabili locali, informazioni sulle eccezioni e così via.

## <a name="edit-code-and-refresh-the-debug-session"></a>Modificare il codice e aggiornare la sessione di debug
Con il debugger attivo, apportare una modifica al codice. Ad esempio, modificare di nuovo il messaggio di saluto:

```javascript
app.get('/api', function (req, res) {
    res.send('**** Hello from webfrontend running in Azure! ****');
});
```

Salvare il file e nel **riquadro Azioni di debug** fare clic sul pulsante **Aggiorna**. 

![](media/debug-action-refresh-nodejs.png)

Invece di ricompilare e ridistribuire una nuova immagine del contenitore ogni volta che vengono apportate modifiche al codice, spesso con un considerevole dispendio di tempo, Connected Environment riavvierà il processo Node.js tra le sessioni di debug per rendere possibile un ciclo di modifica/debug più veloce.

Aggiornare l'app Web nel browser oppure premere il pulsante *Say It Again*. Il messaggio personalizzato verrà visualizzato nell'interfaccia utente.


## <a name="use-nodemon-to-develop-even-faster"></a>Usare NodeMon per velocizzare ulteriormente lo sviluppo
*Nodemon* è uno strumento diffuso usato dagli sviluppatori Node.js per lo sviluppo rapido. Invece di riavviare manualmente il processo Node dopo ogni modifica del codice sul lato server, gli sviluppatori spesso configurano il progetto Node in modo che *nodemon* esegua il monitoraggio delle modifiche ai file e riavvi automaticamente il processo server. Con questo stile di lavoro, lo sviluppatore aggiorna semplicemente il browser dopo aver apportato una modifica al codice.

Lo scopo di Connected Environment è consentire l'uso degli stessi flussi di lavoro per lo sviluppo produttivi adottati per lo sviluppo in locale. Per illustrare questo approccio, il progetto di esempio `webfrontend` è stato configurato per l'uso di *nodemon* (configurato come dipendenza di sviluppo in `package.json`).

Provare quanto segue:
1. Arrestare il debugger di Visual Studio Code.
1. Fare clic sull'icona Debug nella **barra attività** sul lato di Visual Studio Code. 
1. Selezionare **Connetti (VSCE)** come configurazione di debug attiva.
1. Premere F5.

In questa configurazione, il contenitore è configurato per avviare *nodemon*. Quando vengono apportate modifiche al codice sul lato server, *nodemon* riavvia automaticamente il processo Node, come avviene quando si sviluppa in locale. 
1. Modificare di nuovo il messaggio di saluto in `server.js` e salvare il file.
1. Aggiornare il browser oppure fare clic sul pulsante *Say It Again* per rendere effettive le modifiche.

**Ora si conosce un metodo per eseguire rapidamente iterazioni e debug del codice direttamente in Kubernetes.** Si vedrà poi come è possibile creare e chiamare un secondo contenitore.

> [!div class="nextstepaction"]
> [Chiamare un servizio in esecuzione in un contenitore separato](get-started-nodejs-05.md)

