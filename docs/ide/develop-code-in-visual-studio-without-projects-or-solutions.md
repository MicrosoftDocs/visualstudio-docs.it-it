---
title: Sviluppare codice in Visual Studio senza progetti o soluzioni | Microsoft Docs
ms.date: 02/21/2018
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
ms.openlocfilehash: 08c50a07992a1856ad0d5f45c0200e0b8a232cb7
ms.sourcegitcommit: 3abca1c733af876c8146daa43a62e829833be280
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/23/2018
---
# <a name="develop-code-in-visual-studio-without-projects-or-solutions"></a>Sviluppare codice in Visual Studio senza progetti o soluzioni

In Visual Studio 2017 è possibile aprire codice da quasi qualsiasi tipo di progetto basato su directory in Visual Studio senza la necessità di un file di soluzione o progetto. Questo significa, ad esempio, che è possibile clonare un repository in GitHub, aprirlo direttamente in Visual Studio e avviare l'attività di sviluppo senza dover creare una soluzione o un progetto. Se necessario, è possibile specificare attività di compilazione personalizzate e parametri di avvio tramite semplici file JSON.

Dopo aver aperto i file di codice in Visual Studio, Esplora soluzioni consente di visualizzare tutti i file nella cartella. È possibile fare clic su qualsiasi file per iniziare a modificarlo. Visual Studio avvia l'indicizzazione dei file in background per abilitare le funzionalità IntelliSense, di navigazione e di refactoring. Man mano che si modificano, creano, spostano o eliminano file, Visual Studio tiene traccia automaticamente delle modifiche e aggiorna continuamente il relativo indice IntelliSense. Il codice verrà visualizzato con colorazione della sintassi e in molti casi includerà le funzionalità di base per il completamento delle istruzioni IntelliSense.

## <a name="open-any-code"></a>Aprire qualsiasi codice

È possibile aprire il codice in Visual Studio in uno dei modi seguenti:

- Nella barra dei menu di Visual Studio scegliere **File** > **Apri** > **Cartella** e quindi passare al percorso del codice.
- Nel menu di scelta rapida (pulsante destro del mouse) di una cartella contenente codice scegliere il comando **Apri in Visual Studio**.
- Scegliere il collegamento **Apri cartella** nella pagina iniziale di Visual Studio.
- Se si preferisce usare la tastiera, premere **CTRL**+**MAIUSC**+**ALT**+**O** in Visual Studio.
- Aprire codice da un repository GitHub clonato.

### <a name="to-open-code-from-a-cloned-github-repo"></a>Per aprire codice da un repository GitHub clonato

L'esempio seguente mostra come clonare un repository GitHub e quindi aprire il relativo codice in Visual Studio. Per eseguire questa procedura, è necessario disporre di un account GitHub e di GIT per Windows installato nel sistema. Per altre informazioni, vedere [Signing up for a new GitHub account](https://help.github.com/articles/signing-up-for-a-new-github-account/) (Registrarsi per un nuovo account GitHub) e [Git for Windows](https://git-for-windows.github.io/) (GIT per Windows).

1. Passare al repository da clonare su GitHub.

1. Scegliere il pulsante **Clone or download** (Clona o scarica) e quindi il pulsante **Copy to clipboard** (Copia negli appunti) nel menu a discesa per copiare l'URL sicuro per il sito GitHub.

   ![Pulsante per clonare in GitHub](./media/VSIDE_Code_Clone.png)

1. In Visual Studio scegliere la scheda **Team Explorer** per aprire Team Explorer. Se la scheda non è visualizzata, aprirla da **Visualizza** > **Team Explorer**.

1. In Team Explorer, nella sezione **Repository Git locali**, scegliere il comando **Clona** e quindi incollare l'URL della pagina GitHub nella casella di testo.

   ![Clonare il progetto](./media/VSIDE_Code_Clone2.png)

1. Scegliere il pulsante **Clona** per clonare i file del progetto in un repository Git locale. L'operazione potrebbe richiedere diversi minuti a seconda delle dimensioni del repository.

1. Dopo aver clonato il repository nel sistema, in Team Explorer scegliere il comando **Apri** nel menu di scelta rapida (pulsante destro del mouse) del repository appena clonato.

   ![Repository clonato](./media/VSIDE_Code_Clone3.png)

1. Scegliere il comando **Mostra visualizzazione cartelle** per visualizzare i file in Esplora soluzioni.

   ![Mostra visualizzazione cartelle](./media/VSIDE_Code_Clone3_show.png)

   È ora possibile esaminare le cartelle e i file nel repository clonato, visualizzare il codice ed eseguire ricerche al suo interno nell'editor del codice di Visual Studio, usufruendo della colorazione della sintassi e di altre funzionalità.

