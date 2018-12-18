---
title: Continuazione dell'esecuzione dopo un'eccezione | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- managed exceptions, continuing execution after
- exceptions, continuing execution after
- debugger, exceptions
- managed code, exception handling
- exception handling, continuing execution after
- execution, continuing after an exception
- program execution
- threading [Visual Studio], continuing execution after exceptions
- Exceptions dialog box
- programs, executing
ms.assetid: 6fe97aac-2131-4615-bd92-d3afee741558
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1b26fe427ba83eea9e989e492fde89ade498a114
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="continuing-execution-after-an-exception"></a>Continuazione dell'esecuzione dopo un'eccezione
Quando il debugger interrompe l'esecuzione a causa di un'eccezione, verrà visualizzato il **supporto eccezioni**, per impostazione predefinita. Se è stata disabilitata la **supporto eccezioni** nel **opzioni** nella finestra di dialogo verrà visualizzato il **eccezioni** (in c# o Visual Basic) o **eccezione**  la finestra di dialogo (C++).  
  
 Quando il **supporto eccezioni** viene visualizzata, è possibile provare a risolvere il problema che ha causato l'eccezione.
  
## <a name="managed-and-native-code"></a>Codice gestito e nativo  
 Nel codice gestito e nativo, è possibile continuare l'esecuzione nello stesso thread dopo un'eccezione non gestita. Il **supporto eccezioni** rimuove lo stack di chiamate al punto in cui è stata generata l'eccezione.
  
## <a name="mixed-code"></a>Codice misto  
 Se si rileva un'eccezione non gestita durante il debug di codice misto nativo e gestito, i vincoli del sistema operativo impediscono la rimozione dello stack di chiamate. Se si tenta di rimuovere lo stack di chiamate utilizzando il menu di scelta rapida, un messaggio di errore indica che il debugger non può eseguire la rimozione da un'eccezione non gestita durante il debug di codice misto.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione delle eccezioni con il Debugger](../debugger/managing-exceptions-with-the-debugger.md)