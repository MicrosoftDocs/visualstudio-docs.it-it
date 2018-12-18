---
title: BPRESI_FIELDS | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- BPRESI_FIELDS
helpviewer_keywords:
- BPRESI_FIELDS enumeration
ms.assetid: 99f17b1e-3e67-4f85-89d6-5c6cf45c8008
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1b6ecfd729762944bcf26814e735c4c73841e2d0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="bpresifields"></a>BPRESI_FIELDS
Specifica le informazioni da recuperare su una corretta risoluzione di un punto di interruzione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
enum enum_BPRESI_FIELDS {   
   BPRESI_BPRESLOCATION = 0x0001,  
   BPRESI_PROGRAM       = 0x0002,  
   BPRESI_THREAD        = 0x0004,  
   BPRESI_ALLFIELDS     = 0xffffffff  
};  
typedef DWORD BPRESI_FIELDS;  
```  
  
```csharp  
public enum enum_BPRESI_FIELDS {   
   BPRESI_BPRESLOCATION = 0x0001,  
   BPRESI_PROGRAM       = 0x0002,  
   BPRESI_THREAD        = 0x0004,  
   BPRESI_ALLFIELDS     = 0xffffffff  
};  
```  
  
## <a name="members"></a>Membri  
 BPRESI_BPRESLOCATION  
 Inizializzazione/Usa il `bpResLocation` campo (punto di interruzione risoluzione percorso) della finestra di [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) struttura.  
  
 BPRESI_PROGRAM  
 Inizializzazione/Usa il `pProgram` campo il `BP_RESOLUTION_INFO` struttura.  
  
 BPRESI_THREAD  
 Inizializzazione/Usa il `pThread` campo il `BP_RESOLUTION_INFO` struttura.  
  
 BPRESI_ALLFIELDS  
 Specifica tutti i campi.  
  
## <a name="remarks"></a>Note  
 Passare il [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) metodo per indicare quali campi del [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) struttura devono essere inizializzati.  
  
 Questi flag sono utilizzati anche per indicare quali campi del `BP_RESOLUTION_INFO` struttura sono validi e utilizzate quando viene restituito tale struttura.  
  
 Questi valori possono essere combinati con un bit per bit `OR`.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)