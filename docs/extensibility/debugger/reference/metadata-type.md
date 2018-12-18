---
title: METADATA_TYPE | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: METADATA_TYPE
helpviewer_keywords: METADATA_TYPE structure
ms.assetid: 2d8b78f6-0aef-4d79-809a-cff9b2c24659
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 15f284a99c6382423bfb61cab105ff8e91129ac9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="metadatatype"></a>METADATA_TYPE
Questa struttura consente di specificare informazioni su un tipo di campo prelevato dai metadati.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
typedef struct _tagTYPE_METADATA {  
   ULONG32  ulAppDomainID;  
   GUID     guidModule;  
   _mdToken tokClass;  
} METADATA_TYPE;  
```  
  
```csharp  
public struct METADATA_TYPE {  
   public uint ulAppDomainID;  
   public Guid guidModule;  
   public int  tokClass;  
};  
```  
  
#### <a name="parameters"></a>Parametri  
 ulAppDomainID  
 ID dell'applicazione da cui proviene il simbolo. Questo viene utilizzato per identificare in modo univoco un'istanza dell'applicazione.  
  
 guidModule  
 Il GUID del modulo che contiene questo campo.  
  
 tokClass  
 L'ID del token dei metadati di questo tipo.  
  
 [C++] `_mdToken` è un `typedef` un 32-bit `int`.  
  
## <a name="remarks"></a>Note  
 Questa struttura viene visualizzato come parte dell'unione nel [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) struttura quando il `dwKind` campo il `TYPE_INFO` struttura è impostata su `TYPE_KIND_METADATA` (compreso il [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) enumerazione).  
  
 Il `tokClass` valore è un token di metadati che identifica in modo univoco un tipo. Per informazioni dettagliate su come interpretare i bit superiori di ID del token di metadati, vedere il `CorTokenType` enumerazione nel file corhdr. h di [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] SDK.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)