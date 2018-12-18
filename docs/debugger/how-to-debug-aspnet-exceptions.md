---
title: 'Procedura: Debug di eccezioni ASP.NET | Documenti Microsoft'
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
helpviewer_keywords:
- debugging [Visual Studio], ASP.NET exceptions
- ASP.NET, exceptions
- exceptions, ASP.NET
ms.assetid: 1810096e-de8c-435e-be3d-f365d0cd0a6a
caps.latest.revision: "23"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: aspnet
ms.openlocfilehash: 82c81f2998497f047550e35397dc870338ed977e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-debug-aspnet-exceptions"></a>Procedura: debug di eccezioni ASP.NET
Il debug delle eccezioni è una parte importante dello sviluppo di una potente [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] dell'applicazione. Informazioni generali su come eseguire il debug di eccezioni, vedere [la gestione delle eccezioni con il Debugger](../debugger/managing-exceptions-with-the-debugger.md).  
  
 Per eseguire il debug non gestita [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] eccezioni, è necessario assicurarsi che il debugger si arresta per loro. Il runtime di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] dispone di un gestore eccezioni di livello superiore. Di conseguenza, per impostazione predefinita il debugger non si interrompe mai in corrispondenza di eccezioni non gestite. Per interrompere il debugger quando viene generata un'eccezione, è necessario selezionare **Interrompi quando un'eccezione è: generata** impostazione per tale eccezione nella **eccezioni** la finestra di dialogo.  
  
 Se è stata abilitata Just My Code, **Interrompi quando un'eccezione è: generata** non comporta l'interruzione immediata se viene generata un'eccezione in un metodo .NET Framework o altro codice di sistema del debugger. Invece l'esecuzione continua sino al raggiungimento di codice non di sistema, quindi si interrompe. Non è pertanto necessario eseguire il codice di sistema quando si verifica un'eccezione.  
  
 Just My Code fornisce un'altra opzione che può rivelarsi molto utile: **Interrompi quando un'eccezione è: gestita dall'utente**. Se si sceglie questa impostazione per un'eccezione, il debugger interromperà l'esecuzione nel codice utente, ma solo se l'eccezione non viene intercettata e gestita dal codice utente. Questa impostazione annulla l'effetto del gestore eccezioni di primo livello di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], perché quest'ultimo si trova nel codice non utente.  
  
### <a name="to-enable-debugging-of-aspnet-exceptions-with-just-my-code"></a>Per attivare il debug delle eccezioni ASP.NET con Just My Code  
  
1.  Nel **Debug** menu, fare clic su **eccezioni**.  
  
     Il **eccezioni** viene visualizzata la finestra di dialogo.  
  
2.  Nel **eccezioni Common Language Runtime** riga, selezionare **generata** o **gestita dall'utente**.  
  
     Utilizzare il **gestita dall'utente** impostazione **Just My Code** deve essere abilitata...  
  
### <a name="to-use-best-practices-for-aspnet-exception-handling"></a>Procedure ottimali per la gestione delle eccezioni ASP.NET  
  
-   Collocare blocchi `try ... catch` attorno al codice che può generare eccezioni anticipabili e gestibili. Ad esempio, se l'applicazione effettua chiamate a un servizio Web XML o direttamente a SQL Server, il codice dovrebbe trovarsi **try … catch** blocca perché esistono numerose eccezioni che possono verificarsi.

## <a name="see-also"></a>Vedere anche
[Debug di applicazioni ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)