---
title: "Guida introduttiva: Creare per la prima volta un'app Node.js con Visual Studio | Microsoft Docs"
description: In questa guida introduttiva verrà creata un'app Node.js in Visual Studio
ms.custom: ''
ms.date: 11/15/2017
ms.technology:
- vs-acquisition
ms.topic: quickstart
ms.devlang: javascript
ms.assetid: b0e4ebed-1a01-41ef-aad1-4d8465ce5322
author: mikejo5000
ms.author: mikejo
manager: douge
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: c1c40d3d62abb855906b7b61a75c698d21622d1d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="quickstart-use-visual-studio-to-create-your-first-nodejs-app"></a>Guida introduttiva: Creare per la prima volta un'app Node.js con Visual Studio
In questa introduzione di 5-10 minuti all'ambiente di sviluppo integrato (IDE) di Visual Studio si creerà una semplice applicazione Web Node.js. Se non è ancora stato installato Visual Studio, installarlo gratuitamente [qui](http://www.visualstudio.com).  

## <a name="create-a-project"></a>Creare un progetto
Per prima cosa si crea un progetto di applicazione Web Node.js.

1. Se il runtime di Node.js non è già installato, installare la versione LTS dal sito Web [Node.js](https://nodejs.org/en/download/).

    In generale, Visual Studio rileva automaticamente il runtime di Node.js installato. Se non viene rilevato un runtime installato è possibile configurare il progetto per fare riferimento al runtime installato.

1. Aprire Visual Studio 2017.  

1. Nella barra dei menu in alto scegliere **File** > **Nuovo** > **Progetto**.  

1. Nel riquadro sinistro della finestra di dialogo **Nuovo progetto** espandere **JavaScript** e quindi selezionare **Node.js**. Nel riquadro centrale scegliere **Applicazione Web Node.js vuota**, quindi scegliere **OK**.   

     Se non viene visualizzato il modello di progetto **Applicazione Web Node.js vuota**, fare clic sul collegamento **Apri il programma di installazione di Visual Studio** nel riquadro sinistro della finestra di dialogo **Nuovo progetto**. Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo Node.js**, quindi scegliere **Modifica**.  

     ![Carico di lavoro Node.js nel programma di installazione di Visual Studio](../ide/media/quickstart-nodejs-workload.png)  

    Visual Studio crea la nuova soluzione e apre il progetto. Nell'editor nel riquadro sinistro si apre *server.js*.

## <a name="explore-the-ide"></a>Esplorare l'IDE  

1. Osservare **Esplora soluzioni** nel riquadro a destra.

   ![Esplora soluzioni](../ide/media/quickstart-nodejs-solution-explorer.png)  

  - Il progetto viene visualizzato in grassetto, con il nome assegnato in precedenza nella finestra di dialogo **Nuovo progetto**. Sul disco il progetto è rappresentato da un file con estensione njsproj nella cartella del progetto.

  - Al primo livello è presente una soluzione che, per impostazione predefinita, ha lo stesso nome del progetto. Una soluzione, rappresentata sul disco da un file con estensione sln, è un contenitore per uno o più progetti correlati.

  - Il nodo npm visualizza tutti i pacchetti npm eventualmente installati. È possibile fare clic con il pulsante destro del mouse sul nodo npm per cercare e installare pacchetti npm tramite una finestra di dialogo.

1. Se si vuole installare pacchetti npm o comandi node.js da un prompt dei comandi, fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Apri prompt dei comandi qui**.

   ![Prompt dei comandi node.js](../ide/media/quickstart-nodejs-command-prompt.png) 

1. Nel file *server.js* dell'editor (riquadro sinistro), scegliere `http.createServer` e premere **F12** oppure scegliere **Vai a definizione** dal menu di scelta rapida (attivato con il clic destro del mouse). Questo comando consente di passare alla definizione della funzione `createServer` in index.d.ts.  

   ![Menu di scelta rapida Vai a definizione](../ide/media/quickstart-nodejs-gotodefinition.png)  

1. Ritornare a *server.js*, posizionare il cursore alla fine della stringa di questa riga di codice, `res.end('Hello World\n');`, e modificarla come visualizzato di seguito:

    `res.end('Hello World\n' + res.connection.`

    Quando si digita `connection.` IntelliSense offre opzioni per il completamento automatico dell'immissione di codice.

   ![Completamento automatico di IntelliSense](../ide/media/quickstart-nodejs-intellisense.png)  

1. Scegliere **localPort**, quindi digitare `);` per completare l'istruzione in modo che risulti simile alla seguente:

    `res.end('Hello World\n' + res.connection.localPort);`

## <a name="run-the-application"></a>Esecuzione dell'applicazione
1. Premere **CTRL+F5** o scegliere **Debug > Avvia senza eseguire debug** per eseguire l'applicazione. L'app viene aperta in un browser.  

1. Nella finestra del browser viene visualizzato "Hello World" e il numero della porta locale.

1. Chiudere il Web browser.  

La guida introduttiva è stata completata. Ci auguriamo che sia stata utile per l'apprendimento sull'uso di IDE di Visual Studio. Se si vuole approfondire la conoscenza relativa alle funzionalità, continuare con un'esercitazione nella sezione del sommario relativa alle **esercitazioni**.  

## <a name="next-steps"></a>Passaggi successivi 

- Completare l'[Esercitazione per Node.js e Express](../nodejs/tutorial-nodejs.md)  
- Completare l'[Esercitazione per Node.js e React](../nodejs/tutorial-nodejs-with-react-and-jsx.md)  