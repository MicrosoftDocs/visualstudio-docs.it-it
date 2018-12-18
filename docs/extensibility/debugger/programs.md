---
title: I programmi | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], programs
- programs, debugging
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dd3d1c1e72524c393fdb3adc4477ea9ae374fbfa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
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