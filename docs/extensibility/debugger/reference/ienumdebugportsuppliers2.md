---
title: IEnumDebugPortSuppliers2 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugPortSuppliers2
helpviewer_keywords:
- IEnumDebugPortSuppliers2
ms.assetid: cd0a73dc-dd25-46fd-8c4f-5b011501afeb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b330be8efb77119d6d78c1478555c9ee5bd6aabc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="ienumdebugportsuppliers2"></a>IEnumDebugPortSuppliers2
Questa interfaccia enumera i fornitori di porte.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IEnumDebugPortSuppliers2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Visual Studio implementa questa interfaccia per rappresentare un elenco di fornitori di porte.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Chiamare [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) per ottenere un elenco di fornitori di porte.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IEnumDebugPortSuppliers2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[avanti](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-next.md)|Recupera un numero specificato di fornitori di porte in una sequenza di enumerazione.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-skip.md)|Ignora un numero specificato di fornitori di porte in una sequenza di enumerazione.|  
|[Reimpostazione](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-reset.md)|Reimposta una sequenza di enumerazione all'inizio.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione come enumerazione corrente.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-getcount.md)|Ottiene il numero di fornitori di porte in un enumeratore.|  
  
## <a name="remarks"></a>Note  
 Un motore di debug in genere non è necessario ottenere questa interfaccia.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)