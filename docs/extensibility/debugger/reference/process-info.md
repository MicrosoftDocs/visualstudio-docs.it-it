---
title: PROCESS_INFO | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- PROCESS_INFO
helpviewer_keywords:
- PROCESS_INFO structure
ms.assetid: 260c33cc-a05e-4645-84b6-536d0b3b0537
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d35b94b6153b65672453ed8b4e7d2c0d9c2bd5eb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="processinfo"></a>PROCESS_INFO
Contiene informazioni su un processo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
typedef struct tagPROCESS_INFO {   
   PROCESS_INFO_FIELDS Fields;  
   BSTR                bstrFileName;  
   BSTR                bstrBaseName;  
   BSTR                bstrTitle;  
   AD_PROCESS_ID       ProcessId;  
   DWORD               dwSessionId;  
   BSTR                bstrAttachedSessionName;  
   FILETIME            CreationTime;  
   PROCESS_INFO_FLAGS  Flags;  
} PROCESS_INFO;  
```  
  
```csharp  
public struct PROCESS_INFO {   
   public uint          Fields;  
   public string        bstrFileName;  
   public string        bstrBaseName;  
   public string        bstrTitle;  
   public AD_PROCESS_ID ProcessId;  
   public uint          dwSessionId;  
   public string        bstrAttachedSessionName;  
   public FILETIME      CreationTime;  
   public uint          Flags;  
};  
```  
  
## <a name="members"></a>Membri  
 Campi  
 Una combinazione di flag dal [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md) enumerazione che specificano quali campi vengono compilati.  
  
 bstrFileName  
 Nome e percorso completo del processo. Equivalente alla chiamata di [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) (metodo) con il parametro `GN_FILENAME`.  
  
 bstrBaseName  
 Il nome del file e l'estensione del processo. Equivalente alla chiamata di `IDebugProcess2::Getname` (metodo) con il parametro `GN_BASENAME`.  
  
 bstrTitle  
 Il titolo del processo, se presente. Equivalente alla chiamata di `IDebugProcess2::Getname` (metodo) con il parametro `GN_TITLE`.  
  
 ProcessId  
 Il [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) struttura che identifica il processo. Equivalente alla chiamata di [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md) metodo.  
  
 dwSessionId  
 Identificatore della sessione di debug che questo processo è in esecuzione in.  
  
 bstrAttachedSessionName  
 Il nome della sessione associata. Equivalente alla chiamata di [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md) metodo.  
  
 CreationTime  
 L'ora in cui è stato creato il processo.  
  
 Flag  
 Una combinazione di flag dal [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md) enumerazione che specificano proprietà del processo.  
  
## <a name="remarks"></a>Note  
 Questa struttura viene passata per il [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) (metodo) in cui viene compilato.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)   
 [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)   
 [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)   
 [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)   
 [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)