---
title: DEBUG_ADDRESS | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- DEBUG_ADDRESS
helpviewer_keywords:
- DEBUG_ADDRESS structure
ms.assetid: 79f5e765-9aac-4b6e-82ef-bed88095e9ba
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 07312208967aeccfbd81f44587f84a43dfebf4c0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="debugaddress"></a>DEBUG_ADDRESS
Questa struttura rappresenta un indirizzo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
typedef struct _tagDEBUG_ADDRESS {  
   ULONG32             ulAppDomainID;  
   GUID                guidModule;  
   _mdToken            tokClass;  
   DEBUG_ADDRESS_UNION addr;  
} DEBUG_ADDRESS;  
```  
  
```csharp  
public struct DEBUG_ADDRESS {  
   public uint                ulAppDomainID;  
   public Guid                guidModule;  
   public int                 tokClass;  
   public DEBUG_ADDRESS_UNION addr;  
}  
```  
  
## <a name="terms"></a>Termini  
 ulAppDomainID  
 L'ID del processo.  
  
 guidModule  
 Il GUID del modulo che contiene questo indirizzo.  
  
 tokClass  
 Il token che identifica la classe o un tipo di questo indirizzo.  
  
> [!NOTE]
>  Questo valore è specifico di un provider di simboli e pertanto non ha alcun significato generale diverso come identificatore per un tipo di classe.  
  
 Addr  
 Oggetto [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) struttura, che contiene l'unione di strutture che descrivono i tipi di indirizzo. Il valore `addr`.`dwKind` proviene il [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) enumerazione, che viene illustrato come interpretare l'unione.  
  
## <a name="remarks"></a>Note  
 Questa struttura viene passata per il [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) metodo deve essere compilato.  
  
 **Avviso [solo C++]**  
  
 Se `addr.dwKind` è `ADDRESS_KIND_METADATA_LOCAL` e se `addr.addr.addrLocal.pLocal` non è un valore null, sarà necessario chiamare `Release` sul puntatore token:  
  
```  
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL &&  addr.addr.addrLocal.pLocal != NULL)  
{  
    addr.addr.addrLocal.pLocal->Release();  
}  
```  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)