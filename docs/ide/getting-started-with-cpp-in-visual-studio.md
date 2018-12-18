---
title: Introduzione a C++ in Visual Studio | Microsoft Docs
ms.custom: mvc
ms.date: 12/04/2017
ms.technology: vs-acquisition
ms.tgt_pltfrm: ''
ms.topic: tutorial
author: corob-msft
ms.author: tglee
manager: ghogen
dev_langs:
- CPP
ms.workload:
- cplusplus
ms.openlocfilehash: ce0d48a4390ee1c008f889e45760fcef92538cb2
ms.sourcegitcommit: 064f8678f4a918e1dce60285090a9803d37dc34b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2018
---
# <a name="get-started-with-c-in-visual-studio"></a>Introduzione a C++ in Visual Studio

Completare questa procedura dettagliata per acquisire familiarità con molti strumenti e molte finestre di dialogo utili per lo sviluppo di applicazioni in C++ con Visual Studio. Creare una semplice applicazione in stile "Hello, World", acquisendo al contempo altre informazioni su come lavorare in un ambiente di sviluppo integrato (IDE, Integrated Development Environment).

## <a name="prerequisites"></a>Prerequisiti

Non è necessario avere familiarità con C++ per completare questa guida rapida, ma è necessario avere familiarità con l'attività di programmazione generale e i concetti di debug. La documentazione di Visual Studio non illustra come eseguire la programmazione in C++. Una guida valida per le risorse di formazione di C++ è la pagina [Introduzione](https://isocpp.org/get-started) del sito Web ISO C++.

Per seguire la procedura, è necessaria una copia della versione 15.3 o successiva di Visual Studio 2017, con il carico di lavoro **sviluppo di applicazioni Desktop con C++** installato. Per una Guida rapida all'installazione, vedere la pagina per [il supporto per l'installazione di C++ in Visual Studio](/cpp/build/vscpp-step-0-installation).

## <a name="create-a-console-app"></a>Creare un'applicazione console

Se non è ancora stato avviato, avviare Visual Studio.

