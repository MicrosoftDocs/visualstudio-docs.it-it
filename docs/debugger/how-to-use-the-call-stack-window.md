---
title: Visualizzare lo stack di chiamate nel debugger | Microsoft Docs
ms.custom: seodec18
ms.date: 10/29/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.callstack
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
- aspx
helpviewer_keywords:
- threading [Visual Studio], displaying calls to or from
- functions [debugger], viewing code on call stack
- disassembly code
- breakpoints, Call Stack window
- debugging [Visual Studio], switching to another stack frame
- debugging [Visual Studio], Call Stack window
- Call Stack window, viewing source code for functions on the call stack
- stack, switching stack frames
- Call Stack window, viewing disassembly code for functions on the call stack
ms.assetid: 5154a2a1-4729-4dbb-b675-db611a72a731
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fe3b266ee44b326749ed555df77dee66b8e82aae
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062351"
---
# <a name="view-the-call-stack-and-use-the-call-stack-window-in-the-debugger"></a>Visualizzare lo stack di chiamate e utilizzare la finestra Stack di chiamate nel debugger

Tramite la finestra **Stack di chiamate** è possibile visualizzare le chiamate di funzione o di routine attualmente presenti nello stack. La finestra **Stack di chiamate** visualizza l'ordine in cui vengono chiamati metodi e funzioni. Lo stack di chiamate è un ottimo modo per esaminare e comprendere il flusso di esecuzione di un'app.

