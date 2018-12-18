---
title: I programmi | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], programs
- programs, debugging
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 03b4885e653d879e3aaec1d9a68bc9be144cb676
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="programs"></a>Programs
In termini di architettura del debugger, un **programma**:  
  
-   È un contenitore per un set di thread e un set di moduli. Un programma non ha analogia singolo nel sistema operativo Windows.  
  
     Un programma è un tipo di processo secondario. Ad esempio, quando si esegue il debug di un sito Web, uno script può essere considerato un programma. Durante l'esecuzione di uno script nel processo del motore di scripting, indipendente da altri script, include anche un proprio set di thread. Un motore di debug (DE) viene associato a un programma e non a un processo o un thread.  
  
-   Consente di identificare se stesso e il processo è in esecuzione in e deve essere collegata a scollegati da e descrivere DE che lo ha creato, se presente. Un programma possa eseguire, arrestare, continuare e terminato.  
  
-   Possibile enumerare tutti i relativi thread. Un programma può fornire anche il flusso di disassembly e possa enumerare tutti i contesti di codice di una posizione del documento specificato.  
  
-   È rappresentato da un [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) interfaccia, creata prima il programma è collegato o come parte del processo di collegamento, a seconda dell'implementazione. Quando una porta enumera i programmi di un processo, ogni programma è stato creato in base a un corrispondente [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) interfaccia passata come argomento per [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Mentre i motori di debug anche creare `IDebugProgram2` interfacce per rappresentare i programmi, questi programmi non vengono create in base a un nodo di programma. Il `IDebugProgramNode2` interfacce create da un DE vengono utilizzate per il debug effettivo, mentre quelli creati da una porta sono utilizzati solo per l'individuazione quali programmi sono in esecuzione in un processo.  
  
## <a name="see-also"></a>Vedere anche  
 [Processi](../../extensibility/debugger/processes.md)   
 [Nodi di programma](../../extensibility/debugger/program-nodes.md)   
 [Moduli](../../extensibility/debugger/modules.md)   
 [Concetti di debugger](../../extensibility/debugger/debugger-concepts.md)   
 [Motore di debug](../../extensibility/debugger/debug-engine.md)   
 [Posizione di documento](../../extensibility/debugger/document-position.md)   
 [Contesto del codice](../../extensibility/debugger/code-context.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)