---
title: Visualizzare lo stack di chiamate nel debugger di Visual Studio | Documenti Microsoft
ms.custom: H1Hack27Feb2017
ms.date: 04/06/2017
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
ms.openlocfilehash: d20a1ac9f1a09b93f577c6aa90f550ccd6ff0def
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="view-the-call-stack-and-use-the-call-stack-window-in-the-visual-studio-debugger"></a>Consente di visualizzare lo stack di chiamate e utilizzare la finestra Stack di chiamate nel debugger di Visual Studio

Tramite il **Stack di chiamate** finestra, è possibile visualizzare le chiamate di funzione o di routine attualmente presenti nello stack. Il **Stack di chiamate** finestra Mostra l'ordine in cui sono chiamate i metodi e funzioni. Lo stack di chiamate è un ottimo modo per esaminare e comprendere il flusso di esecuzione di un'app.
  
Quando [i simboli di debug](#bkmk_symbols) non sono disponibili per una parte di uno stack di chiamate, il **Stack di chiamate** finestra potrebbe non essere in grado di visualizzare le informazioni corrette per tale parte dello stack di chiamate. In questo caso, viene visualizzata la notazione seguente:  
  
`[Frames below may be incorrect and/or missing, no symbols loaded for name.dll]`

>  [!NOTE]
> Il **Stack di chiamate** finestra è simile alla prospettiva di Debug in un IDE come Eclipse. 

> [!NOTE]
>  Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella presente Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, selezionare **Importa / Esporta impostazioni** sul **strumenti** menu.  Vedere [personalizzazione dell'IDE](../ide/personalizing-the-visual-studio-ide.md)
  
## <a name="view-the-call-stack-while-in-the-debugger"></a>Visualizzare lo stack di chiamate quando nel debugger 
  
-   Durante il debug di **Debug** dal menu **Windows > Stack di chiamate**.

 ![Finestra Stack di chiamate](../debugger/media/dbg_basics_callstack_window.png "CallStackWindow")

Lo stack frame in cui è attualmente posizionato il puntatore di esecuzione è contraddistinto da una freccia gialla. Per impostazione predefinita, questo è lo stack frame cui informazioni vengono visualizzate nell'origine, **variabili locali**, **Auto**, **espressioni di controllo**, e **Disassembly** windows . Se si desidera modificare il contesto del debugger a un altro frame nello stack, è possibile farlo [passaggio a un altro stack frame](#bkmk_switch).   
  
## <a name="display-non-user-code-in-the-call-stack-window"></a>Visualizzare il codice non utente nella finestra Stack di chiamate  
  
-   Fare doppio clic su di **Stack di chiamate** window e selezionare **Mostra codice esterno**.

Codice non utente è un codice che non viene visualizzato quando [Just My Code](../debugger/just-my-code.md) è abilitata. Nel codice gestito, i frame di codice non utente sono nascosti per impostazione predefinita. La notazione seguente viene visualizzato invece i frame di codice non utente:  
  
**[\<Codice esterno >]**  
  
## <a name="bkmk_switch"></a> Passare a un altro stack frame (modifica il contesto di debug)
  
1.  Nel **Stack di chiamate** finestra, lo stack frame il cui codice e i dati che si desidera visualizzare con pulsante destro del mouse.

    In alternativa, è possibile fare doppio clic su un frame nel **Stack di chiamate** finestra per passare al frame selezionato. 
  
2.  Selezionare **passa al Frame**.  
  
     Una freccia verde ricurva viene visualizzato accanto al frame dello stack selezionato. Il puntatore di esecuzione rimarrà nel frame originale, sempre contrassegnato dalla freccia gialla. Se si seleziona **passaggio** o **continua** dal **Debug** menu esecuzione continuerà nel frame originale, non nel frame selezionato.  
  
## <a name="view-the-source-code-for-a-function-on-the-call-stack"></a>Visualizzare il codice sorgente per una funzione nello stack di chiamate  
  
-   Nel **Stack di chiamate** finestra, la funzione di codice la cui origine si desidera visualizzare e selezionare rapida **Vai a codice sorgente**.

## <a name="run-to-a-specific-function-from-the-call-stack-window"></a>Eseguire una funzione specifica dalla finestra Stack di chiamate  
  
-  Nel **Stack di chiamate** finestra, selezionare la funzione, mouse e scegliere **Esegui fino al cursore**.  
  
## <a name="set-a-breakpoint-on-the-exit-point-of-a-function-call"></a>Impostare un punto di interruzione nel punto di uscita di una chiamata di funzione  
  
-   Vedere [impostare un punto di interruzione in una funzione dello stack di chiamate](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_in_the_call_stack_window).

## <a name="display-calls-to-or-from-another-thread"></a>Visualizzare le chiamate a o da un altro thread  
  
-   Fare doppio clic su di **Stack di chiamate** window e selezionare **Includi chiamate da e verso altri thread**.   
  
## <a name="visually-trace-the-call-stack"></a>Tracciare visivamente lo stack di chiamate  

Se si utilizza Visual Studio Enterprise (solo), è possibile visualizzare le mappe codice per lo stack di chiamate durante il debug.

- Nel **Stack di chiamate** finestra, aprire il menu di scelta rapida. Scegliere **Mostra Stack di chiamate nella mappa del codice**. (Tastiera: **CTRL** + **MAIUSC** + **`**)  
  
    Per informazioni dettagliate, vedere [mappare i metodi sullo stack di chiamate durante il debug](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

![Mostra Stack di chiamate nella mappa codici](../debugger/media/dbg_basics_show_call_stack_on_code_map.gif "ShowCallStackOnCodeMap")
  
## <a name="view-the-disassembly-code-for-a-function-on-the-call-stack"></a>Visualizzare il codice disassembly per una funzione nello stack di chiamate  
  
-   Nel **Stack di chiamate** finestra, la funzione il cui disassembly di codice si desidera visualizzare e selezionare rapida **Vai a Disassembly**.    

## <a name="change-the-optional-information-displayed"></a>Modificare le informazioni opzionali visualizzate  
  
-   Fare doppio clic sui **Stack di chiamate** finestra e di impostare o deselezionare **Mostra \< ***le informazioni che desidera***>**.  
  
## <a name="bkmk_symbols"></a> Caricare i simboli per un modulo
Nel **Stack di chiamate** finestra, è possibile caricare i simboli per il codice che non dispone attualmente di caricare i simboli di debug. Questi simboli possono essere simboli di sistema o .NET Framework scaricati dai server dei simboli pubblici Microsoft o simboli contenuti in un percorso nel computer del quale si esegue il debug.  
  
Vedere [specifica simboli (PDB) e i file di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
### <a name="to-load-symbols"></a>Per caricare i simboli  
  
1.  Nel **Stack di chiamate** finestra, pulsante destro del mouse sul frame dello stack per i simboli non sono stati caricati. Il frame verrà disattivato (rappresentato in grigio).  
  
2.  Scegliere **Carica simboli** e quindi fare clic su **server dei simboli Microsoft** (se disponibile) o selezionare il percorso dei simboli.  
  
### <a name="to-set-the-symbol-path"></a>Per impostare il percorso dei simboli  
  
1.  Nel **Stack di chiamate** finestra, scegliere **impostazioni simboli** dal menu di scelta rapida.  
  
     Il **opzioni** verrà visualizzata la finestra di dialogo e **simboli** viene visualizzata la pagina.  
  
2.  Fare clic su **le impostazioni dei simboli**.  
  
3.  Nel **opzioni** finestra di dialogo fare clic sull'icona della cartella.  
  
     Nel **percorsi dei file (con estensione pdb) di simboli** casella, viene visualizzato un cursore.  
  
4.  Digitare il percorso di directory del simbolo sul computer del quale si esegue il debug. Per il debug locale e remoto, si tratta di un percorso nel computer locale.
  
5.  Fare clic su **OK** per chiudere la finestra di dialogo **Opzioni**.  
  
## <a name="see-also"></a>Vedere anche  
 [Codice misto e informazioni mancanti nella finestra Stack di chiamate](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md)  
 [Visualizzazione dei dati nel Debugger](../debugger/viewing-data-in-the-debugger.md)   
 [Specificare i simboli (PDB) e file di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Uso di punti di interruzione](../debugger/using-breakpoints.md)