---
title: BPERESI_FIELDS | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- BPERESI_FIELDS
helpviewer_keywords:
- BPERESI_FIELDS enumeration
ms.assetid: dd7dd89c-1043-46a1-a929-099cc039c344
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2280740766e20a048f57e58590cc529d98b85264
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="bperesifields"></a>BPERESI_FIELDS
Specifica le informazioni da recuperare su una soluzione non riuscita di un punto di interruzione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
enum enum_BPERESI_FIELDS {   
   PERESI_BPRESLOCATION = 0x0001,  
   BPERESI_PROGRAM      = 0x0002,  
   BPERESI_THREAD       = 0x0004,  
   BPERESI_MESSAGE      = 0x0008,  
   BPERESI_TYPE         = 0x0010,  
   BPERESI_ALLFIELDS    = 0xffffffff  
};  
typedef DWORD BPERESI_FIELDS;  
```  
  
```csharp  
public enum enum_BPERESI_FIELDS {   
   PERESI_BPRESLOCATION = 0x0001,  
   BPERESI_PROGRAM      = 0x0002,  
   BPERESI_THREAD       = 0x0004,  
   BPERESI_MESSAGE      = 0x0008,  
   BPERESI_TYPE         = 0x0010,  
   BPERESI_ALLFIELDS    = 0xffffffff  
};  
```  
  
## <a name="members"></a>Membri  
 PERESI_BPRESLOCATION  
 Inizializzazione/Usa il `bpResLocation` campo (punto di interruzione risoluzione percorso) della finestra di [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) struttura.  
  
 BPERESI_PROGRAM  
 Inizializzazione/Usa il `pProgram` campo il `BP_ERROR_RESOLUTION_INFO` struttura.  
  
 BPERESI_THREAD  
 Inizializzazione/Usa il `pThread` campo il `BP_ERROR_RESOLUTION_INFO` struttura.  
  
 BPERESI_MESSAGE  
 Inizializzazione/Usa il `bstrMessage` campo il `BP_ERROR_RESOLUTION_INFO` struttura.  
  
 BPERESI_TYPE  
 Inizializzazione/Usa il `dwType` campo (tipo di punto di interruzione) del `BP_ERROR_RESOLUTION_INFO` struttura.  
  
 BPERESI_ALLFIELDS  
 Tutti i campi di inizializzazione/Usa il `BP_ERROR_RESOLUTION_INFO` struttura.  
  
## <a name="remarks"></a>Note  
 Passato come parametro per il [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) metodo per indicare quali campi del [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) struttura devono essere inizializzati.  
  
 Questi valori vengono utilizzati anche per indicare quali campi nel `BP_ERROR_RESOLUTION_INFO` struttura sono validi e utilizzate quando viene restituito tale struttura.  
  
 Questi valori possono essere combinati con un bit per bit `OR`.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)