---
title: Microsoft Visual Studio (generata eccezione), finestra di dialogo del Debugger | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.exceptions.thrown
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Microsoft Visual Studio Debugger (Exception Thrown) dialog box
- exception handling, during debugging
- debugger, exceptions
- throwing exceptions, during debugging
ms.assetid: 1fe98d10-c8f9-4b39-a920-99169bfd542e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 24ccb3de6b22f54b239b5b772490a8d05a990dbd
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="microsoft-visual-studio-debugger-exception-thrown-dialog-box"></a>finestra di dialogo Debugger di Microsoft Visual Studio (generata eccezione)
Si è verificata un'eccezione nel programma. In questa finestra di dialogo è indicato il tipo di eccezione generata. Il codice deve gestire questa eccezione. Per la gestione dell'eccezione sono disponibili le seguenti opzioni:  
  
 **Break**  
 Consente il passaggio dell'esecuzione nel debugger. Il gestore dell'eccezione non viene richiamato prima dell'interruzione, ma solo se si sceglie di continuare dopo l'interruzione.  
  
 **Continue**  
 Consente all'esecuzione di continuare offrendo al gestore dell'eccezione la possibilità di gestirla. Questa opzione non è disponibile per alcuni tipi di eccezioni. **Continuare** consentirà all'applicazione di continuare. In un'applicazione nativa, l'eccezione verrà generata nuovamente. In un'applicazione gestita, il programma verrà interrotto oppure l'eccezione verrà gestita da un'applicazione host.  
  
> [!NOTE]
>  Non è possibile scegliere di continuare dopo un'eccezione non gestita nel codice gestito. Scelta di **continua** dopo un'eccezione non gestita nel codice gestito, il debug verrà interrotto.  
  
 **Ignorare**  
 Consente all'esecuzione di continuare senza richiamare il gestore dell'eccezione. Poiché il gestore dell'eccezione non viene richiamato, questa scelta può comportare ulteriori conseguenze, tra cui altre eccezioni o errori. Questa opzione non è disponibile per alcuni tipi di eccezioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione delle eccezioni con il Debugger](../debugger/managing-exceptions-with-the-debugger.md)   
 [Procedure consigliate per le eccezioni](/dotnet/standard/exceptions/best-practices-for-exceptions)   
 [Gestione delle eccezioni](/cpp/windows/exception-handling-cpp-component-extensions)