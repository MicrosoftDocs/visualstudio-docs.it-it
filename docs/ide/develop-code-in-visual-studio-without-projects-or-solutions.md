---
title: Sviluppare codice in Visual Studio senza progetti o soluzioni | Microsoft Docs
ms.custom: 
ms.date: 02/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: article
helpviewer_keywords:
- open folder [Visual Studio]
- anycode [Visual Studio]
- projects and solutions, develop code without
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 40995be9ee5d5da5a3219dd8badcb13e4b3f6e62
ms.sourcegitcommit: d6327b978661c0a745bf4b59f32d8171607803a3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2018
---
# <a name="develop-code-in-visual-studio-without-projects-or-solutions"></a>Sviluppare codice in Visual Studio senza progetti o soluzioni

In Visual Studio 2017 è possibile aprire codice da quasi qualsiasi tipo di progetto basato su directory in Visual Studio senza la necessità di un file di soluzione o progetto. Questo significa, ad esempio, che è possibile trovare un progetto di codice in GIT, clonarlo e quindi aprirlo direttamente in Visual Studio e avviare l'attività di sviluppo senza dover creare una soluzione o un progetto.  

Non solo è possibile modificare il codice e compilarlo in Visual Studio, ma è anche possibile spostarsi al suo interno, ad esempio con il comando Passa a. Il codice verrà visualizzato con colorazione della sintassi e in molti casi supporta funzionalità per il completamento delle istruzioni di base e il debug, inclusi i punti di interruzione. Per alcuni linguaggi possono essere disponibili anche altre funzionalità. Per altre informazioni, vedere [Creare impostazioni personalizzate e portabili per l'editor](create-portable-custom-editor-options.md).  

## <a name="open-code-anywhere"></a>Aprire il codice ovunque

È possibile aprire il codice in Visual Studio nei modi seguenti:  

- Nella barra dei menu di Visual Studio scegliere **File**, **Apri**, **Cartella** e quindi passare al percorso del codice.  

- Nel menu di scelta rapida (pulsante destro del mouse) di una cartella contenente codice scegliere il comando **Apri in Visual Studio**.  

- Scegliere il collegamento **Apri cartella** nella pagina iniziale di Visual Studio.  

- Aprire codice clonato da un repository di GitHub.  

### <a name="to-open-code-from-a-cloned-github-repo"></a>Per aprire codice da un repository GitHub clonato

L'esempio seguente mostra come clonare un repository GitHub e quindi aprire il relativo codice in Visual Studio. Per eseguire questa procedura, è necessario disporre di un account GitHub e di GIT per Windows installato nel sistema. Per altre informazioni, vedere [Signing up for a new GitHub account](https://help.github.com/articles/signing-up-for-a-new-github-account/) (Registrarsi per un nuovo account GitHub) e [Git for Windows](https://git-for-windows.github.io/) (GIT per Windows).  

1. Passare al repository da clonare su GitHub.  

1. Scegliere il pulsante **Clone or download** (Clona o scarica) e quindi il pulsante **Copy to clipboard** (Copia negli appunti) nel menu a discesa per copiare l'URL sicuro per il sito GitHub.  

  ![Pulsante per clonare in GitHub](./media/VSIDE_Code_Clone.png)

    > [!NOTE]
    >  Anche se è possibile aprire il progetto sul desktop o scaricare un file ZIP del progetto, questo esempio illustra come clonare il repository usando il metodo dell'URL sicuro.

1. In Visual Studio scegliere la scheda **Team Explorer** per aprire Team Explorer.  

1. In Team Explorer, nella sezione **Repository Git locali**, scegliere il comando **Clona** e quindi incollare l'URL della pagina GitHub nella casella di testo.  

  ![Clonare il progetto](./media/VSIDE_Code_Clone2.png)

1. Scegliere il pulsante **Clona** per clonare i file del progetto in un repository Git locale. L'operazione potrebbe richiedere diversi minuti a seconda delle dimensioni del repository.  

1. Dopo aver clonato il repository nel sistema, in Team Explorer scegliere il comando **Apri** nel menu di scelta rapida (pulsante destro del mouse) del repository appena clonato.  

  ![Repository clonato](./media/VSIDE_Code_Clone3.png)

1. Scegliere il comando **Mostra visualizzazione cartelle** per visualizzare i file in Esplora soluzioni.  

  ![Mostra visualizzazione cartelle](./media/VSIDE_Code_Clone3_show.png)

  È ora possibile esaminare le cartelle e i file nel repository clonato, visualizzare il codice ed eseguire ricerche al suo interno nell'editor del codice di Visual Studio, usufruendo della colorazione della sintassi e di altre funzionalità.

    ![Ricerca nel codice del progetto clonato](./media/VSIDE_Code_Clone4.png)  

|         |         |
|---------|---------|
|  ![icona della telecamera](../install/media/video-icon.png "Guardare un video")  |    [Guardare un video](https://mva.microsoft.com/en-us/training-courses/getting-started-with-visual-studio-2017-17798?l=lp3TOKD6D_6711787171) su come clonare e aprire il codice da un repository di GitHub in Visual Studio. |

## <a name="debug-your-code"></a>Eseguire il debug del codice

È possibile eseguire il debug del codice in Visual Studio senza un progetto o una soluzione. Per eseguire il debug di alcuni linguaggi, potrebbe essere necessario specificare un *file di avvio* valido nel progetto del codice, ad esempio uno script, un eseguibile o un progetto. Quando di esegue il debug del codice, Visual Studio esegue prima di tutto questo codice specificato.  

Nella casella di riepilogo a discesa accanto al pulsante Avvia della barra degli strumenti sono elencati tutti gli elementi di avvio rilevati da Visual Studio, oltre agli elementi scelti in modo specifico in una cartella.  

![Pulsante Esegui](./media/VSIDE_Code_Run_Button.png)  

Visual Studio riconosce automaticamente i progetti, ma gli script (ad esempio Python e JavaScript) devono essere selezionati esplicitamente come elemento di avvio prima che compaiano in questo elenco. Alcuni elementi di avvio, inoltre, come MSBuild e CMake, possono avere più configurazioni di compilazione che vengono visualizzate nell'elenco a discesa del pulsante Esegui.  

Visual Studio supporta attualmente il debug per i linguaggi seguenti:  

- Node.js  

- Python  

- Progetti basati su MSBuild (C#, VB, C++)  

- Qualsiasi eseguibile con file PDB (Python Debugger).  

### <a name="to-debug-nodejs-and-python"></a>Per eseguire il debug di codice Node.js e Python:

1. Installare Node.js o Python Tools oppure Visual Studio 2017 e il runtime Node.js.  

1. Nel menu di scelta rapida di un file JavaScript in Esplora soluzioni scegliere il comando **Imposta come elemento di avvio**.  

1. Premere il tasto **F5** per avviare il debug.  

### <a name="to-debug-msbuild-projects"></a>Per eseguire il debug di progetti MSBuild

1. Nel menu di Visual Studio scegliere **Debug**. Nel menu a discesa scegliere il progetto o selezionare il progetto o file da visualizzare come elemento di avvio in Esplora soluzioni.  

1. Premere il tasto **F5** per avviare il debug.  

### <a name="to-debug-executable-files"></a>Per eseguire il debug di file eseguibili

1. Nel menu di Visual Studio scegliere **Debug**. Nel menu a discesa scegliere il progetto o selezionare il progetto o file da visualizzare come elemento di avvio in Esplora soluzioni.  

1. Premere il tasto **F5** per avviare il debug.  

## <a name="enable-custom-build-tools"></a>Abilitare gli strumenti di compilazione personalizzati

Visual Studio riconosce automaticamente molti linguaggi diversi per l'esecuzione, ma non tutti. Se Visual Studio riconosce il linguaggio, è possibile eseguire immediatamente il codice. Se si tenta di eseguire il codice, ma Visual Studio non sa come eseguirlo, viene visualizzata una barra informazioni che richiede di designare un file nella codebase come elemento di avvio.  

Se tuttavia la codebase usa strumenti di compilazione personalizzati che Visual Studio non riconosce, probabilmente non sarà possibile eseguire il codice, né eseguirne il debug, in Visual Studio se non si completano alcuni passaggi aggiuntivi. È necessario specificare un tipo di file eseguibile valido, ad esempio un compilatore, insieme a eventuali parametri e argomenti personalizzati richiesti dal linguaggio. Per rendere possibile tutto ciò, Visual Studio include le *attività di compilazione*. È possibile creare un'attività di compilazione per specificare tutti gli elementi necessari per compilare ed eseguire il codice di un linguaggio.  

È anche possibile creare attività di compilazione arbitrarie che possono eseguire praticamente qualsiasi operazione. Ad esempio, si può creare un'attività per elencare il contenuto di una cartella o rinominare un file. Si possono anche creare attività di compilazione personalizzate più specifiche, che eseguono operazioni come la compilazione del progetto con argomenti specifici. La procedura seguente illustra come creare entrambi i tipi di attività di compilazione.  

#### <a name="to-create-an-arbitrary-build-task"></a>Per creare un'attività di compilazione arbitraria

1. Scegliere il file o la cartella del progetto in Esplora soluzioni in cui si vuole includere l'attività e nel menu di scelta rapida (pulsante destro del mouse) del file o della cartella scegliere **Configura attività**.  

  ![Configura attività](./media/VSIDE_Code_Config_Task.png)

  Quando si sceglie **Configura attività** viene aperto un file denominato tasks.vs.json. Se questo file non esiste, viene creato. Questo file contiene le attività di compilazione per la cartella o il file selezionato.  

  ![File Tasks.vs.json](./media/VSIDE_Code_Tasks_JSON.png)

1. Aggiungere l'attività di compilazione seguente al file tasks.vs.json. Per questo esempio, si aggiungerà una semplice attività denominata "List outputs" che elenca i file e le sottocartelle della cartella selezionata nella finestra di output. La nuova attività deve essere aggiunta all'interno della matrice "tasks" esistente.  

  ```xml
      {
        "taskName": "List outputs",
        "appliesTo": "*",
        "type": "command",
        "command": "${env.COMSPEC}",
        "args": [
          "dir ${outDir}"
        ]
      },
  ```
  L'aspetto dell'attività di compilazione completa dovrebbe essere simile al seguente.  

  ![Attività di compilazione arbitraria](./media/VSIDE_Code_Tasks_ArbTask.png)

1. Salvare il progetto.  

1. Aprire il menu di scelta rapida per la cartella selezionata. La nuova attività di compilazione arbitraria dovrebbe essere visualizzata nella parte inferiore del menu di scelta rapida.  

  ![Comando per l'attività di compilazione arbitraria](./media/VSIDE_Code_Tasks_ArbTask2.png)

1. Scegliere il nuovo comando **List outputs** per eseguire l'attività.  

### <a name="to-create-a-custom-build-task"></a>Per creare un'attività di compilazione personalizzata

Questa procedura illustra come aggiungere due attività di compilazione personalizzate che usano nMake per compilare e pulire il codice.  

1. Scegliere un file del progetto in Esplora soluzioni da designare in seguito come elemento di avvio. Nel menu di scelta rapida (pulsante destro del mouse) del file scegliere **Configura attività**.  

  ![Comando per l'attività di compilazione personalizzata](./media/VSIDE_Code_Tasks_CustTask1.png)

1. Aggiungere le attività di compilazione seguenti al file tasks.vs.json. Per questo esempio verranno aggiunte due attività: una denominata "makefile-build" che usa il comando nMake per compilare il progetto e l'altra denominata makefile-clean che chiama il comando nMake con l'argomento "clean". Queste attività devono essere aggiunte all'interno della matrice "tasks" esistente. Si noti che questi sono solo esempi di attività di compilazione. Per consentirne il funzionamento, è necessario che nel sistema sia installato il carico di lavoro contenente [nMake](/cpp/build/nmake-reference).

  ```xml
  {
  "taskName": "makefile-build",
  "appliesTo": "makefile",
  "type": "command",
  "contextType": "build",
  "command": "nmake"
  },
  {
  "taskName": "makefile-clean",
  "appliesTo": "makefile",
  "type": "command",
  "contextType": "clean",
  "command": "nmake",
  "args": [
    "clean"
    ]
  },
  ```
  L'aspetto dell'attività di compilazione personalizzata completa dovrebbe essere simile al seguente.  

  ![Attività di compilazione personalizzata](./media/VSIDE_Code_Tasks_CustTask2.png)

1. Salvare il progetto.  

1. Aprire il menu di scelta rapida per il file selezionato. Le nuove attività di compilazione personalizzate dovrebbero essere visualizzate al centro del menu di scelta rapida.  

  ![Comando per l'attività di compilazione personalizzata](./media/VSIDE_Code_Tasks_CustTask3.png)

  > [!NOTE]
  > I comandi vengono visualizzati sotto il comando **Configura attività** a causa delle impostazioni `contextType`. "build" e "clean" sono comandi di compilazione, pertanto vengono visualizzati nella sezione della compilazione al centro il menu di scelta rapida.  

  Dopo aver associato i comandi di compilazione personalizzati al file, è ora possibile designare il file come elemento di avvio.  

1. Nel menu di scelta rapida del file scegliere **Imposta come elemento di avvio**.  

  ![Comando per l'attività di compilazione personalizzata](./media/VSIDE_Code_Tasks_CustTask4.png)

1. Sulla barra degli strumenti scegliere la freccia in giù accanto al pulsante Avvia. L'elemento di avvio viene ora visualizzato come opzione.  

  ![Comando per l'attività di compilazione personalizzata](./media/VSIDE_Code_Tasks_CustTask5.png)

È ora possibile scegliere il pulsante **Avvia** o il tasto **F5** per eseguire la codebase. È possibile modificare la codebase ed eseguirne il debug in Visual Studio anche se Visual Studio non riconosce gli strumenti di compilazione della codebase. L'output dall'attività di compilazione viene visualizzato nella **finestra di output** e gli errori di compilazione vengono visualizzati nell'**elenco errori**. Il file dell'attività di compilazione tasks.vs.json associa il ciclo di sviluppo interno di Visual Studio agli strumenti di compilazione personalizzati usati dalla codebase.  

Le attività di compilazione personalizzate possono essere aggiunte a singoli file o a tutti i file di un tipo specifico. Ad esempio, i file di pacchetti NuGet possono essere configurati con un'attività "Ripristino pacchetti" oppure si possono configurare tutti i file di origine con un'attività di analisi statica, ad esempio un linter per tutti i file con estensione js.  

Visual Studio supporta la sostituzione VSCode `$variable` nella radice del file tasks.vs.json, oltre alle variabili di ambiente, come `$env.var`, o le chiavi.  

## <a name="specify-build-output"></a>Specificare l'output della compilazione

Se il progetto deve essere compilato, è possibile aggiungere un altro tag chiamato `output` nel file tasks.vs.json. Di seguito è riportato un esempio.  

`"output": "${workspaceRoot}\\bin\\hellomake.exe"`

La specifica del percorso di output consente di indicare a Visual Studio dove trovare l'output di compilazione del progetto.  

## <a name="tasksvsjson-file-location"></a>Posizione del file tasks.vs.json

Per impostazione predefinita, il file tasks.vs.json si trova in una cartella nascosta denominata `.vs`. Per visualizzare i file nascosti in Visual Studio, scegliere il pulsante **Mostra tutti i file** sulla barra degli strumenti di Esplora soluzioni.

![Comando per l'attività di compilazione arbitraria](./media/VSIDE_Code_Tasks_FileLocation.png)

Il file tasks.vs.json è nascosto in quanto la maggior parte degli utenti preferisce in genere non archiviarlo nel controllo del codice sorgente. Se, tuttavia, si vuole avere la possibilità di archiviarlo nel controllo del codice sorgente, trascinare il file nella radice del progetto dove sarà visibile.  

Nella cartella .vs potrebbero essere presenti altri file con estensione json, ma gli unici spostabili sono il file tasks.vs.json e il file launch.vs.json, se presente. Il file launch.vs.json configura il debugger di Visual Studio, mentre il file tasks.vs.json configura la compilazione in Visual Studio.  

## <a name="see-also"></a>Vedere anche

[Scrivere codice nell'editor del codice](../ide/writing-code-in-the-code-and-text-editor.md)
