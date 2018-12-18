---
title: IDebugAddress2 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugAddress2
helpviewer_keywords:
- IDebugAddress2 interface
ms.assetid: b150e0ed-4ac0-4f8c-9732-4b3e54b9d243
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 588b2d3e338080a086fee421deb17760496a268f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugaddress2"></a>IDebugAddress2
Questa interfaccia fornisce accesso all'ID del processo a cui appartiene l'oggetto il cui indirizzo è rappresentato da questa interfaccia.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugAddress2 : IDebugAddress  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Un provider di simboli implementa questa interfaccia sullo stesso oggetto che implementa il [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfaccia. Questa interfaccia fornisce l'accesso all'ID del processo a cui appartiene l'oggetto che è correlato a questo indirizzo.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Utilizzare [QueryInterface](/cpp/atl/queryinterface) per questa interfaccia da ottenere il [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfaccia.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine vtable  
 Oltre ai metodi ereditati dal [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfaccia, implementa il metodo seguente:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetProcessID](../../../extensibility/debugger/reference/idebugaddress2-getprocessid.md)|Recupera l'ID del processo a cui appartiene l'oggetto rappresentato da questa interfaccia.|  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce del Provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)