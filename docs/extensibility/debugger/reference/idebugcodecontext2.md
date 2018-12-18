---
title: IDebugCodeContext2 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCodeContext2
helpviewer_keywords:
- IDebugCodeContext2 interface
ms.assetid: 3670439e-2171-405d-9d77-dedb0f1cba93
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5b46ec36a93ac91647a3f17aac28187519ca2447
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugcodecontext2"></a>IDebugCodeContext2
Questa interfaccia rappresenta la posizione iniziale di un'istruzione di codice. Per la maggior parte delle architetture in fase di esecuzione oggi un contesto del codice può essere considerato come un indirizzo nel flusso di esecuzione del programma.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugCodeContext2 : IDebugMemoryContext2  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Il motore di debug implementa questa interfaccia per correlare la posizione di un'istruzione di codice in una posizione del documento.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 In molte interfacce restituiscono questa interfaccia, generalmente, [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md). Viene inoltre utilizzato diffusamente con il [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) interfaccia anche come informazioni sulla risoluzione dei punti di interruzione.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Oltre ai metodi nel [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) interfaccia, implementa i metodi seguenti:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)|Ottiene il contesto del documento che corrisponde al contesto del codice attivo.|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugcodecontext2-getlanguageinfo.md)|Ottiene le informazioni relative alla lingua per il contesto del codice.|  
  
## <a name="remarks"></a>Note  
 La differenza principale tra un `IDebugCodeContext2` interfaccia e un [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) interfaccia è che un `IDebugCodeContext2` è sempre istruzione allineato. Ciò significa che un `IDebugCodeContext2` fa sempre riferimento all'inizio di un'istruzione, mentre un `IDebugMemoryContext2` può puntare a qualsiasi byte di memoria dell'architettura della fase di esecuzione. `IDebugCodeContext2` viene incrementato per istruzioni anziché per le dimensioni di archiviazione di base (in genere byte).  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)   
 [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)   
 [Avanti](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)