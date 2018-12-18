---
title: IDebugPropertyField | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPropertyField
helpviewer_keywords:
- IDebugPropertyField interface
ms.assetid: b50edb2c-fb8d-4def-993d-17d23d2027c1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 26b876b19d5242bb90a3d13f255f9245fe14f93a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugpropertyfield"></a>IDebugPropertyField
Questa interfaccia fornisce le funzioni che consentono di ottenere e impostare una proprietà.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugPropertyField : IDebugContainerField  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Un provider di simboli implementa questa interfaccia sullo stesso oggetto che implementa il [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md). Questa interfaccia è una specializzazione che supporta il concetto di proprietà in una classe.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Utilizzare [QueryInterface](/cpp/atl/queryinterface) per questa interfaccia da ottenere il [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) interfaccia se il [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) restituisce `FIELD_KIND_PROP`.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Oltre ai metodi nel [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) e [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) interfacce, questa interfaccia implementa i metodi seguenti:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)|Ottiene il metodo che ottiene la proprietà.|  
|[GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)|Ottiene il metodo che imposta la proprietà.|  
  
## <a name="remarks"></a>Note  
 Una proprietà è un concetto di codice gestito e rappresenta un metodo che viene considerato come una variabile. Proprietà non esistono in C++ gestito.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce del Provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)