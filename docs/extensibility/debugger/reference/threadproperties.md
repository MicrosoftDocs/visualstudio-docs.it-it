---
title: THREADPROPERTIES | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- THREADPROPERTIES
helpviewer_keywords:
- THREADPROPERTIES structure
ms.assetid: 7d397207-db03-4ec0-9f79-3794056ed89f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e4079c688358f3e7deedd28b5eb05e556192bfe6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="threadproperties"></a>THREADPROPERTIES
Vengono descritte le proprietà di un thread.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
typedef struct _tagTHREADPROPERTIES {   
   THREADPROPERTY_FIELDS dwFields;  
   DWORD                 dwThreadId;  
   DWORD                 dwSuspendCount;  
   DWORD                 dwThreadState;  
   BSTR                  bstrPriority;  
   BSTR                  bstrName;  
   BSTR                  bstrLocation;  
} THREADPROPERTIES;  
```  
  
```csharp  
public struct THREADPROPERTIES {   
   public uint   dwFields;  
   public uint   dwThreadId;  
   public uint   dwSuspendCount;  
   public uint   dwThreadState;  
   public string bstrPriority;  
   public string bstrName;  
   public string bstrLocation;  
};  
```  
  
## <a name="members"></a>Membri  
 dwFields  
 Una combinazione di flag dal [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md) enumerazione, che indica quali campi in questa struttura sono validi.  
  
 dwThreadId  
 ID del thread.  
  
 dwSuspendCount  
 Il thread sospendere conteggio.  
  
 dwThreadState  
 Un valore di [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md) enumerazione che indica lo stato del thread operativo.  
  
 bstrPriority  
 Stringa che specifica la priorità di thread. ad esempio, "Superiore al normale", "Normal" o "Ora critiche".  
  
 bstName  
 Il nome del thread.  
  
 bstrLocation  
 Il percorso del thread (in genere il frame dello stack più in alto), in genere espresso come il nome del metodo in esecuzione è attualmente bloccata.  
  
## <a name="remarks"></a>Note  
 Questa struttura viene compilata una chiamata al [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) metodo. Le informazioni restituite pertanto in genere è utilizzate per il popolamento di **thread** finestra.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)   
 [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)   
 [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)