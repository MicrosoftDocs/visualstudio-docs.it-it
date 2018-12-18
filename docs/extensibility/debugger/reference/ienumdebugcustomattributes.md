---
title: IEnumDebugCustomAttributes | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumCustomAttributes
helpviewer_keywords:
- IEnumDebugCustomAttributes interface
ms.assetid: 11aa768d-1852-44d6-9de3-17f9bafaded2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1f3387a8243a617fc9120c5caa161912e7aa92fd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="ienumdebugcustomattributes"></a>IEnumDebugCustomAttributes
Enumera gli attributi personalizzati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IEnumCustomAttributes : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Un provider di simboli implementa questa interfaccia per supportare gli attributi personalizzati (tramite il [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md) interface).  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md) restituisce questa interfaccia.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IEnumDebugCustomAttributes`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[avanti](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md)|Recupera un numero specificato di attributi personalizzati in una sequenza di enumerazione.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugcustomattributes-skip.md)|Ignora un numero specificato di attributi personalizzati in una sequenza di enumerazione.|  
|[Reimpostazione](../../../extensibility/debugger/reference/ienumdebugcustomattributes-reset.md)|Reimposta una sequenza di enumerazione all'inizio.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugcustomattributes-clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione come enumerazione corrente.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcustomattributes-getcount.md)|Ottiene il numero di attributi personalizzati in un enumeratore.|  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce del Provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)   
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)