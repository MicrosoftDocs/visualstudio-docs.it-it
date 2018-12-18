---
title: Creare un progetto Node.js e un'app Express in Visual Studio | Microsoft Docs
description: In questa esercitazione si creerà un progetto Node.js e un'app Express in Visual Studio
ms.custom: ''
ms.date: 03/13/2018
ms.technology: vs-nodejs
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: douge
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 47bf06fabba9197029831382b6ad6e9068e7829c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="tutorial-create-a-nodejs-and-express-app-in-visual-studio"></a>Esercitazione: Creare un progetto Node.js e un'app Express in Visual Studio
In questa esercitazione per lo sviluppo in Visual Studio con Node.js ed Express si creerà una semplice applicazione Web Node.js e si aggiungerà codice all'app, quindi si esploreranno alcune funzionalità dell'ambiente IDE e si eseguirà l'app. Se non è ancora stato installato Visual Studio, installarlo gratuitamente [qui](http://www.visualstudio.com).

In questa esercitazione si imparerà a:
> [!div class="checklist"]
> * Creare un progetto Node.js
> * Aggiungere codice
> * Usare IntelliSense
> * Eseguire l'app
> * Raggiungere un punto di interruzione

## <a name="prerequisites"></a>Prerequisiti

* È necessario che siano installati Visual Studio e il carico di lavoro di sviluppo Node.js.

    Se non è ancora stato installato Visual Studio, installarlo gratuitamente [qui](http://www.visualstudio.com).

    Se il carico di lavoro è già installato ed è necessario installare Visual Studio, fare clic sul collegamento **Apri il programma di installazione di Visual Studio** nel riquadro sinistro della finestra di dialogo **Nuovo progetto**. Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo Node.js**, quindi scegliere **Modifica**.

* Il runtime di Node.js deve essere installato.

    Se il runtime non è installato, installare la versione LTS dal sito Web [Node.js](https://nodejs.org/en/download/). In generale, Visual Studio rileva automaticamente il runtime di Node.js installato. Se non viene rilevato un runtime installato, è possibile usare la pagina delle proprietà per configurare il progetto in modo che faccia riferimento al runtime installato (dopo aver creato un progetto, fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Proprietà**).

    Questa esercitazione è stata testata con Node.js 8.10.0.

## <a name="create-a-project"></a>Creare un progetto
Per prima cosa si crea un progetto di applicazione Web Node.js.

1. Aprire Visual Studio 2017.

1. Nella barra dei menu in alto scegliere **File** > **Nuovo** > **Progetto**.

1. Nel riquadro sinistro della finestra di dialogo **Nuovo progetto** espandere **JavaScript** e quindi selezionare **Node.js**. Nel riquadro centrale selezionare **Applicazione Express 4 Node.js Azure di base** e quindi scegliere **OK**.

     Se non viene visualizzato il modello di progetto **Applicazione Express 4 Node.js Azure di base** è necessario installare prima il carico di lavoro **Sviluppo Node.js**.

    Visual Studio crea la nuova soluzione e apre il progetto. Il file di progetto *app.js* verrà aperto nell'editor (riquadro a sinistra).

    - Il progetto viene visualizzato in grassetto, con il nome assegnato in precedenza nella finestra di dialogo **Nuovo progetto**. Nel file system il progetto è rappresentato da un file con estensione *njsproj* nella cartella del progetto. È possibile impostare le proprietà e le variabili di ambiente associate al progetto facendo clic con il pulsante destro del mouse sul progetto e scegliendo **Proprietà**. È possibile eseguire sequenze di andata e ritorno con altri strumenti di sviluppo, perché il file di progetto non apporta modifiche personalizzate all'origine del progetto Node.js.

    - Al primo livello è presente una soluzione che, per impostazione predefinita, ha lo stesso nome del progetto. Una soluzione, rappresentata su disco da un file con estensione *sln*, è un contenitore per uno o più progetti correlati.

    - Il nodo npm visualizza tutti i pacchetti npm eventualmente installati. È possibile fare clic con il pulsante destro del mouse sul nodo npm per cercare e installare pacchetti npm tramite una finestra di dialogo.

    - I file di progetto come *app.js* vengono visualizzati sotto il nodo del progetto. *app.js* è il file di avvio del progetto.

1. Aprire il nodo **npm** e assicurarsi che siano presenti tutti i pacchetti npm necessari.

    Se uno o più pacchetti risultano mancanti (icona con il punto esclamativo), fare clic con il pulsante destro del mouse sul nodo **npm** e scegliere **Installa pacchetti npm mancanti**.

## <a name="add-some-code"></a>Aggiungere codice

1. In Esplora soluzioni (riquadro a destra) aprire la cartella Visualizzazioni e quindi aprire *index.pug*.

1. Sostituire il contenuto con il markup seguente.

    ```js
    extends layout

    block content
      h1= title
      p Welcome to #{title}
      script.
        var f1 = function() { document.getElementById('myImage').src='#{data.item1}' }
      script.
        var f2 = function() { document.getElementById('myImage').src='#{data.item2}' }
      script.
        var f3 = function() { document.getElementById('myImage').src='#{data.item3}' }

      button(onclick='f1()') One!
      button(onclick='f2()') Two!
      button(onclick='f3()') Three!
      p
      a: img(id='myImage' height='200' width='200' src='')
    ```

1. Nella cartella Route aprire *index.js*.

1. Aggiungere il codice seguente prima della chiamata a `router.get`:

    ```js
    var getData = function () {
        var data = {
            'item1': 'http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-76.jpg',
            'item2': 'http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-77.jpg',
            'item3': 'http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-78.jpg'
        }
        return data;
    }
    ````

1. Sostituire la chiamata alla funzione `router.get` con il codice seguente:

    ```js
    router.get('/', function (req, res) {
        res.render('index', { title: 'Express', "data" });
    });
    ```

    È presente un errore nella riga di codice contenente `res.render`. È necessario correggerlo prima di poter eseguire l'app. L'errore verrà corretto nella prossima sezione.

## <a name="use-intellisense"></a>Usare IntelliSense

1. In *index.js* passare alla riga di codice contenente `res.render`.

1. Dopo la stringa `data` digitare `: get`. IntelliSense visualizza la funzione `getData`. Selezionare `getData`.

    ![Usare IntelliSense](../nodejs/media/tutorial-nodejs-intellisense.png)

1. Rimuovere la virgola (`,`) prima di `"data"`. Verrà visualizzata l'evidenziazione verde della sintassi per l'espressione. Spostare il puntatore del mouse sull'evidenziazione della sintassi.

    ![Visualizzazione di un errore di sintassi](../nodejs/media/tutorial-nodejs-syntax-checking.png)

    L'ultima riga di questo messaggio indica che l'interprete JavaScript prevedeva una virgola (`,`).

1. Fare clic sulla scheda **Elenco errori**.

    Con il nome del file e il numero di riga verranno visualizzati l'avviso e la relativa descrizione.

    ![Visualizzazione dell'elenco errori](../nodejs/media/tutorial-nodejs-error-list.png)

1. Correggere il codice aggiungendo la virgola (`,`) prima di `"data"`.

## <a name="set-a-breakpoint"></a>Imposta punto di interruzione

1. In *index.js* fare clic sul margine a sinistra prima della riga di codice seguente per impostare un punto di interruzione:

    `res.render('index', { title: 'Express', "data": getData() });`

    I punti di interruzione rappresentano la funzionalità di base essenziale per un debug affidabile. Un punto di interruzione indica il punto in cui Visual Studio dovrebbe sospendere l'esecuzione del codice in modo da poter esaminare i valori delle variabili, il comportamento della memoria o lo stato di esecuzione di un ramo del codice.

    ![Imposta punto di interruzione](../nodejs/media/tutorial-nodejs-set-breakpoint.png)

## <a name="run-the-application"></a>Esecuzione dell'applicazione

1. Selezionare la destinazione di debug sulla barra degli strumenti Debug.

    ![Selezione della destinazione di debug](../nodejs/media/tutorial-nodejs-deploy-target.png)

1. Premere **F5** (**Debug** > **Avvia debug**) per eseguire l'applicazione.

    Il debugger si fermerà in corrispondenza del punto di interruzione impostato. È ora possibile esaminare lo stato dell'app.

1. Spostare il puntatore del mouse su `getData` per visualizzarne le proprietà in un suggerimento dati

    ![Esame delle variabili](../nodejs/media/tutorial-nodejs-inspect-variables.png)

1. Premere **F5** (**Debug** > **Continua**) per continuare.

    L'app verrà aperta in un browser.

    Nella finestra del browser verrà visualizzato il titolo "Express" e nel primo paragrafo verrà visualizzato il messaggio "Welcome to Express".

1. Fare clic sui pulsanti per visualizzare immagini diverse.

    ![App in esecuzione nel browser](../nodejs/media/tutorial-nodejs-running-in-browser.png)

1. Chiudere il Web browser.

## <a name="optional-publish-to-azure-app-service"></a>(Facoltativo) Pubblicare in Servizio app di Azure

1. In Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto e scegliere **Pubblica**.

   ![Eseguire la pubblicazione nel servizio app di Azure](../nodejs/media/tutorial-nodejs-publish-to-azure.png)

1. Scegliere **Servizio app di Microsoft Azure**.

    Nella finestra di dialogo **Servizio app** è possibile accedere all'account di Azure e connettersi a sottoscrizioni di Azure esistenti.

1. Seguire i passaggi rimanenti per selezionare una sottoscrizione, scegliere o creare un gruppo di risorse, scegliere o creare un piano di servizio app e quindi, quando richiesto, seguire i passaggi per la pubblicazione in Azure. Per istruzioni più dettagliate, vedere [Publish to Azure Website using Web Deploy](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy) (Pubblicare in Sito Web di Azure tramite Distribuzione Web).

1. La finestra **Output** visualizza lo stato della distribuzione in Azure.

    Al termine della distribuzione, l'app viene aperta in un browser in esecuzione in Servizio app di Azure. Fare clic su un pulsante per visualizzare un'immagine.

   ![App in esecuzione in Servizio app di Azure](../nodejs/media/tutorial-nodejs-running-in-azure.png)

L'esercitazione è stata completata.

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione è stato descritto come creare ed eseguire un'app Node.js usando Express e come raggiungere un punto di interruzione usando il debugger.

> [!div class="nextstepaction"]
> [Node.js Tools per Visual Studio](https://github.com/Microsoft/nodejstools)