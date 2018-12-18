---
title: BP_FLAGS90 | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: BP_FLAGS90 enumeration
ms.assetid: 3e5a06c5-fb30-4b8a-b2d5-4a0570fc80bd
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: af59e06ad31b56c04127ca89b43a903db36d3615
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="bpflags90"></a>BP_FLAGS90
Enumera i valori validi per i flag facoltativo. I flag facoltativi possono essere utilizzati per specificare informazioni aggiuntive quando si imposta un punto di interruzione. Questa enumerazione estende il [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) enumerazione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
enum enum_BP_FLAGS90  
{  
   // VS 8.0 values  
   BP90_FLAG_NONE               = 0x0000,  
   BP90_FLAG_MAP_DOCPOSITION    = 0x0001,  
   BP90_FLAG_DONT_STOP          = 0x0002,  
  
   // Values added in VS 9.0  
   BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,  
};  
typedef DWORD BP_FLAGS90;  
```  
  
```csharp  
public enum enum_BP_FLAGS90  
{  
   // VS 8.0 values  
   BP90_FLAG_NONE                = 0x0000,  
   BP90_FLAG_MAP_DOCPOSITION     = 0x0001,  
   BP90_FLAG_DONT_STOP           = 0x0002,  
  
   // Values added in VS 9.0  
   BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,  
};  
```  
  
#### <a name="parameters"></a>Parametri  
 BP90_FLAG_NONE  
 Non specifica il flag di alcun punto di interruzione.  
  
 BP90_FLAG_MAP_DOCPOSITION  
 Specifica che il motore di debug (DE) deve eseguire il mapping del punto di interruzione utilizzando la posizione del documento. Ciò si applica solo ai punti di interruzione impostati nei file di origine orientata ai servizi di script, ad esempio le pagine ASP (Active Server).  
  
 BP90_FLAG_DONT_STOP  
 Specifica che il punto di interruzione deve essere elaborato dal motore di debug, ma che il motore di debug in ultima analisi non deve arrestare. vale a dire un [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) oggetto evento non deve essere inviato. Questo flag è progettato per essere utilizzati principalmente con i punti di traccia.  
  
 BP90_FLAG_TRACEPOINT_CONTINUE  
 Utilizzato dal motore di debug nativo per determinare se lo stato di avanzamento nell'esecuzione deve essere cancellato. Si differenzia dal BP90_FLAG_DONT_STOP perché BP90_FLAG_DONT_STOP non è impostato se il punto di analisi viene eseguita una macro.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Msdbg90.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)