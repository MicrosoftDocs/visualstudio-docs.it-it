---
title: IEnumDebugFields | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugFields
helpviewer_keywords:
- IEnumDebugFields interface
ms.assetid: 403c2a51-3ba5-431f-a1dd-2f3b2046c00c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3a475d7e163cd146a0fd200c1bcac2f3a572ef9e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="ienumdebugfields"></a>IEnumDebugFields
Questa interfaccia rappresenta una raccolta di oggetti che implementano il [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfaccia.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IEnumDebugFields : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Questa interfaccia viene implementata dal provider di simboli per fornire i set di oggetti che implementano il [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfaccia. Si noti che questo non è un'enumerazione standard COM a causa della presenza del [GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md) metodo.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Questa interfaccia viene restituita da [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md) e [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md).  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Questa interfaccia implementa i metodi seguenti.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[avanti](../../../extensibility/debugger/reference/ienumdebugfields-next.md)|Recupera il set successivo di [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) oggetti dall'enumerazione.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugfields-skip.md)|Ignora un numero specificato di voci.|  
|[Reimpostazione](../../../extensibility/debugger/reference/ienumdebugfields-reset.md)|Reimposta l'enumerazione per la prima voce.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugfields-clone.md)|Recupera una copia dell'enumerazione corrente.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md)|Recupera il numero di voci dell'enumerazione.|  
  
## <a name="remarks"></a>Note  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce del Provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)   
 [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)