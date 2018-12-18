---
title: BP_UNBOUND_REASON | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- BP_UNBOUND_REASON
helpviewer_keywords:
- BP_UNBOUND_REASON enumeration
ms.assetid: 939b6f9c-113b-471d-9f30-b03871af6285
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 65398ac0c4bde18dc772d75ceea203bdbfe3b189
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="bpunboundreason"></a>BP_UNBOUND_REASON
Indica il motivo di che un punto di interruzione è stato associato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
enum enum_BP_UNBOUND_REASON {   
   BPUR_UNKNOWN           = 0x0000,  
   BPUR_CODE_UNLOADED     = 0x0002,  
   BPUR_BREAKPOINT_REBIND = 0x0003,  
   BPUR_BREAKPOINT_ERROR  = 0x0004  
};  
typedef DWORD BP_UNBOUND_REASON;  
```  
  
```csharp  
public enum enum_BP_UNBOUND_REASON {   
   BPUR_UNKNOWN           = 0x0000,  
   BPUR_CODE_UNLOADED     = 0x0002,  
   BPUR_BREAKPOINT_REBIND = 0x0003,  
   BPUR_BREAKPOINT_ERROR  = 0x0004  
};  
```  
  
## <a name="members"></a>Membri  
 BPUR_UNKNOWN  
 Il motivo è sconosciuto.  
  
 BPUR_CODE_UNLOADED  
 Il codice che contiene il punto di interruzione è stato scaricato.  
  
 BPUR_BREAKPOINT_REBIND  
 Il punto di interruzione è stato riassociato a un percorso diverso. Questo può verificarsi dopo la modifica e continuare le operazioni quando si sposta il punto di interruzione, oppure quando il punto di interruzione è associata a un file con un percorso che non è più valido.  
  
 BPUR_ BREAKPOINT_ERROR  
 Il punto di interruzione viene identificato un errore dopo l'associazione. Questo accade per i punti di interruzione gestiti le cui condizioni non sono più validi.  
  
## <a name="remarks"></a>Note  
 Come risultato di [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md) metodo.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)