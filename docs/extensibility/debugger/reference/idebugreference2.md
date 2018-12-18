---
title: IDebugReference2 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugReference2
helpviewer_keywords:
- IDebugReference2 interface
ms.assetid: 3cfed312-f532-4bce-84a5-1677c14567d7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fb5d5d8b3ab6e608a2454847fc9ec27e384777bc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugreference2"></a>IDebugReference2
Questa interfaccia rappresenta un riferimento a una proprietà di frame dello stack o un'altra proprietà.  
  
> [!NOTE]
>  `IDebugReference2` è riservato per utilizzi futuri e tutti i relativi metodi devono restituire `E_NOTIMPL`.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugReference2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 La Germania implementa questa interfaccia per rappresentare un riferimento a un particolare tipo di valore. Ad esempio, il valore può essere un valore numerico come risultato di valutazione di un'espressione, un contesto di memoria utilizzata per la visualizzazione di memoria o un elenco di registri e i relativi valori.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Chiamare [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md) per ottenere questa interfaccia. [GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md) e [GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md) restituire anche questa interfaccia.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugReference2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)|Ottiene il [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) struttura che descrive questo riferimento.|  
|[SetValueAsString](../../../extensibility/debugger/reference/idebugreference2-setvalueasstring.md)|Imposta il valore di questo riferimento da una stringa.|  
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugreference2-setvalueasreference.md)|Imposta il valore di questo riferimento da un altro riferimento.|  
|[EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)|Enumera gli elementi figlio di questo riferimento.|  
|[GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md)|Ottiene l'elemento padre di questo riferimento.|  
|[GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md)|Ottiene il riferimento più derivato di questo riferimento.|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)|Ottiene i byte di memoria a cui fa riferimento questo riferimento.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)|Ottiene il contesto di memoria per questo riferimento.|  
|[GetSize](../../../extensibility/debugger/reference/idebugreference2-getsize.md)|Ottiene le dimensioni, in byte, della Guida di riferimento.|  
|[SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)|Imposta il tipo di riferimento.|  
|[Compare](../../../extensibility/debugger/reference/idebugreference2-compare.md)|Confronta questo riferimento con un altro.|  
  
## <a name="remarks"></a>Note  
  
> [!NOTE]
>  Questo utilizzo di "proprietà" non deve essere confuso con una variabile membro di una classe, che pertanto anche se un `IDebugReference2` può rappresentare tale entità.  
  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) rappresenta una proprietà, mentre `IDebugReference2` rappresenta un riferimento a una proprietà, in genere un riferimento a un oggetto del programma sottoposto a debug.  
  
 La differenza principale tra una proprietà e un riferimento è che una proprietà fa riferimento a un'istanza denominata di un oggetto, mentre un riferimento si riferisce a un'istanza senza nome. Ad esempio, una proprietà può fare riferimento a un oggetto nell'heap del programma da `"a.b"`. Un'altra proprietà può fare riferimento allo stesso oggetto come `"c.d"`. Il modo di fare riferimento a questa proprietà è necessario che `"a.b"` o `"c.d"` nell'ambito. Un riferimento all'oggetto stesso è senza nome; l'oggetto può essere indicato per fino a quando la memoria per l'oggetto è valida.  
  
 Un `IDebugProperty2` interfaccia può essere considerata come un valore con un nome, un tipo e un indirizzo. Un `IDebugReference2`, d'altra parte, può essere considerato come un tipo e un indirizzo.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [getReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)