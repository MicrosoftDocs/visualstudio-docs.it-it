---
title: IEnumDebugAddresses | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugAddresses
helpviewer_keywords:
- IEnumDebugAddresses interface
ms.assetid: 5f6f6751-e6d8-4c5a-8e81-414b6e5d8cc5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bfed705253a03ec550e7533f7e2ab323b7ead62a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="ienumdebugaddresses"></a>IEnumDebugAddresses
Questa interfaccia rappresenta una raccolta di oggetti che implementano il [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfaccia.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IEnumDebugAdresses : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Questa interfaccia viene implementata dal provider di simboli per fornire i set di oggetti che implementano il [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfaccia. Si noti che questo non è un'enumerazione standard COM a causa della presenza del [GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md) metodo.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Questa interfaccia viene restituita da [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md) e [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md).  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Questa interfaccia implementa i metodi seguenti.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[avanti](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md)|Recupera il set successivo di [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) oggetti dall'enumerazione.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugaddresses-skip.md)|Ignora un numero specificato di voci.|  
|[Reimpostazione](../../../extensibility/debugger/reference/ienumdebugaddresses-reset.md)|Reimposta l'enumerazione per la prima voce.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugaddresses-clone.md)|Recupera una copia dell'enumerazione corrente.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md)|Recupera il numero di voci dell'enumerazione.|  
  
## <a name="remarks"></a>Note  
 Questa interfaccia viene generalmente utilizzata dal motore di debug per determinare l'indirizzo appropriato per consentire l'analizzatore di espressioni.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce del Provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)   
 [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)