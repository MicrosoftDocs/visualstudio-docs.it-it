---
title: IDebugStackFrame2 | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugStackFrame2
helpviewer_keywords: IDebugStackFrame2 interface
ms.assetid: bd212a6a-dcc6-4756-a77a-e8dfda38b104
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 457cfc4997ca02ca76b296e3b56fded244629e52
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugstackframe2"></a>IDebugStackFrame2
Questa interfaccia rappresenta un frame di stack singolo in uno stack di chiamate in un particolare thread.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugStackFrame2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Il motore di debug (DE) implementa questa interfaccia per rappresentare uno stack frame.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Chiamare [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) per recuperare un [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) interfaccia. Chiamare [Avanti](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md) per recuperare un [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) struttura che contiene il `IDebugStackFrame2` interfaccia.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugStackFrame2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Ottiene il contesto del codice per questo stack frame.|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Ottiene il contesto di documento per lo stack frame.|  
|[GetName](../../../extensibility/debugger/reference/idebugstackframe2-getname.md)|Ottiene il nome del frame dello stack.|  
|[GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)|Ottiene una descrizione del frame dello stack.|  
|[GetPhysicalStackRange](../../../extensibility/debugger/reference/idebugstackframe2-getphysicalstackrange.md)|Ottiene una rappresentazione dipendenti dal computer dell'intervallo di indirizzi fisici associati a uno stack frame.|  
|[GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)|Ottiene un contesto di valutazione per l'esecuzione di valutazione dell'espressione di un frame dello stack e un thread all'interno del contesto corrente.|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugstackframe2-getlanguageinfo.md)|Ottiene la lingua associata a uno stack frame.|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)|Ottiene una descrizione delle proprietà associata a uno stack frame.|  
|[EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)|Crea un enumeratore per lo stack di proprietà di frame.|  
|[GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)|Ottiene il thread associato a uno stack frame.|  
  
## <a name="remarks"></a>Note  
 Questa interfaccia viene ottenuta solo quando il programma in fase di debug è stato arrestato in un punto di interruzione (sia causato da un punto di interruzione impostato dall'utente o un'eccezione). Da questa interfaccia, è possibile ottenere un contesto di espressione per valutare le espressioni, può essere restituito un elenco di registri o possibile ottenuto ed esaminare lo stack di chiamate.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)