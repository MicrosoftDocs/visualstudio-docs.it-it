---
title: Modifica e continuazione di finestra di messaggio di errore | Documenti Microsoft
ms.custom: ''
ms.date: 06/22/2017
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.ENC.SupportedButNotAvaiable
- vs.debug.ENC.CannotEditWhileException
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue Error Message dialog box
ms.assetid: f98c91c0-447a-4533-85b6-87170a0dc4c3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5b521eafcc62a49f2dd2a4c327158070bdbe62ce
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="edit-and-continue-error-message-dialog-box"></a>Finestra di dialogo di errore di Modifica e continuazione
Questa finestra di dialogo viene visualizzata quando si esegue il debug in un linguaggio che supporta la modifica e continuazione, ma **modifica e continuazione** non è disponibile per il tipo di sono state apportate modifiche al codice. Nel messaggio di errore sono riportate informazioni più dettagliate. Questa finestra di dialogo può essere visualizzata per uno dei seguenti motivi:  

-   Si è tentato di modificare il codice di SQL Server.

-   Si è tentato di modificare il codice ottimizzato. (Potrebbe essere necessario passare da una build di rilascio a una build di debug)

-   Si è tentato di modificare il codice durante l'esecuzione (invece che durante la sospensione del debugger). Provare a [impostando un punto di interruzione](../debugger/using-breakpoints.md) e la modifica del codice durante la sospensione.

-   Si è tentato di modificare il codice gestito mentre era abilitato il debug di codice non gestito. Modifica e continuazione non funziona con [debug in modalità mista](../debugger/how-to-debug-in-mixed-mode.md).

-   Responsabile di un codice di modifica che non è supportata da modifica e continuazione nel linguaggio di programmazione. Per altre informazioni, vedere gli argomenti per modifiche al codice non supportato in [c#](../debugger/supported-code-changes-csharp.md), [Visual Basic](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md), e [C++](../debugger/supported-code-changes-cpp.md).
  
-   Si è tentato di modificare il codice in un programma che si era connessi anziché avviandolo dal **Debug** menu.  
  
-   Si è tentato di modificare il codice durante il debug di un dump di Dr. Watson.  
  
-   Si è tentato di modificare il codice dopo un'eccezione non gestita e l'opzione "**Rimuovi stack di chiamate su eccezioni non gestite**" non è stata selezionata.  
  
-   Si è tentato di modificare il codice durante il debug di un'applicazione di runtime incorporata.
  
-   Si è tentato di modificare il codice gestito utilizzando la versione di .NET Framework prima 4.5.1 e la destinazione è un'applicazione a 64 bit. Se si desidera utilizzare Modifica e continuazione, è necessario impostare la destinazione su x86 (*projectname* **proprietà**, **compilare** scheda **del compilatore avanzate** impostazione.).  
  
-   Si è tentato di modificare il codice in un assembly modificato durante il debug e ricaricato.  
  
-   Si è tentato di modificare il codice in un assembly che non è stato caricato.  
  
-   Si è avviato il debug di una versione precedente dell'applicazione, poiché la nuova versione presenta errori di compilazione.
  
## <a name="uielement-list"></a>Elenco UIElement  
 **OK**  
 Chiudere la finestra di dialogo e annullare il tentativo di modifica immediatamente precedente.  
  
## <a name="see-also"></a>Vedere anche  
 [C++ Modifica e continuazione blog post](https://blogs.msdn.microsoft.com/vcblog/2016/07/01/c-edit-and-continue-in-visual-studio-2015-update-3/)  
 [Modifiche al codice supportate (C++)](../debugger/supported-code-changes-cpp.md)