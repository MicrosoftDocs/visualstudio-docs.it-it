---
title: Barra degli strumenti di Spy + + | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Spy++ toolbar
ms.assetid: 949c18fb-bb25-42ed-9130-c4a47869f24d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f90c9f249ea0091d7cd5b899ffcd9b7cdadc5a7c
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="spy-toolbar"></a>Barra degli strumenti di Spy++
La barra degli strumenti viene visualizzata nella barra dei menu di Spy + +. Per visualizzare o nascondere la barra degli strumenti nel **vista** menu, fare clic su **barra degli strumenti**.  
  
 I controlli seguenti sono disponibili sulla barra degli strumenti.  
  
## <a name="uielement-list"></a>Elenco UIElement  
  
|Button|Effetto|  
|------------|------------|  
|![Spy&#43; &#43; pulsante di Windows](../debugger/media/icon_spy--_windows.gif "Icon_Spy + + Windows")|Consente di visualizzare una visualizzazione albero dei controlli windows e nel sistema. Per ulteriori informazioni, vedere [Windows Vista](../debugger/windows-view.md).|  
|![Spy&#43; &#43; elabora pulsante](../debugger/media/icon_spy--_processes.gif "Icon_Spy + + _Processes")|Consente di visualizzare una visualizzazione albero dei processi nel sistema. Per ulteriori informazioni, vedere [visualizzazione processi](../debugger/processes-view.md).|  
|![Spy&#43; &#43; pulsante di thread](../debugger/media/icon_spy--_threads.gif "Icon_Spy + + _Threads")|Consente di visualizzare una visualizzazione albero dei thread nel sistema. Per ulteriori informazioni, vedere [visualizzazione thread](../debugger/threads-view.md).|  
|![Spy&#43; &#43; pulsante i messaggi](../debugger/media/icon_spy--_messages.gif "Icon_Spy + + _Messages")|Crea una finestra per visualizzare i messaggi della finestra e apre il **Opzioni messaggio** nella finestra di dialogo in cui è possibile selezionare la finestra in cui i messaggi verranno visualizzati e le altre opzioni. Per ulteriori informazioni, vedere [visualizzazione messaggi](../debugger/messages-view.md).|  
|![Spy&#43; &#43; avviare pulsante registro](../debugger/media/icon_spy--_startlog.gif "Icon_Spy + + _StartLog")|Inizia la registrazione dei messaggi e consente di visualizzare il flusso di messaggi. Questo controllo è disponibile solo quando un **messaggi** finestra è la finestra attiva. Per ulteriori informazioni, vedere [procedura: avviare e arrestare la visualizzazione del Log dei messaggi](../debugger/how-to-start-and-stop-the-message-log-display.md).|  
|![Spy&#43; &#43; pulsante Arresta registro](../debugger/media/icon_spy--_stoplog.gif "Icon_Spy + + _StopLog")|Registrazione e la visualizzazione del flusso di messaggi dei messaggi si interrompe. Questo controllo è disponibile solo quando un **messaggi** finestra è la finestra attiva. Per ulteriori informazioni, vedere [procedura: avviare e arrestare la visualizzazione del Log dei messaggi](../debugger/how-to-start-and-stop-the-message-log-display.md).|  
|![Spy&#43; &#43; pulsante Opzioni registri](../debugger/media/icon_spy--_logoptions.gif "Icon_Spy + + _LogOptions")|Consente di visualizzare il [Opzioni messaggio](../debugger/message-options-dialog-box.md) la finestra di dialogo. Utilizzare questa finestra di dialogo per selezionare windows e di tipi per la visualizzazione di messaggi. Questo controllo è disponibile solo quando un **messaggi** finestra è la finestra attiva.|  
|![Spy&#43; &#43; Log pulsante Cancella](../debugger/media/spy--_clearlog.gif "Spy + + _ClearLog")|Cancella il contenuto dell'oggetto attivo **messaggi** finestra. Questo controllo è disponibile solo quando un **messaggi** finestra è la finestra attiva.|  
|![Spy&#43; &#43; pulsante Trova finestra](../debugger/media/icon_spy--_findwindow.gif "Icon_Spy + + _FindWindow")|Apre il [Trova finestra](../debugger/find-window-dialog-box.md) nella finestra di dialogo che consente di impostare i criteri di ricerca di finestra e visualizzare le proprietà o i messaggi. Per ulteriori informazioni, vedere [procedura: utilizzare lo strumento di ricerca](../debugger/how-to-use-the-finder-tool.md).|  
|![Spy&#43; &#43; pulsante Trova prima finestra](../debugger/media/icon_spy--_window.gif "Icon_Spy + + _Window")|Consente la visualizzazione corrente per una finestra corrispondente, processo, thread o messaggio.|  
|![Spy&#43; &#43; pulsante Trova finestra successiva](../debugger/media/icon_spy--_nextwindow.gif "Icon_Spy + + _NextWindow")|Consente la visualizzazione corrente per la finestra corrispondente successiva, processo, thread o messaggio. Questo controllo (e il comando di menu correlate) è disponibile solo se è presente un risultato di ricerca valido che non è univoco. Ad esempio, quando si usa un handle di finestra come criterio di ricerca nell'albero della finestra, produce risultati univoci in quanto è solo una finestra nell'albero della finestra con tale handle; In questo caso, **Trova successivo** non è disponibile.|  
|![Spy&#43; &#43; precedente pulsante Trova finestra](../debugger/media/icon_spy--_prevwindow.gif "Icon_Spy + + _PrevWindow")|Consente la visualizzazione corrente per la finestra corrispondente precedente, processo, thread o messaggio. Questo controllo (e il comando di menu correlate) è disponibile solo se è presente un risultato di ricerca valido che non è univoco. Ad esempio, quando si usa un handle di finestra come criterio di ricerca nell'albero della finestra, produce risultati univoci in quanto è solo una finestra nell'albero della finestra con tale handle; In questo caso, **Trova precedente** non è disponibile.|  
|![Spy&#43; &#43; pulsante delle proprietà Explorer](../debugger/media/icon_spy--_propexp.gif "Icon_Spy + + _PropExp")|Visualizza le proprietà della finestra che viene selezionato nella visualizzazione delle finestre.|  
|![Spy&#43; &#43; pulsante Aggiorna](../debugger/media/icon_spy--_refresh.gif "Icon_Spy + + _Refresh")|Aggiorna le viste di sistema.|  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo di Spy + +](../debugger/using-spy-increment.md)   
 [Visualizzazioni di Spy + +](../debugger/spy-increment-views.md)   
 [riferimenti per Spy++](../debugger/spy-increment-reference.md)