---
title: BP_FLAGS | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- BP_FLAGS
helpviewer_keywords:
- BP_FLAGS enumeration
ms.assetid: c45dfc74-5e7f-4f1e-a147-ab2a55dccbd0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 481dd21287ba3ca68c2abc61412785fc0151788d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="bpflags"></a>BP_FLAGS
Fornisce flag facoltativo che può essere usato per specificare informazioni aggiuntive durante l'impostazione di un punto di interruzione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
enum enum_BP_FLAGS {   
   BP_FLAG_NONE            = 0x0000,  
   BP_FLAG_MAP_DOCPOSITION = 0x0001,  
   BP_FLAG_DONT_STOP       = 0x0002  
};  
typedef DWORD BP_FLAGS;  
```  
  
```csharp  
public enum enum_BP_FLAGS {   
   BP_FLAG_NONE            = 0x0000,  
   BP_FLAG_MAP_DOCPOSITION = 0x0001,  
   BP_FLAG_DONT_STOP       = 0x0002  
};  
```  
  
## <a name="members"></a>Membri  
 BP_FLAG_NONE  
 Non specifica il flag di alcun punto di interruzione.  
  
 BP_FLAG_MAP_DOCPOSITION  
 Specifica che il motore di debug (DE) deve eseguire il mapping del punto di interruzione utilizzando la posizione del documento. Ciò si applica solo ai punti di interruzione impostati nei file di origine orientata ai servizi di script, ad esempio le pagine ASP (Active Server).  
  
 BP_FLAG_DONT_STOP  
 Specifica che il punto di interruzione deve essere elaborato dal motore di debug, ma che il motore di debug in ultima analisi non deve arrestare vi (vale a dire un [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) oggetto evento non deve essere inviato). Questo flag è progettato per essere utilizzati principalmente con i punti di analisi.  
  
## <a name="remarks"></a>Note  
 Utilizzato per il `dwFlags` appartenente il [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) e [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) strutture.  
  
 Questi valori possono essere combinati con un bit per bit `OR`.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)   
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)