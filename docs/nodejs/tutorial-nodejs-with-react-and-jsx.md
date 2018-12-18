---
title: Creare un progetto Node.js e un'app React in Visual Studio | Microsoft Docs
description: In questa esercitazione si crea un progetto Node.js e un'app React in Visual Studio
ms.custom: mvc
ms.date: 02/19/2018
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
ms.openlocfilehash: 21debd24f69b79cb2dbbf9e9ceea928ac9dd851e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="tutorial-create-a-nodejs-and-react-app-in-visual-studio"></a>Esercitazione: Creare un progetto Node.js e un'app React in Visual Studio
Visual Studio consente di creare con facilità un progetto Node.js e di avvalersi di IntelliSense e delle altre funzionalità incorporate che supportano Node.js. In questa esercitazione per Visual Studio si crea un progetto di applicazione web Node.js da un modello di Visual Studio. Quindi si crea un'app semplice usando React.

In questa esercitazione si imparerà a:
> [!div class="checklist"]
> * Creare un progetto Node.js
> * Aggiungere pacchetti npm
> * Aggiungere codice React all'app
> * Eseguire il transpile in JSX
> * Collegare il debugger

## <a name="prerequisites"></a>Prerequisiti

* È necessario che siano installati Visual Studio e il carico di lavoro di sviluppo Node.js.

    Se non è ancora stato installato Visual Studio, installarlo gratuitamente [qui](http://www.visualstudio.com).

    Se il carico di lavoro è già installato ed è necessario installare Visual Studio, fare clic sul collegamento **Apri il programma di installazione di Visual Studio** nel riquadro sinistro della finestra di dialogo **Nuovo progetto**. Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo Node.js**, quindi scegliere **Modifica**.

* Il runtime di Node.js deve essere installato.

    Se il runtime non è installato, installare la versione LTS dal sito Web [Node.js](https://nodejs.org/en/download/). In generale, Visual Studio rileva automaticamente il runtime di Node.js installato. Se non viene rilevato un runtime installato, è possibile usare la pagina delle proprietà per configurare il progetto in modo che faccia riferimento al runtime installato (dopo aver creato un progetto, fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Proprietà**).

    Questa esercitazione è stata sottoposta a test con la versione 8.9.4.

## <a name="create-a-project"></a>Creare un progetto
Per prima cosa creare un progetto di applicazione Web Node.js.

1. Aprire Visual Studio 2017.

1. Nella barra dei menu in alto scegliere **File** > **Nuovo** > **Progetto**.

1. Nel riquadro sinistro della finestra di dialogo **Nuovo progetto** espandere **JavaScript** e quindi selezionare **Node.js**. Nel riquadro centrale scegliere **Applicazione Web Node.js vuota**, digitare il nome **NodejsWebAppBlank** e scegliere **OK**.

     Se non viene visualizzato il modello di progetto **Applicazione Web Node.js vuota** è necessario installare prima il carico di lavoro Sviluppo Node.js.

    Visual Studio crea la nuova soluzione e apre il progetto.

    ![Progetto Node.js in Esplora soluzioni](../nodejs/media/tutorial-nodejs-react-project-structure.png)

    - Il progetto viene visualizzato in grassetto, con il nome assegnato in precedenza nella finestra di dialogo **Nuovo progetto**. Nel file system il progetto è rappresentato da un file con estensione *njsproj* nella cartella del progetto. È possibile impostare le proprietà e le variabili di ambiente associate al progetto facendo clic con il pulsante destro del mouse sul progetto e scegliendo **Proprietà**. È possibile eseguire sequenze di andata e ritorno con altri strumenti di sviluppo, perché il file di progetto non apporta modifiche personalizzate all'origine del progetto Node.js.

    - Al primo livello è presente una soluzione che, per impostazione predefinita, ha lo stesso nome del progetto. Una soluzione, rappresentata su disco da un file con estensione *sln*, è un contenitore per uno o più progetti correlati.

    - Il nodo npm visualizza tutti i pacchetti npm eventualmente installati. È possibile fare clic con il pulsante destro del mouse sul nodo npm per cercare e installare pacchetti npm tramite una finestra di dialogo.

    - I file di progetto come *server.js* vengono visualizzati sotto il nodo del progetto. *server.js* è il file di avvio del progetto.

## <a name="add-npm-packages"></a>Aggiungere pacchetti npm

Per essere eseguita correttamente, l'app richiede vari moduli npm.

* react
* react-dom
* express
* path
* ts-loader
* typescript
* webpack
* webpack-cli

1. In Esplora soluzioni (riquadro destro), fare clic con il pulsante destro del mouse sul nodo **npm** nel progetto e scegliere **Installa nuovi pacchetti npm**.

    Nella finestra di dialogo **Installa nuovi pacchetti npm** è possibile scegliere di installare la versione più recente dei pacchetti o specificare la versione desiderata. Se dopo aver scelto di installare la versione corrente di questi pacchetti si riscontrano errori imprevisti, potrebbe essere necessario installare le versioni esatte dei pacchetti citate più avanti in questa procedura.

1. Nella finestra di dialogo **Installa nuovi pacchetti npm** cercare il pacchetto react e fare clic su **Installa pacchetto** per installarlo.

    ![Installa nuovi pacchetti npm](../nodejs/media/tutorial-nodejs-react-install-packages.png)

    La finestra **Output** visualizza lo stato di installazione del pacchetto. Dopo l'installazione il pacchetto viene visualizzato sotto il nodo **npm**.

    Il file *package.json* del progetto viene aggiornato con le nuove informazioni sul pacchetto, inclusa la versione del pacchetto.

1. Anziché usare l'interfaccia utente per cercare e aggiungere gli altri pacchetti uno alla volta, incollare il codice seguente nel file package.json. Sostituire la sezione `dependencies` con il codice seguente:

    ```js
    "dependencies": {
      "express": "4.16.2",
      "path": "0.12.7",
      "react": "16.2.0",
      "react-dom": "16.2.0",
      "ts-loader": "4.0.1",
      "typescript": "2.7.2",
      "webpack": "4.1.1",
      "webpack-cli": "2.0.11"
    }
    ```

1. Fare clic con il pulsante destro del mouse sul nodo **npm** nel progetto e scegliere **Installa pacchetti npm mancanti**.

    La finestra **Output** visualizza lo stato di installazione dei pacchetti.

    Ecco come appaiono i moduli npm in Esplora soluzioni dopo l'installazione.

    ![Pacchetti npm](../nodejs/media/tutorial-nodejs-react-npm-modules.png)

    > [!NOTE]
    > Se si preferisce installare pacchetti npm o comandi node.js dalla riga di comando, fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Apri prompt dei comandi qui**. Per installare i pacchetti, usare i comandi Node.js standard.

## <a name="add-project-files"></a>Aggiungere file di progetto

In questa procedura si aggiungono quattro nuovi file al progetto.

* *app.tsx*
* *webpack-config.js*
* *index.html*
* *tsconfig.json*

Per questa app semplice i nuovi file di progetto vengono aggiunti nella radice del progetto. Nella maggior parte delle app i file vengono aggiunti a sottocartelle e i riferimenti al percorso relativo vengono modificati di conseguenza.

1. In Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto **NodejsWebAppBlank** e scegliere **Aggiungi** > **Nuovo elemento**.

1. Nella finestra di dialogo **Aggiungi nuovo elemento** scegliere **File JSX TypeScript**, digitare il nome *app.tsx* e fare clic su **OK**.

1. Ripetere questi passaggi per aggiungere *webpack-config.js*.

1. Ripetere gli stessi passaggi per aggiungere *index.html* al progetto. Invece di un file JavaScript, scegliere **File HTML**.

1. Ripetere gli stessi passaggi per aggiungere *tsconfig.json* al progetto. Invece di un file JavaScript, scegliere **File di configurazione JSON per TypeScript**.

## <a name="add-app-code"></a>Aggiungere il codice dell'app

1. Aprire il file *server.js* e sostituire il codice con il seguente:

    ```javascript
    'use strict';
    var path = require('path');
    var express = require('express');

    var app = express();

    var staticPath = path.join(__dirname, '/');
    app.use(express.static(staticPath));

    // Allows you to set port in the project properties.
    app.set('port', process.env.PORT || 3000);

    var server = app.listen(app.get('port'), function() {
        console.log('listening');
    });
    ```

   Il codice precedente usa Express per avviare Node.js come server di applicazioni web. Questo codice imposta la porta sul numero di porta configurato nelle proprietà del progetto (per impostazione predefinita, nelle proprietà è configurata la porta 1337). Per aprire le proprietà del progetto fare clic con il pulsante destro del mouse sul progetto e scegliere **Proprietà**.

1. Aprire *app.tsx* e aggiungere il codice seguente:

    ```javascript
    declare var require: any

    var React = require('react');
    var ReactDOM = require('react-dom');

    class Hello extends React.Component {
        render() {
            return (
                <h1>Welcome to React!!</h1>
            );
        }
    }

    ReactDOM.render(<Hello />, document.getElementById('root'));
    ```

    Il codice precedente usa la sintassi JSX e React per visualizzare un messaggio semplice.

1. Aprire *index.html* e sostituire la sezione **body** con il codice seguente:

    ```html
    <body>
        <div id="root"></div>
        <!-- scripts -->
        <script src="./dist/app-bundle.js"></script>
    </body>
    ```

    Questa pagina HTML carica *app-bundle.js*, che contiene il codice JSX e React convertito tramite transpile in codice JavaScript semplice. Attualmente *app-bundle.js* è un file vuoto. Nella sezione successiva, si configurano le opzioni per eseguire il transpile del codice.

## <a name="configure-webpack-and-typescript-compiler-options"></a>Configurare le opzioni di webpack e del compilatore TypeScript

Nei passaggi precedenti è stato aggiunto al progetto *webpack-config.js*. Ora si aggiunge il codice di configurazione webpack. Si aggiunge una configurazione webpack semplice, che specifica un file di input (*app.tsx*) e un file di output (*app-bundle.js*) per la creazione di bundle e il transpile da JSX a codice JavaScript semplice. Per l'esecuzione del transpile si configurano anche alcune opzioni del compilatore TypeScript. Questo codice è una configurazione di base, che ha lo scopo di presentare webpack e il compilatore TypeScript.

1. In Esplora soluzioni aprire *webpack-config.js* e aggiungere il codice seguente.

    ```json
    module.exports = {
        devtool: 'source-map',
        entry: "./app.tsx",
        mode: "development",
        output: {
            filename: "./app-bundle.js"
        },
        resolve: {
            extensions: ['.Webpack.js', '.web.js', '.ts', '.js', '.jsx', '.tsx']
        },
        module: {
            rules: [
                {
                    test: /\.tsx$/,
                    exclude: /(node_modules|bower_components)/,
                    use: {
                        loader: 'ts-loader'
                    }
                }
            ]
        }
    }
    ```

    Il codice di configurazione webpack indica a Webpack di usare il caricatore TypeScript per eseguire il transpile di JSX.

1. Aprire tsconfig.json e aggiungere il codice seguente, che specifica le opzioni del compilatore TypeScript:

    ```json
    {
      "compilerOptions": {
        "noImplicitAny": false,
        "module": "commonjs",
        "noEmitOnError": true,
        "removeComments": false,
        "sourceMap": true,
        "target": "es5",
        "jsx": "react"
      },
      "exclude": [
        "node_modules"
      ],
      "files": [
        "app.tsx"
      ]
    }
    ```

    app.tsx è specificato come file di origine.

## <a name="transpile-the-jsx"></a>Eseguire il transpile di JSX

1. In Esplora soluzioni fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Apri prompt dei comandi qui**.

1. Al prompt dei comandi digitare il seguente comando:

    `node_modules\.bin\webpack app.tsx --config webpack-config.js`

    Il risultato viene visualizzato nella finestra del prompt dei comandi.

    ![Eseguire webpack](../nodejs/media/tutorial-nodejs-react-run-webpack.png)

    Se invece dell'output precedente vengono visualizzati degli errori, è necessario risolverli prima di poter eseguire l'app. Una causa degli errori può essere il fatto che le versioni dei pacchetti npm sono diverse da quelle visualizzate in questa esercitazione. Un modo per correggere gli errori consiste nell'usare le versioni esatte visualizzate nei passaggi precedenti. Se una o più di queste versioni dei pacchetti sono state deprecate e generano errori, potrebbe essere necessario installare una versione più recente per correggere gli errori.

1. In Esplora soluzioni fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Aggiungi** > **Cartella esistente**, quindi scegliere la cartella *dist* e fare clic su **Seleziona cartella**.

    Visual Studio aggiunge al progetto la cartella *dist* che contiene *app-bundle.js* e *app-bundle.js.map*.

1. Aprire *app-bundle.js* per visualizzare il codice JavaScript di cui è stato eseguito il transpile.

1. Se viene richiesto di ricaricare i file modificati esternamente, fare clic su **Sì a tutti**.

    ![Caricare i file modificati](../nodejs/media/tutorial-nodejs-react-reload-files.png)

Ogni volta che si apportano modifiche ad *app.tsx* è necessario eseguire nuovamente il comando webpack.

## <a name="run-the-app"></a>Eseguire l'app

1. Verificare che Chrome sia selezionato come destinazione di debug corrente.

    ![Selezionare Chrome come destinazione di debug](../nodejs/media/tutorial-nodejs-react-debug-target.png)

1. Per eseguire l'app, premere **F5** (**Debug** > **Avvia debug**) o fare clic sul pulsante con la freccia verde.

    Viene visualizzata una finestra della console Node.js che indica la porta sulla quale è in ascolto il debugger.

    Visual Studio avvia l'app eseguendo il file di avvio *server.js*.

    ![Eseguire React nel browser](../nodejs/media/tutorial-nodejs-react-running-react.png)

1. Chiudere la finestra del browser.

1. Chiudere la finestra della console.

## <a name="set-a-breakpoint-and-run-the-app"></a>Impostare un punto di interruzione ed eseguire l'app

1. In *server.js* fare clic nella barra a sinistra della dichiarazione `staticPath` per impostare un punto di interruzione:

    ![Imposta punto di interruzione](../nodejs/media/tutorial-nodejs-react-set-breakpoint.png)

    I punti di interruzione rappresentano la funzionalità di base essenziale per un debug affidabile. Un punto di interruzione indica il punto in cui Visual Studio dovrebbe sospendere l'esecuzione del codice in modo da poter esaminare i valori delle variabili, il comportamento della memoria o lo stato di esecuzione di un ramo del codice.

1. Per eseguire l'applicazione, premere **F5** (**Debug** > **Avvia debug**).

    Il debugger sospende l'esecuzione nel punto di interruzione impostato (l'istruzione corrente è contrassegnata in giallo). A questo punto è possibile controllare lo stato dell'app passando il mouse sulle variabili attualmente incluse nell'ambito e usando finestre del debugger come **Variabili locali** e **Espressioni di controllo**.

1. Premere **F5** per continuare con l'esecuzione dell'app.

1. Per usare Chrome Developer Tools, premere **F12**. È possibile usare questi strumenti per esaminare il modello DOM e interagire con l'app mediante la console JavaScript.

1. Chiudere il Web browser e la console.

## <a name="set-and-hit-a-breakpoint-in-the-client-side-react-code"></a>Impostare e raggiungere un punto di interruzione nel codice React lato client

Nella sezione precedente il debugger è stato associato al codice Node.js lato server. Per associare il debugger da Visual Studio e accedere a punti di interruzione nel codice React lato client, è necessario che il debugger identifichi il processo corretto. Di seguito viene descritto un metodo per abilitare questa funzionalità.

1. Chiudere tutte le finestre di Chrome.

1. Aprire il comando **Esegui** dal pulsante **Start** di Windows (fare clic con il pulsante destro del mouse e scegliere **Esegui**) e immettere il comando seguente:

    `chrome.exe --remote-debugging-port=9222`

    Viene avviato Chrome con il debug abilitato.

1. Passare a Visual Studio e impostare un punto di interruzione nel codice *app-bundle.js* in corrispondenza della funzione `render()`, come indicato di seguito:

    ![Imposta punto di interruzione](../nodejs/media/tutorial-nodejs-react-set-breakpoint-client-code.png)

1. Con Chrome selezionato come destinazione di debug in Visual Studio, premere **CTRL+F5** (**Debug** > **Avvia senza eseguire debug**) per eseguire l'app nel browser.

    L'app viene aperta in una nuova scheda del browser.

1. Scegliere **Debug** > **Associa a processo**.

1. Nella finestra di dialogo **Associa a processo** scegliere **Webkit code** (Codice webkit) nel campo **Attach to** (Associa a), quindi digitare **chrome** nella casella del filtro per applicare un filtro ai risultati della ricerca.

1. Selezionare il processo di Chrome con la porta host corretta (in questo esempio 1337) e fare clic su **Associa**.

    ![Associa a processo](../nodejs/media/tutorial-nodejs-react-attach-to-process.png)

    Se DOM Explorer e la console JavaScript Console si aprono in Visual Studio, il debugger è stato associato correttamente. Questi strumenti di debug sono simili agli strumenti Chrome Developer Tools e agli Strumenti F12 per Edge.

    > [!NOTE]
    > Se il debugger non è associato e viene visualizzato il messaggio "Impossibile connettersi al processo. Operazione non valida nello stato corrente.", usare Gestione attività per chiudere tutte le istanze di Chrome prima di avviare Chrome in modalità di debug. Se sono in esecuzione estensione di Chrome, la modalità di debug complete potrebbe essere impedita.

1. Dato che il codice con il punto di interruzione è già stato eseguito, aggiornare la pagina del browser per raggiungere il punto di interruzione.

    Durante la pausa del debugger, è possibile esaminare lo stato dell'app passando il mouse sulle variabili e usando le finestre del debugger. È possibile far avanzare il debugger eseguendo il codice istruzione per istruzione (**F5**, **F10** e **F11**).

    A seconda dell'ambiente e dello stato del browser è possibile raggiungere il punto di interruzione in *app-bundle.js* o nel relativo percorso mappato in *app.tsx*. In entrambi i casi è possibile eseguire il codice istruzione per istruzione ed esaminare le variabili.

    * Se è necessario inserire un'interruzione nel codice in *app.tsx*, ma non è possibile eseguire questa operazione, usare **Associa a processo** come descritto nei passaggi precedenti per associare il debugger. A questo punto, aprire il file *app.tsx* generato dinamicamente da Esplora soluzioni selezionando **Documenti script** > **app.tsx**, impostare un punto di interruzione e aggiornare la pagina nel browser.

        Oppure, se è necessario inserire un'interruzione nel codice in *app.tsx*, ma non è possibile eseguire questa operazione, provare a usare l'istruzione `debugger;` in *app.tsx* o impostare i punti di interruzione in Chrome Developer Tools.

    * Se è necessario inserire un'interruzione nel codice in *app bundle.js*, ma non è possibile eseguire questa operazione, rimuovere il file del mapping di origine *app-bundle.js.map*.

    > [!TIP]
    > Dopo aver eseguito per la prima volta l'associazione al processo seguendo questa procedura, è possibile ripetere rapidamente l'associazione allo stesso processo in Visual Studio 2017 scegliendo **Debug** > **Riassocia a processo**.

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione è stato descritto come creare un progetto Node.js e un'app React e come eseguire il transpile in JSX e il debug. Per altre informazioni sugli strumenti Node.js per Visual Studio, vedere la pagina Wiki.

> [!div class="nextstepaction"]
> [Node.js Tools per Visual Studio](https://github.com/Microsoft/nodejstools)
