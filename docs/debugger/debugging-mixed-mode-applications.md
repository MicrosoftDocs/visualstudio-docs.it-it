---
title: "Debug di applicazioni in modalità mista | Documenti Microsoft"
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
- debugging [Visual Studio], mixed-mode
- mixed-mode debugging, property evaluation
- Call Stack window
- mixed-mode debugging
- Call Stack window, mixed-mode debugging
- debugging managed code, mixed code
- mixed-mode debugging, call stack
ms.assetid: 60e34477-ae4e-48c7-9093-3e37f72e1bc3
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 2870f1b74532b181ae2101ae01a0e95b494f6f61
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="debugging-mixed-mode-applications"></a>Debug delle applicazioni in modalità mista
Un'applicazione in modalità mista combina codice nativo (C++) con codice gestito, ad esempio Visual Basic, Visual C# o C++ eseguito in Common Language Runtime. Il debug di applicazioni in modalità mista è ampiamente trasparente in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e non è molto diverso dal debug di un'applicazione in modalità singola. È tuttavia necessario fare alcune considerazioni specifiche.  
  
## <a name="enable-c-edit-and-continue-in-mixed-mode-debugging"></a>Abilitare la funzione di modifica e continuazione di C++ nel debug in modalità mista  
  
-   Per utilizzare Modifica e continuazione per C++ in Visual Studio 2013, è necessario ripristinare il motore di debug legacy. Vedere [passando alla modalità di compatibilità gestita in Visual Studio 2013](http://blogs.msdn.com/b/visualstudioalm/archive/2013/10/16/switching-to-managed-compatibility-mode-in-visual-studio-2013.aspx) sul blog di Microsoft Application Lifecycle Management.  
  
## <a name="property-evaluation-in-mixed-mode-applications"></a>Valutazione delle proprietà nelle applicazioni in modalità mista  
 In un'applicazione in modalità mista la valutazione delle proprietà tramite il debugger è un'operazione complessa. Di conseguenza, alcune operazioni di debug, ad esempio il debug passo a passo, possono risultare lente. Per ulteriori informazioni, vedere [esecuzione](http://msdn.microsoft.com/en-us/8791dac9-64d1-4bb9-b59e-8d59af1833f9). Se nel debug in modalità mista le prestazioni non risultano soddisfacenti, disattivare la valutazione delle proprietà nelle finestre del debugger.  
  
> [!NOTE]
>  Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
#### <a name="to-turn-off-property-evaluation"></a>Per disattivare la valutazione delle proprietà  
  
1.  Scegliere **Opzioni** dal menu **Strumenti**.  
  
2.  Nel **opzioni** la finestra di dialogo, aprire il **debug** cartella e selezionare il **generale** categoria.  
  
3.  Cancella il **Attiva valutazione delle proprietà e altre chiamate di funzioni implicite** casella di controllo.  
  
 Poiché gli stack di chiamate native sono diversi dagli stack di chiamate gestite, il debugger non può sempre fornire lo stack di chiamate completate per il codice misto. Quando il codice nativo chiama il codice gestito, possono essere presenti alcune differenze. Per ulteriori informazioni, vedere [codice misto e informazioni mancanti nella finestra Stack di chiamate](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di codice gestito](../debugger/debugging-managed-code.md)