Quando [i simboli di debug](#bkmk_symbols) non sono disponibili per una parte di uno stack di chiamate, la **Stack di chiamate** finestra potrebbe non essere in grado di visualizzare le informazioni corrette per tale parte dello stack di chiamate, visualizzazione invece:

`[Frames below may be incorrect and/or missing, no symbols loaded for name.dll]`

> [!NOTE]
> La finestra **Stack di chiamate** è simile alla prospettiva di debug di alcuni IDE come Eclipse.

> [!NOTE]
> Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella presente Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti**.  Visualizzare [Reimposta le impostazioni](../ide/environment-settings.md#reset-settings).

## <a name="view-the-call-stack-while-in-the-debugger"></a>Visualizzare lo stack di chiamate quando nel debugger

- Durante il debug di **Debug** dal menu **Windows > Stack di chiamate**.

  ![Finestra Stack di chiamate](../debugger/media/dbg_basics_callstack_window.png "CallStackWindow")

Lo stack frame in cui è attualmente posizionato il puntatore di esecuzione è contraddistinto da una freccia gialla. Per impostazione predefinita, le informazioni in questo stack frame viene visualizzato nell'origine, **variabili locali**, **Auto**, **Watch**, e **Disassembly** windows. Per modificare il contesto del debugger a un altro frame nello stack [passare a un altro stack frame](#bkmk_switch).

## <a name="display-non-user-code-in-the-call-stack-window"></a>Visualizzare il codice non utente nella finestra Stack di chiamate

-   Fare clic con il pulsante destro del mouse sulla finestra **Stack di chiamate** e selezionare **Mostra codice esterno**.

Codice non utente è un codice che non viene visualizzato quando [Just My Code](../debugger/just-my-code.md) è abilitata. Nel codice gestito, i frame del codice non utente sono nascoste per impostazione predefinita. La notazione seguente viene visualizzato al posto le cornici di codice non utente:

`[<External Code>]`

## <a name="bkmk_switch"></a> Passare a un altro stack frame (modifica il contesto di debug)

1.  Nel **Stack di chiamate** finestra, pulsante destro del mouse lo stack frame con codice e i dati che si desidera visualizzare.

    O, è possibile fare doppio clic su un frame nel **Stack di chiamate** finestra per passare a quel frame.

2.  Selezionare **Passa al frame**.

     Viene visualizzata una freccia verde ricurva accanto al frame dello stack che è stato selezionato. Il puntatore di esecuzione rimarrà nel frame originale, sempre contrassegnato dalla freccia gialla. Se si sceglie **Esegui** o **Continua** dal menu **Debug**, l'esecuzione continuerà nel frame originale, non nel frame selezionato.

## <a name="view-the-source-code-for-a-function-on-the-call-stack"></a>Visualizzare il codice sorgente per una funzione nello stack di chiamate

-   Nella finestra **Stack di chiamate** fare clic con il pulsante destro del mouse sulla funzione della quale si vuole esaminare il codice sorgente e selezionare **Vai a codice sorgente**.

## <a name="run-to-a-specific-function-from-the-call-stack-window"></a>Eseguire una funzione specifica dalla finestra Stack di chiamate

-  Nel **Stack di chiamate** finestra, selezionare la funzione, fare doppio clic su, quindi scegliere **Esegui fino al cursore**.

## <a name="set-a-breakpoint-on-the-exit-point-of-a-function-call"></a>Impostare un punto di interruzione nel punto di uscita di una chiamata di funzione

-   Visualizzare [impostare un punto di interruzione in una funzione dello stack di chiamate](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_in_the_call_stack_window).

## <a name="display-calls-to-or-from-another-thread"></a>Visualizzare le chiamate a o da un altro thread

-   Fare clic con il pulsante destro del mouse sulla finestra **Stack di chiamate** e selezionare **Includi chiamate da e verso altri thread**.

## <a name="visually-trace-the-call-stack"></a>Tracciare visivamente lo stack di chiamate

In Visual Studio Enterprise (solo), è possibile visualizzare le mappe codice per lo stack di chiamate durante il debug.

- Nella finestra **Stack di chiamate** aprire il menu di scelta rapida. Scegli **Mostra Stack di chiamate nella mappa del codice** (**Ctrl** + **MAIUSC** + **`**).

    Per altre informazioni, vedere [mappare i metodi sullo stack di chiamate durante il debug](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

![Mostra Stack di chiamate nella mappa del codice](../debugger/media/dbg_basics_show_call_stack_on_code_map.gif "ShowCallStackOnCodeMap")

## <a name="view-the-disassembly-code-for-a-function-on-the-call-stack-c-c-visual-basic-f"></a>Visualizzare il codice disassembly per una funzione nello stack di chiamate (C#, C++, Visual Basic, F#)

-   Nella finestra **Stack di chiamate** fare clic con il pulsante destro del mouse sulla funzione della quale si desidera esaminare il codice del disassembly e selezionare **Vai a disassembly**.

## <a name="change-the-optional-information-displayed"></a>Scegliere quali informazioni opzionali visualizzate

-   Fare doppio clic nella **Stack di chiamate** finestra e impostare o deselezionare **mostrano \<**  _le informazioni che desidera_ **>**.

## <a name="bkmk_symbols"></a> Caricare i simboli per un modulo (C#, C++, Visual Basic, F#)

Nella finestra **Stack di chiamate** è possibile caricare i simboli di debug per un codice che non ne dispone. Questi simboli possono essere simboli di sistema o .NET Framework scaricati dai server dei simboli pubblici Microsoft o simboli contenuti in un percorso nel computer del quale si esegue il debug.

Vedere [Specificare file di simboli (con estensione pdb) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

### <a name="to-load-symbols"></a>Per caricare i simboli

1.  Nel **Stack di chiamate** finestra, pulsante destro del mouse sul frame dello stack per i simboli non vengono caricati. Il frame verrà disattivato (rappresentato in grigio).

2.  Puntare **caricare i simboli** e quindi selezionare **server dei simboli Microsoft** (se disponibile), o selezionare il percorso dei simboli.

### <a name="to-set-the-symbol-path"></a>Per impostare il percorso dei simboli

1.  Nella finestra **Stack di chiamate** scegliere **Impostazioni simboli** nel menu di scelta rapida.

     Viene visualizzata la finestra di dialogo **Opzioni** con la pagina **Simboli**.

2.  Selezionare **delle impostazioni dei simboli**.

3.  Nella finestra di dialogo **Opzioni** fare clic sull'icona della cartella.

     Viene visualizzato un cursore nella casella **Percorsi dei file di simboli (pdb)**.

4.  Immettere un nome di percorso di directory nel percorso simboli nel computer in cui si esegue il debug. Per eseguire il debug locale e remoto, questo è un percorso nel computer locale.

5.  Selezionare **OK** per chiudere la **opzioni** nella finestra di dialogo.

## <a name="see-also"></a>Vedere anche

- [Codice misto e informazioni mancanti nella finestra Stack di chiamate](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md)
- [Visualizzazione di dati nel debugger](../debugger/viewing-data-in-the-debugger.md)
- [Specificare file di simboli (PDB) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Uso di punti di interruzione](../debugger/using-breakpoints.md)