---
title: La valutazione dello Stack di chiamate | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], call stack evaluation
- call stacks, evaluation
ms.assetid: 373d6b49-0459-4cce-816e-05745a44fe49
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fddbe370362eb30dd9560e51574847d808c126fd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="call-stack-evaluation"></a>Valutazione dello Stack di chiamate
Per visualizzare gli stack frame dello stack di chiamate durante la modalità di interruzione, è necessario implementare la [EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) metodo.  
  
## <a name="methods-for-evaluation"></a>Metodi per la valutazione  
 Per un motore di debug semplice (DE), potrebbe esserci un solo frame dello stack. Per esaminare lo stack frame in modalità di interruzione, è necessario implementare i metodi seguenti della [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md).  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Ottiene il contesto del codice per uno stack frame. Il contesto del codice rappresenta il puntatore all'istruzione corrente in uno stack frame.|  
|[GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Ottiene il contesto di documento per uno stack frame. Il contesto del documento rappresenta la posizione corrente nel codice sorgente per uno stack frame. Necessario per la visualizzazione del codice sorgente nel caso di interruzione in un programma.|  
  
 Questi metodi richiedono l'implementazione dei diversi metodi e interfacce correlate al contesto. Di conseguenza, è necessario implementare la [GetDocumentContext](../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) metodo e i metodi seguenti della [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md).  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Ottiene l'intervallo di istruzione del file di un contesto di documento.|  
  
 Per enumerare i contesti di codice, è necessario implementare tutti i metodi di [IEnumDebugCodeContexts2](../../extensibility/debugger/reference/ienumdebugcodecontexts2.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Controllo dell'esecuzione e valutazione dello stato](../../extensibility/debugger/execution-control-and-state-evaluation.md)