---
title: ATTACH_REASON | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- ATTACH_REASON
helpviewer_keywords:
- ATTACH_REASON enumeration
ms.assetid: 159fb70b-a344-4ba6-9115-b7eaa16e228f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2dc7736f9210ef15cec8cece45d7899cc116a334
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="attachreason"></a>ATTACH_REASON
Specifica il motivo per il motore di debug (DE) da associare a un nodo di programma.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
enum enum_ATTACH_REASON {   
   ATTACH_REASON_LAUNCH = 0x0001,  
   ATTACH_REASON_USER   = 0x0002,  
   ATTACH_REASON_AUTO   = 0x0003  
};  
typedef DWORD ATTACH_REASON;  
```  
  
```csharp  
public enum enum_ATTACH_REASON {   
   ATTACH_REASON_LAUNCH = 0x0001,  
   ATTACH_REASON_USER   = 0x0002,  
   ATTACH_REASON_AUTO   = 0x0003  
};  
```  
  
## <a name="members"></a>Membri  
 ATTACH_REASON_AUTO  
 Collegare poiché il processo è attualmente in modalità di debug.  
  
 ATTACH_REASON_LAUNCH  
 Collegare perché è stato avviato il processo.  
  
 ATTACH_REASON_USER  
 Collegare a causa di una richiesta dell'utente.  
  
## <a name="remarks"></a>Note  
 Questi valori vengono utilizzati come parametro per il [collegamento](../../../extensibility/debugger/reference/idebugengine2-attach.md) e [collegamento](../../../extensibility/debugger/reference/idebugprogramex2-attach.md) metodi.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Collegare](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [Attach](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)