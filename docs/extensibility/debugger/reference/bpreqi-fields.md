---
title: BPREQI_FIELDS | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- BPREQI_FIELDS
helpviewer_keywords:
- BPREQI_FIELDS enumeration
ms.assetid: 679e771e-4a79-484e-af37-f962ef4aa245
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ff66a2c23f96ad083d84a937a45c1b2b8cf3ddec
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="bpreqifields"></a>BPREQI_FIELDS
Specifica le informazioni da recuperare su una richiesta di punto di interruzione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
enum enum_BPREQI_FIELDS {   
   BPREQI_BPLOCATION   = 0x0001,  
   BPREQI_LANGUAGE     = 0x0002,  
   BPREQI_PROGRAM      = 0x0004,  
   BPREQI_PROGRAMNAME  = 0x0008,  
   BPREQI_THREAD       = 0x0010,  
   BPREQI_THREADNAME   = 0x0020,  
   BPREQI_PASSCOUNT    = 0x0040,  
   BPREQI_CONDITION    = 0x0080,  
   BPREQI_FLAGS        = 0x0100,  
   BPREQI_ALLOLDFIELDS = 0x01ff  
   BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only  
   BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only  
   BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only  
   BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only  
};  
typedef DWORD BPREQI_FIELDS;  
```  
  
```csharp  
public enum enum_BPREQI_FIELDS {   
   BPREQI_BPLOCATION   = 0x0001,  
   BPREQI_LANGUAGE     = 0x0002,  
   BPREQI_PROGRAM      = 0x0004,  
   BPREQI_PROGRAMNAME  = 0x0008,  
   BPREQI_THREAD       = 0x0010,  
   BPREQI_THREADNAME   = 0x0020,  
   BPREQI_PASSCOUNT    = 0x0040,  
   BPREQI_CONDITION    = 0x0080,  
   BPREQI_FLAGS        = 0x0100,  
   BPREQI_ALLOLDFIELDS = 0x01ff  
   BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only  
   BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only  
   BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only  
   BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only  
};  
```  
  
## <a name="members"></a>Membri  
 BPREQI_BPLOCATION  
 Inizializzazione/Usa il `bpLocation` campo (posizione punto di interruzione) del [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) o [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) struttura.  
  
 BPREQI_LANGUAGE  
 Inizializzazione/Usa il `guidLanguage` campo il `BP_REQUEST_INFO` o `BP_REQUEST_INFO2` struttura.  
  
 BPREQI_PROGRAM  
 Inizializzazione/Usa il `pProgram` campo il `BP_REQUEST_INFO` o `BP_REQUEST_INFO2` struttura.  
  
 BPREQI_PROGRAMNAME  
 Inizializzazione/Usa il `bstrProgramName` campo il `BP_REQUEST_INFO` o `BP_REQUEST_INFO2` struttura.  
  
 BPREQI_THREAD  
 Inizializzazione/Usa il `pThread` campo il `BP_REQUEST_INFO` o `BP_REQUEST_INFO2` struttura.  
  
 BPREQI_THREADNAME  
 Inizializzazione/Usa il `bstrThreadName` campo il `BP_REQUEST_INFO` o `BP_REQUEST_INFO2` struttura.  
  
 BPREQI_PASSCOUNT  
 Inizializzazione/Usa il `bpPassCount` campo il `BP_REQUEST_INFO` o `BP_REQUEST_INFO2` struttura.  
  
 BPREQI_CONDITION  
 Inizializzazione/Usa il `bpCondition` campo (condizione punto di interruzione) del `BP_REQUEST_INFO` o `BP_REQUEST_INFO2` struttura.  
  
 BPREQI_FLAGS  
 Inizializzazione/Usa il `dwFlags` campo il `BP_REQUEST_INFO` o `BP_REQUEST_INFO2` struttura.  
  
 BPREQI_ALLOLDFIELDS  
 Inizializzazione/Usa tutti i campi per il del `BP_REQUEST_INFO` struttura.  
  
 BPREQI_VENDOR  
 Inizializzazione/Usa il `guidVendor` campo `BP_REQUEST_INFO2` struttura.  
  
 BPREQI_CONSTRAINT  
 Inizializzazione/Usa il `bstrConstraint` campo `BP_REQUEST_INFO2` struttura.  
  
 BPREQI_TRACEPOINT  
 Inizializzazione/Usa il `bstrTracepoint` campo `BP_REQUEST_INFO2` struttura.  
  
 BPREQI_ALLFIELDS  
 Specifica tutti i campi per il `BP_REQUEST_INFO2` struttura.  
  
## <a name="remarks"></a>Note  
 Passata come argomento per il [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) e [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) metodi per specificare quali campi del [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) e [BP_REQUEST_INFO2 ](../../../extensibility/debugger/reference/bp-request-info2.md) strutture sono da inizializzare.  
  
 Questi flag sono utilizzati anche per indicare quali campi del `BP_REQUEST_INFO` e `BP_REQUEST_INFO2` strutture sono validi e utilizzate quando viene restituito ogni struttura.  
  
 Questi valori possono essere combinati con un bit per bit `OR`.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)