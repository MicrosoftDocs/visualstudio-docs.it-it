---
title: BPREQI_FIELDS90 | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: BPREQI_FIELDS90 enumeration
ms.assetid: bf6f7efc-39f2-46a2-906d-c3647bf89995
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1988bbe5262bc6a4807a6068adf45f381ccf4296
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="bpreqifields90"></a>BPREQI_FIELDS90
Enumera i valori validi che specificano le informazioni da recuperare una richiesta di punto di interruzione. Questa enumerazione estende il [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) enumerazione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
enum enum_BPREQI_FIELDS90  
{  
   // VS 8.0 values  
   BPREQI90_BPLOCATION                = 0x0001,  
   BPREQI90_LANGUAGE                  = 0x0002,  
   BPREQI90_PROGRAM                   = 0x0004,  
   BPREQI90_PROGRAMNAME               = 0x0008,  
   BPREQI90_THREAD                    = 0x0010,  
   BPREQI90_THREADNAME                = 0x0020,  
   BPREQI90_PASSCOUNT                 = 0x0040,  
   BPREQI90_CONDITION                 = 0x0080,  
   BPREQI90_FLAGS                     = 0x0100,  
   BPREQI90_ALLOLDFIELDS              = 0x01ff,  
   BPREQI90_VENDOR                    = 0x0200,  
   BPREQI90_CONSTRAINT                = 0x0400,  
   BPREQI90_TRACEPOINT                = 0x0800,  
  
   // Values added in VS 9.0  
   BPREQI90_MACROTRACEPOINT           = 0x1000,  
  
   BPREQI90_ALLFIELDS                 = 0xffff  
};  
typedef DWORD BPREQI_FIELDS90;  
```  
  
```csharp  
public enum enum_BPREQI_FIELDS90  
{  
    // VS 8.0 values  
    BPREQI90_BPLOCATION                = 0x0001,  
    BPREQI90_LANGUAGE                  = 0x0002,  
    BPREQI90_PROGRAM                   = 0x0004,  
    BPREQI90_PROGRAMNAME               = 0x0008,  
    BPREQI90_THREAD                    = 0x0010,  
    BPREQI90_THREADNAME                = 0x0020,  
    BPREQI90_PASSCOUNT                 = 0x0040,  
    BPREQI90_CONDITION                 = 0x0080,  
    BPREQI90_FLAGS                     = 0x0100,  
    BPREQI90_ALLOLDFIELDS              = 0x01ff,  
    BPREQI90_VENDOR                    = 0x0200,  
    BPREQI90_CONSTRAINT                = 0x0400,  
    BPREQI90_TRACEPOINT                = 0x0800,  
  
    // Values added in VS 9.0  
    BPREQI90_MACROTRACEPOINT           = 0x1000,  
  
    BPREQI90_ALLFIELDS                 = 0xffff  
};  
```  
  
#### <a name="parameters"></a>Parametri  
 BPREQI90_BPLOCATION  
 Inizializzare o utilizzare il `bpLocation` campo (posizione punto di interruzione) del [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) o [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) struttura.  
  
 BPREQI90_LANGUAGE  
 Inizializzare o utilizzare il `guidLanguage` campo il `BP_REQUEST_INFO` o `BP_REQUEST_INFO2` struttura.  
  
 BPREQI90_PROGRAM  
 Inizializzare o utilizzare il `pProgram` campo il `BP_REQUEST_INFO` o `BP_REQUEST_INFO2` struttura.  
  
 BPREQI90_PROGRAMNAME  
 Inizializzare o utilizzare il `bstrProgramName` campo il `BP_REQUEST_INFO` o `BP_REQUEST_INFO2` struttura.  
  
 BPREQI90_THREAD  
 Inizializzare o utilizzare il `pThread` campo il `BP_REQUEST_INFO` o `BP_REQUEST_INFO2` struttura.  
  
 BPREQI90_THREADNAME  
 Inizializzare o utilizzare il `bstrThreadName` campo il `BP_REQUEST_INFO` o `BP_REQUEST_INFO2` struttura.  
  
 BPREQI90_PASSCOUNT  
 Inizializzare o utilizzare il `bpPassCount` campo il `BP_REQUEST_INFO` o `BP_REQUEST_INFO2` struttura.  
  
 BPREQI90_CONDITION  
 Inizializzare o utilizzare il `bpCondition` campo (condizione punto di interruzione) del `BP_REQUEST_INFO` o `BP_REQUEST_INFO2` struttura.  
  
 BPREQI90_FLAGS  
 Inizializzare o utilizzare il `dwFlags` campo il `BP_REQUEST_INFO` o `BP_REQUEST_INFO2` struttura.  
  
 BPREQI90_ALLOLDFIELDS  
 Inizializzare o utilizzare tutti i campi per il del `BP_REQUEST_INFO` struttura.  
  
 BPREQI90_VENDOR  
 Inizializzare o utilizzare il `guidVendor` campo `BP_REQUEST_INFO2` struttura.  
  
 BPREQI90_CONSTRAINT  
 Inizializzare o utilizzare il `bstrConstraint` campo `BP_REQUEST_INFO2` struttura.  
  
 BPREQI90_TRACEPOINT  
 Inizializzare o utilizzare il `bstrTracepoint` campo `BP_REQUEST_INFO2` struttura.  
  
 BPREQI90_MACROTRACEPOINT  
 Inizializzare o utilizzare il `bstrMacroTracepoint` campo `BP_REQUEST_INFO2` struttura. BPREQI_ALLFIELDS non include questo campo.  
  
 BPREQI90_ALLFIELDS  
 Specifica tutti i campi per il `BP_REQUEST_INFO2` struttura.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Msdbg90.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)