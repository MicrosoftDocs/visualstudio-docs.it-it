---
title: PROVIDER_PROCESS_DATA | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- PROVIDER_PROCESS_DATA
helpviewer_keywords:
- PROVIDER_PROCESS_DATA structure
ms.assetid: ec2362ed-4a0c-4a09-9d66-8ff04e4f41ee
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 61b1b5d67faea0ce5c1c2a56b3f411cd4f947067
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="providerprocessdata"></a>PROVIDER_PROCESS_DATA
Questa struttura fornisce informazioni sui processi in esecuzione in un computer.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
typedef struct tagPROVIDER_PROCESS_DATA {  
   PROVIDER_FIELDS    Fields;  
   PROGRAM_NODE_ARRAY ProgramNodes;  
   BOOL               fIsDebuggerPresent;  
} PROVIDER_PROCESS_DATA;  
```  
  
```csharp  
public struct PROVIDER_PROCESS_DATA {  
   public uint               Fields;  
   public PROGRAM_NODE_ARRAY ProgramNodes;  
   public int                fIsDebuggerPresent;  
}  
```  
  
## <a name="members"></a>Membri  
 Campi  
 Una combinazione di flag dal [PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md) enumerazione, che indica quali campi vengono compilati.  
  
 ProgramNodes  
 Oggetto [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md) struttura che contiene una matrice di nodi di programma.  
  
 fIsDebuggerPresent  
 Diverso da zero (`TRUE`) se il [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] debugger è in esecuzione, zero (`FALSE`) in caso contrario.  
  
## <a name="remarks"></a>Note  
 Questa struttura viene passata per il [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) (metodo) in cui viene compilato.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md)   
 [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md)   
 [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)