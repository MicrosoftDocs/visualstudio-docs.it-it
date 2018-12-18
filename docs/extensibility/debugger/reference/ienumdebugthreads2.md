---
title: IEnumDebugThreads2 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugThreads2
helpviewer_keywords:
- IEnumDebugThreads2
ms.assetid: 1854f078-3b49-42c2-b65b-33e3b506fd63
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3405a8ab52591e79f5a865016b68c69c61e6cf8b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="ienumdebugthreads2"></a>IEnumDebugThreads2
Questo Interfacc enumera i thread in esecuzione nella sessione di debug corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IEnumDebugThreads2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Il motore di debug (DE) implementa questa interfaccia per rappresentare un elenco di thread in un programma.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Chiamare [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md) per ottenere l'interfaccia che rappresenta un elenco di tutti i thread in tutti i programmi in esecuzione in un processo. Chiamare [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) per ottenere l'interfaccia che rappresenta un elenco di thread in esecuzione in un programma.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IEnumDebugThreads2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[avanti](../../../extensibility/debugger/reference/ienumdebugthreads2-next.md)|Recupera un numero specificato di thread nella sequenza di enumerazione.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugthreads2-skip.md)|Ignora un numero specificato di thread in una sequenza di enumerazione.|  
|[Reimpostazione](../../../extensibility/debugger/reference/ienumdebugthreads2-reset.md)|Reimposta una sequenza di enumerazione all'inizio.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugthreads2-clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione del nodo corrente.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugthreads2-getcount.md)|Ottiene il numero di thread in un enumeratore.|  
  
## <a name="remarks"></a>Note  
 Visual Studio ottiene in genere questa interfaccia per l'aggiornamento di **thread** finestra nonché per ottenere il primo thread dell'elenco, per poter chiamare [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md), [continua](../../../extensibility/debugger/reference/idebugprocess3-continue.md), e [Passaggio](../../../extensibility/debugger/reference/idebugprocess3-step.md).  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)   
 [Passaggio](../../../extensibility/debugger/reference/idebugprocess3-step.md)   
 [Continuare](../../../extensibility/debugger/reference/idebugprocess3-continue.md)   
 [Eseguire](../../../extensibility/debugger/reference/idebugprocess3-execute.md)