---
title: Thread | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a2754d3b1b15771f876855e7ca7d1dc510748308
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="threads"></a>Thread
In termini di architettura del debugger, un **thread**:  
  
-   È l'unità fondamentale di calcolo. Un thread esegue in sequenza le istruzioni all'interno del contesto di un singolo stack di chiamate, passare dal contesto di un codice al successivo.  
  
-   Consente di identificare se stesso e il programma è in esecuzione in e può essere denominato, sospesa e ripresa. Un thread possibile enumerare relativi frame dello stack associato e, in alcune condizioni, può essere spostato in un altro stack frame. Fornito il contesto di uno stack frame, un thread può restituire il relativo thread logico associato, se presente. Un thread contiene proprietà, ad esempio un conteggio di sospensione, che possono essere visualizzati nella finestra thread dell'IDE.  
  
-   È rappresentato da un [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) interfaccia, in genere creata da un motore di debug (DE) o di una macchina virtuale determina l'esecuzione di un programma.  
  
## <a name="see-also"></a>Vedere anche  
 [Programmi](../../extensibility/debugger/programs.md)   
 [Stack frame](../../extensibility/debugger/stack-frames.md)   
 [Motore di debug](../../extensibility/debugger/debug-engine.md)   
 [Concetti di debugger](../../extensibility/debugger/debugger-concepts.md)   
 [Gestione del debug delle sessioni](../../extensibility/debugger/session-debug-manager.md)