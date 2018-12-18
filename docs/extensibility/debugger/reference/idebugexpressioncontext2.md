---
title: IDebugExpressionContext2 | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugExpressionContext2
helpviewer_keywords: IDebugExpressionContext2 interface
ms.assetid: 577fdaae-4b2d-4112-9839-ab899535fa6f
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 3d2548e74263b3d6b91ea42ca5a8ec96c64c323f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugexpressioncontext2"></a>IDebugExpressionContext2
Questa interfaccia rappresenta un contesto per la valutazione dell'espressione  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugExpressionContext2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Il motore di debug (DE) implementa questa interfaccia per rappresentare un contesto in cui un'espressione può essere valutata.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Una chiamata a [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) restituisce questa interfaccia. Questa interfaccia è accessibile solo quando il programma in fase di debug è stato sospeso e non è disponibile un frame dello stack.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugExpressionContext2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetName](../../../extensibility/debugger/reference/idebugexpressioncontext2-getname.md)|Recupera il nome del contesto di valutazione.|  
|[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)|Consente di analizzare un'espressione basata su testo per la valutazione.|  
  
## <a name="remarks"></a>Note  
 Un contesto di valutazione può essere considerato come ambito per l'esecuzione di valutazione dell'espressione.  
  
 Quando un programma è stata interrotta, gestore di sessione di debug (SDM) Ottiene uno stack frame dalla Germania con una chiamata a [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md). Chiama quindi il SDM [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) per ottenere il `IDebugExpressionContext2` interfaccia. Questo evento è seguito da una chiamata a [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) per creare un [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) interfaccia che rappresenta l'espressione analizzata pronta per essere valutata.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)   
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)