|         |         |
|---------|---------|
|  ![icona della telecamera](../install/media/video-icon.png "Guardare un video")|    [Guardare un video](https://mva.microsoft.com/en-us/training-courses/getting-started-with-visual-studio-2017-17798?l=lp3TOKD6D_6711787171) su come clonare e aprire il codice da un repository di GitHub in Visual Studio. |

## <a name="run-and-debug-your-code"></a>Eseguire il codice ed eseguirne il debug

È possibile eseguire il debug del codice in Visual Studio senza un progetto o una soluzione. Per eseguire il debug di alcuni linguaggi, potrebbe essere necessario specificare un *file di avvio* valido nella codebase, ad esempio uno script, un eseguibile o un progetto. Nella casella di riepilogo a discesa accanto al pulsante **Avvia** della barra degli strumenti sono elencati tutti gli elementi di avvio rilevati da Visual Studio, oltre agli elementi designati in modo specifico. Quando di esegue il debug del codice, Visual Studio esegue prima di tutto questo codice.

La configurazione del codice per l'esecuzione in Visual Studio varia a seconda del tipo di codice e degli strumenti di compilazione.

### <a name="codebases-that-use-msbuild"></a>Codebase che usano MSBuild

Le codebase basate su MSBuild possono avere più configurazioni di compilazione visualizzate nell'elenco a discesa del pulsante **Avvia**. Selezionare il file che si vuole usare come elemento di avvio e quindi scegliere il pulsante **Avvia** per avviare il debug.

> [!NOTE]
> Per le codebase C# e Visual Basic, è necessario avere installato il carico di lavoro **Sviluppo per desktop .NET**. Per le codebase C++, è necessario avere installato il carico di lavoro **Sviluppo di applicazioni desktop con C++**.

### <a name="codebases-that-use-custom-build-tools"></a>Codebase che usano strumenti di compilazione personalizzati

Se la codebase usa strumenti di compilazione personalizzati, è necessario indicare a Visual Studio come compilare il codice tramite *attività di compilazione* definite in un file *json*. Per altre informazioni, vedere [Personalizzare le attività di compilazione e debug](../ide/customize-build-and-debug-tasks-in-visual-studio.md).

### <a name="codebases-that-contain-python-or-javascript-code"></a>Codebase che contengono codice Python o JavaScript

Se la codebase contiene codice Python o JavaScript, non è necessario configurare file *json*, ma occorre installare il carico di lavoro corrispondente. È anche necessario configurare lo script di avvio:

1. Installare il carico di lavoro [Sviluppo Node.js](https://www.visualstudio.com/vs/node-js/) o [Sviluppo Python](https://www.visualstudio.com/vs/python/) scegliendo **Strumenti** > **Ottieni strumenti e funzionalità** oppure chiudere Visual Studio ed eseguire il programma di installazione Visual Studio.

   ![Carichi di lavoro Sviluppo Node.js e Sviluppo Python](media/python_nodejs_workloads.png)

1. In**Esplora soluzioni** scegliere il comando **Imposta come elemento di avvio** nel menu di scelta rapida di un file JavaScript o Python.

1. Scegliere il pulsante **Avvia** per avviare il debug.

### <a name="codebases-that-contain-c-code"></a>Codebase che contengono codice C++

Per informazioni sull'apertura di codice C++ senza soluzioni o progetti in Visual Studio, vedere [Open Folder projects for C++](/cpp/ide/non-msbuild-projects) (Progetti Apri cartella per C++).

### <a name="codebases-that-contain-a-visual-studio-project"></a>Codebase che contenono un progetto di Visual Studio

Se la cartella del codice contiene un progetto di Visual Studio, è possibile designare il progetto come elemento di avvio.

![Impostare il progetto come elemento di avvio](media/customize-set-project-as-startup-item.png)

Il testo del pulsante **Avvia** cambia per indicare che il progetto è l'elemento di avvio.

![Progetto sul pulsante Avvia](media/customize-start-button-project.png)

## <a name="see-also"></a>Vedere anche

- [Personalizzare le attività di compilazione e debug](../ide/customize-build-and-debug-tasks-in-visual-studio.md)
- [Open Folder projects for C++](/cpp/ide/non-msbuild-projects) (Progetti Apri cartella per C++)
- [Progetti CMake in C++](/cpp/ide/cmake-tools-for-visual-cpp)
- [Scrivere codice nell'editor del codice](../ide/writing-code-in-the-code-and-text-editor.md)