![IDE con Visual C# 43; &#43; impostazioni applicate](../ide/media/get-started-cpp-ide-layout.png "IDE con Visual C# 43; &#43; impostazioni applicate")

Dopo aver aperto Visual Studio, saranno visibili le tre parti fondamentali dell'IDE, vale a dire le finestre degli strumenti, i menu e le barre degli strumenti e lo spazio della finestra principale. Le finestre degli strumenti sono ancorate ai lati sinistro e destro della finestra dell'applicazione. La casella di **Avvio veloce**, la barra dei menu e la barra degli strumenti standard si trovano nella parte superiore. Al centro della finestra si trova la **Pagina iniziale**. Quando si apre una soluzione o un progetto, in questo spazio verranno visualizzati gli editor e le finestre di progettazione. Quando si sviluppa un'applicazione, per la maggior parte del tempo si usa quest'area centrale.

Visual Studia usa i *progetti* per organizzare il codice per un'applicazione e le *soluzioni* per organizzare i progetti. Un progetto contiene tutte le opzioni, le configurazioni e le regole usate per la compilazione dell'applicazione. Gestisce anche la relazione tra tutti i file del progetto e i file esterni. Per creare l'applicazione, per prima cosa, creare un nuovo progetto e una soluzione.

### <a name="to-create-a-console-app-project"></a>Per creare un progetto di un'applicazione console

1. Sulla barra dei menu scegliere **File> Nuovo > Progetto** per aprire la finestra di dialogo **Nuovo progetto**.

   ![Nella barra dei menu scegliere File > Nuovo > Progetto](../ide/media/get-started-cpp-file-new-project-menu.png "Nella barra dei menu scegliere File > Nuovo > Progetto")

1. Nella finestra di dialogo **Nuovo progetto**, selezionare **Installato > Visual C++** se non è già selezionato. Nel riquadro centrale selezionare il modello per **l'applicazione console di Windows**. Nella casella di modifica **Nome**, immettere *HelloApp*.

   ![Usare la finestra di dialogo Nuovo progetto per creare il progetto dell'applicazione](../ide/media/get-started-cpp-new-project-dialog.png "Usare la finestra di dialogo Nuovo progetto per creare il progetto dell'applicazione")

   La finestra di dialogo potrebbe avere opzioni diverse a seconda dei carichi di lavoro di Visual Studio e dei componenti installati. Se non vengono visualizzati i modelli del progetto di Visual C++, è necessario eseguire nuovamente il programma di installazione di Visual Studio e installare il carico di lavoro **Sviluppo di applicazioni desktop con C++**. È possibile farlo direttamente dalla finestra di dialogo **Nuovo progetto**. Per avviare il programma di installazione, scegliere il collegamento nella finestra di dialogo **Apri il programma di installazione di Visual Studio** .

1. Scegliere il pulsante **OK** per creare il progetto e la soluzione dell'applicazione.

   Il progetto e la soluzione HelloApp, con i file di base per un progetto console Windows, verranno creati e caricati automaticamente in **Esplora soluzioni**. Il file HelloApp.cpp si aprirà nell'editor del codice. In **Esplora soluzioni**vengono visualizzati gli elementi riportati di seguito.

   ![File per la soluzione in Esplora soluzioni](../ide/media/get-started-cpp-solution-explorer.png "File per la soluzione in Esplora soluzioni")

## <a name="add-code-to-the-app"></a>Aggiungere codice all'applicazione

In seguito, aggiungere il codice per visualizzare la parola "Hello" nella finestra della console.

### <a name="to-edit-code-in-the-editor"></a>Per scrivere codice nell'editor

1. Nel file HelloApp.cpp, inserire una riga vuota prima della riga `return 0;` e quindi immettere il codice:

   ```cpp
   cout << "Hello\n";
   ```

   Una linea rossa ondulata appare sotto `cout`. Se si posiziona il puntatore del mouse su di essa, viene visualizzato un messaggio di errore.

   ![Testo dell'errore per cout](../ide/media/get-started-cpp-intellisense-error.png "Testo dell'errore per cout")

   Il messaggio di errore viene visualizzato anche nella finestra **Elenco errori** . È possibile visualizzare la finestra scegliendo **Visualizzazione > Elenco errori** dalla barra dei menu.

   ![Errore nella finestra Elenco errori](../ide/media/get-started-cpp-error-list.png "Errore nella finestra Elenco errori")

   Nel codice manca una dichiarazione per [std::cout](/cpp/standard-library/iostream), che si trova nel file di intestazione \<iostream>.

1. Per includere l'intestazione iostream, immettere il codice dopo `#include "stdafx.h"`:

   ```cpp
   #include <iostream>
   using namespace std;
   ```

   Si noti che viene visualizzato un riquadro quando si immette il codice. Questa finestra contiene suggerimenti di completamento automatico per i caratteri immessi. Fa parte di IntelliSense per C++, che specifica prompt di codifica, incluse classi o membri di interfaccia e informazioni sui parametri. È anche possibile usare frammenti di codice, cioè blocchi di codice predefiniti. Per altre informazioni, vedere [Using IntelliSense](../ide/using-intellisense.md) e [Code Snippets](../ide/code-snippets.md).

   ![Il codice corretto nell'editor](../ide/media/get-started-cpp-cout-fix.png "Il codice corretto nell'editor")

   La sottolineatura ondulata di colore rosso sotto `cout` scomparirà dopo aver risolto l'errore.

1. Per salvare le modifiche apportate al file premere **Ctrl+S**.

## <a name="build-the-app"></a>Compilare l'applicazione

È facile compilare il codice. Nella barra dei menu scegliere **Compilazione > Compila soluzione**. Visual Studio compila la soluzione HelloApp e i report sullo stato di avanzamento nella finestra di **Output**.

   ![Compilare la soluzione HelloApp](../ide/media/get-started-cpp-build-solution.gif "Compilare la soluzione HelloApp")

## <a name="debug-and-test-the-app"></a>Eseguire il debug e il test dell'app

È possibile eseguire il debug di HelloApp per verificare se la parola "Hello" viene visualizzata nella finestra della console.

### <a name="to-debug-the-app"></a>Per eseguire il debug dell'app

1. Nella barra dei menu scegliere **Debug > Avvia debug** per avviare il debug.

   ![Avviare il comando debug dal menu Debug](../ide/media/get-started-cpp-start-debugging-menu.png "Avviare il comando debug dal menu Debug")

   Il debugger viene avviato e viene eseguito il codice. La finestra della console (una finestra separata simile a un prompt dei comandi) viene visualizzata per pochi secondi, ma si chiude rapidamente quando il debugger si arresta. Per visualizzare il testo, è necessario impostare un punto di interruzione per arrestare l'esecuzione del programma.

### <a name="to-add-a-breakpoint"></a>Per aggiungere un punto di interruzione

1. Nell'editor, posizionare il cursore sulla riga `return 0;`. Nella barra dei menu scegliere **Debug > Imposta/Rimuovi punto di interruzione**. È anche possibile fare clic sul margine sinistro per impostare un punto di interruzione.

     ![Attivare o disattivare il comando del punto di interruzione dal menu Debug](../ide/media/get-started-cpp-toggle-breakpoint-menu.png "Attivare o disattivare il comando del punto di interruzione dal menu Debug")

     Accanto alla riga di codice nel margine di estrema sinistra della finestra dell'editor verrà visualizzato un cerchio rosso.

     ![Punto di interruzione indicato al margine della finestra](../ide/media/get-started-cpp-breakpoint-set.png "Punto di interruzione indicato al margine della finestra")

1. Premere **F5** per avviare il debug.

   Il debugger viene avviato, e viene visualizzata una finestra della console con la parola **Hello**.

   ![Testo Hello nella finestra della console](../ide/media/get-started-cpp-helloapp-window.png "Testo Hello nella finestra della console")

1. Premere MAIUSC+F5 per arrestare il debug.

Per altre informazioni sul debug di progetti di console, vedere [Progetti di Console](../debugger/debugging-preparation-console-projects.md).

## <a name="build-a-release-version-of-the-app"></a>Compilare una versione di rilascio dell'applicazione

Dopo aver verificato che tutto funzioni, è possibile preparare una build di rilascio dell'applicazione. Le build di versione lasciano le informazioni di debug e usano le opzioni di ottimizzazione del compilatore per creare un codice più piccolo e più veloce.

### <a name="to-clean-the-solution-files-and-build-a-release-version"></a>Per pulire i file della soluzione e compilare una versione di rilascio

1. Nella barra dei menu selezionare **Compila > Pulisci soluzione** per eliminare i file intermedi e di output creati durante le compilazioni precedenti.

   ![Comando Pulisci soluzione dal menu Compila](../ide/media/get-started-cpp-clean-solution-menu.png "ExploreIDE-CleanSolution")

1. Per modificare la configurazione della soluzione per HelloApp da **Debug** a **Versione**, nella barra degli strumenti selezionare l'elenco a discesa sul controllo delle configurazioni di soluzione e quindi scegliere **Versione**.

   ![Compilare una versione di rilascio dell'applicazione](../ide/media/get-started-cpp-set-release-configuration.png "C++IDE_ChangingBuildtoRelease")

1. Compilare la soluzione. Nella barra dei menu scegliere **Compilazione > Compila soluzione**.

Al termine della compilazione sarà stata creata un'applicazione che è possibile copiare ed eseguire in qualsiasi finestra del prompt dei comandi. Potrebbe non servire a molto, ma è il punto di partenza per grandi cose.

La guida introduttiva è stata completata. Per esaminare altri esempi, vedere [Visual Studio Samples](../ide/visual-studio-samples.md).

## <a name="see-also"></a>Vedere anche

[Uso dell'IDE di Visual Studio per lo sviluppo di applicazioni desktop C++](/cpp/ide/using-the-visual-studio-ide-for-cpp-desktop-development)  
[Procedura dettagliata: creare un'applicazione semplice con C# o Visual Basic](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md)  
[Suggerimenti relativi alla produttività per Visual Studio](../ide/productivity-tips-for-visual-studio.md)  
[Esempi di Visual Studio](../ide/visual-studio-samples.md)  
[Introduzione allo sviluppo con Visual Studio](../ide/get-started-developing-with-visual-studio.md)
