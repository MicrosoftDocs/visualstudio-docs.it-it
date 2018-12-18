---
title: Eseguire il debug di un controllo WebView (UWP) | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 7d105907-8b39-4d07-8762-5c5ed74c7f21
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: uwp
ms.openlocfilehash: 8c463bc443540e136b2cffd1a4abdda2cc543d05
ms.sourcegitcommit: 5d43e9590e2246084670b79269cc9d99124bb3df
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/19/2018
---
# <a name="debug-a-webview-control-in-a-uwp-app"></a>Eseguire il debug di un controllo WebView in un'App UWP
  
 Per esaminare ed eseguire il debug dei controlli `WebView` in un'app di Windows Runtime, puoi configurare Visual Studio in modo da collegare Script Debugger all'avvio dell'app. Sono disponibili due modi per interagire con `WebView` controlla l'utilizzo del debugger:  
  
-   Aprire il [DOM Explorer](../debugger/quickstart-debug-html-and-css.md) per un `WebView` istanza e controllare gli elementi DOM, esaminare i problemi di stile CSS e sottoposto a rendering in modo dinamico le modifiche apportate agli stili di test.  
  
-   Selezionare la pagina Web o `iFrame` nella `WebView` istanza come destinazione nel [JavaScript Console](../debugger/javascript-console-commands.md) finestra e quindi interagire con la pagina Web usando i comandi della console. La console consente di accedere al contesto di esecuzione dello script corrente.  
  
### <a name="attach-the-debugger-c-visual-basic-c"></a>Collegare il debugger (C#, Visual Basic, C++)  
  
1.  In Visual Studio, aggiungi un controllo `WebView` all'app di Windows Runtime.  
  
2.  In Esplora soluzioni, aprire le proprietà per il progetto scegliendo **proprietà** dal menu di scelta rapida per il progetto.  
  
3.  Scegliere **Debug**. Nel **processo dell'applicazione** scegliere **Script**.  
  
     ![Collegare il debugger di script](../debugger/media/js_dom_webview_script_debugger.png "JS_DOM_WebView_Script_Debugger")  
  
4.  (Facoltativo) Per le versioni non Express di Visual Studio, disabilitare il debug just-in-time (JIT) scegliendo **strumenti > Opzioni > Debug > Just-In-Time**, e quindi disabilitando il debug JIT per Script.  
  
    > [!NOTE]
    >  Disabilitando il debug JIT, puoi nascondere le finestre di dialogo per le eccezioni non gestite che si verificano in alcune pagine Web. In Visual Studio Express, il debug JIT è sempre disabilitato.  
  
5.  Premere F5 per avviare il debug.  
  
### <a name="use-the-dom-explorer-to-inspect-and-debug-a-webview-control"></a>Usare DOM Explorer per esaminare ed eseguire il debug di un controllo WebView  
  
1.  (C#, Visual Basic, C++) Collega Script Debugger all'app. Per istruzioni consulta la prima sezione.  
  
2.  Se non l'hai già fatto, aggiungi un controllo `WebView` all'app e premi F5 per avviare il debug.  
  
3.  Passa alla pagina contenente i controlli `Webview`.  
  
4.  Aprire la finestra di DOM Explorer per il `WebView` controllo scegliendo **Debug**, **Windows**, **DOM Explorer**e quindi scegliere l'URL del `WebView` che si Se si desidera controllare.  
  
     ![Apertura di DOM Explorer](../debugger/media/js_dom_webview.png "JS_DOM_WebView")  
  
     La finestra di DOM Explorer associata al controllo `WebView` viene visualizzata come nuova scheda in Visual Studio.  
  
5.  Visualizzare e modificare gli elementi DOM attivi e gli stili CSS come descritto in [gli stili di Debug CSS utilizzando DOM Explorer](../debugger/debug-css-styles-using-dom-explorer.md).  
  
### <a name="use-the-javascript-console-window-to-inspect-and-debug-a-webview-control"></a>Usare la finestra Console JavaScript per esaminare ed eseguire il debug di un controllo WebView  
  
1.  (C#, Visual Basic, C++) Collega Script Debugger all'app. Per istruzioni consulta la prima sezione.  
  
2.  Se non l'hai già fatto, aggiungi un controllo `WebView` all'app e premi F5 per avviare il debug.  
  
3.  Aprire la finestra JavaScript Console per il `WebView` controllo scegliendo **Debug**, **Windows**, **JavaScript Console**.  
  
     La finestra Console JavaScript viene visualizzata.  
  
4.  Passa alla pagina contenente i controlli `Webview`.  
  
5.  Nella finestra della Console, selezionare la pagina Web o un `iFrame` visualizzato per il `WebView` controllo il **destinazione** elenco.  
  
     ![Selezione nella finestra della console JavaScript di destinazione](../debugger/media/js_console_target.png "JS_Console_Target")  
  
    > [!NOTE]
    >  Tramite la console puoi interagire con un singolo `WebView`, `iFrame`, contratto di condivisione o Web worker alla volta. Ogni elemento richiede un'istanza separata dell'host della piattaforma Web (WWAHost.exe). Puoi interagire con un solo host alla volta.  
  
6.  Consente di visualizzare e modificare le variabili nell'app o utilizzare i comandi della console, come descritto in [Guida introduttiva: eseguire il Debug di JavaScript](../debugger/quickstart-debug-javascript-using-the-console.md) e [comandi della JavaScript Console](../debugger/javascript-console-commands.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Guida introduttiva: Eseguire il debug di HTML e CSS](../debugger/quickstart-debug-html-and-css.md)