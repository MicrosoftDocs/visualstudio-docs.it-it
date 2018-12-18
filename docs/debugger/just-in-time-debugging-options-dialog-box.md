---
title: Just-In-Time, debug, finestra di dialogo Opzioni | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Debugger.JIT
- vs.debug.options.JIT
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Just-In-Time debugging, setting options
- Options dialog box, debugging
ms.assetid: 7f11b2e3-3fb5-449d-b07c-6ecf1d6a487d
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 057c5e0e37d8e84daa4348c91847a12b6a9ae5e9
ms.sourcegitcommit: 9e6ff74da1afd8bd2f0e69387ce81f2a74619182
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2018
---
# <a name="just-in-time-debugging-options-dialog-box"></a>JIT, Debug, Finestra di dialogo Opzioni
Per l'accesso di **Just-In-Time** page, passare al **strumenti** menu e fare clic su **opzioni**. Nel **opzioni** finestra di dialogo espandere il **debug** nodo e selezionare **Just-In-Time**. Questa pagina consente di abilitare il debug JIT per codice gestito, codice nativo e script. Per ulteriori informazioni, vedere [debug JIT](../debugger/just-in-time-debugging-in-visual-studio.md).  
  
 È possibile abilitare il debug JIT per questi tipi di programma:  
  
-   Gestito  
  
-   Nativo  
  
-   Script  
  
 Il debug JIT è una tecnica per il debug di un programma avviato al di fuori di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. È possibile eseguire un programma creato in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] al di fuori dell'ambiente di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Se il debug JIT è abilitato e si verifica un arresto anomalo, viene visualizzata una finestra di dialogo in cui viene chiesto se si desidera eseguire il debug.  
  
## <a name="associated-warnings"></a>Avvisi associati  
 Quando si visita questa pagina della finestra di **opzioni** nella finestra di dialogo potrebbe essere visualizzato un messaggio di avviso simile al seguente:  
  
 **Un altro debugger è stato registrato come Just-In-Time debugger. Per risolvere il problema, abilitare Just-In-Time debug o ripristinare Visual Studio.**  
  
 Questo messaggio viene visualizzato se come debugger JIT è impostato un altro debugger, ad esempio una versione precedente del debugger di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 È anche possibile che venga visualizzato il messaggio seguente:  
  
 **-In-Time debug rilevati errori di registrazione. Per risolvere il problema, abilitare Just-In-Time debug o ripristinare Visual Studio.**  
  
 Se viene visualizzato uno di questi avvisi, il debug con Just-In-Time [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] richiede privilegi di amministratore, fino a quando non è stato risolto il problema. Se si tenta di abilitare la modalità JIT in queste condizioni senza disporre di questi privilegi, viene visualizzato il seguente messaggio di errore:  
  
 **Accesso negato. Dispone di un amministratore Abilita Just-In-Time di debug o ripristinare l'installazione di Visual Studio.**  
  
## <a name="see-also"></a>Vedere anche  
 [Debug, finestra di dialogo Opzioni](../debugger/debugging-options-dialog-box.md)   
 [Procedura: Specificare le impostazioni del debugger](../debugger/how-to-specify-debugger-settings.md)