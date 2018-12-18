---
title: DEBUGREF_INFO_FLAGS | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- DEBUGREF_INFO_FLAGS
helpviewer_keywords:
- DEBUGREF_INFO_FLAGS enumeration
ms.assetid: 1b043327-302a-4f6d-b51d-f94f9d7c7f9d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f5864b3503b19e8a473f45e4167aad835181da50
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="debugrefinfoflags"></a>DEBUGREF_INFO_FLAGS
Specifica le informazioni da recuperare su un oggetto di riferimento di debug.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
enum enum_DEBUGREF_INFO_FLAGS {   
   DEBUGREF_INFO_NAME             = 0x00000001,  
   DEBUGREF_INFO_TYPE             = 0x00000002,  
   DEBUGREF_INFO_VALUE            = 0x00000004,  
   DEBUGREF_INFO_ATTRIB           = 0x00000008,  
   DEBUGREF_INFO_REFTYPE          = 0x00000010,  
   DEBUGREF_INFO_REF              = 0x00000020,  
   DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,  
   DEBUGREF_INFO_NONE             = 0x00000000,  
   DEBUGREF_INFO_ALL              = 0xffffffff  
};  
typedef DWORD DEBUGREF_INFO_FLAGS;  
```  
  
```csharp  
public enum enum_DEBUGREF_INFO_FLAGS {   
   DEBUGREF_INFO_NAME             = 0x00000001,  
   DEBUGREF_INFO_TYPE             = 0x00000002,  
   DEBUGREF_INFO_VALUE            = 0x00000004,  
   DEBUGREF_INFO_ATTRIB           = 0x00000008,  
   DEBUGREF_INFO_REFTYPE          = 0x00000010,  
   DEBUGREF_INFO_REF              = 0x00000020,  
   DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,  
   DEBUGREF_INFO_NONE             = 0x00000000,  
   DEBUGREF_INFO_ALL              = 0xffffffff  
};  
```  
  
## <a name="members"></a>Membri  
 DEBUGREF_INFO_NAME  
 Inizializzazione/Usa il `bstrName` campo nella struttura.  
  
 DEBUGREF_INFO_TYPE  
 Inizializzazione/Usa il `bstrType` campo nella struttura.  
  
 DEBUGREF_INFO_VALUE  
 Inizializzazione/Usa il `bstrValue` campo nella struttura.  
  
 DEBUGREF_INFO_ATTRIB  
 Inizializzazione/Usa il `dwAttrib` campo nella struttura.  
  
 DEBUGREF_INFO_REFTYPE  
 Inizializzazione/Usa il `dwRefType` campo nella struttura.  
  
 DEBUGREF_INFO_REF  
 Inizializzazione/Usa il `pReference` campo nella struttura.  
  
 DEBUGREF_INFO_VALUE_AUTOEXPAND  
 Il campo del valore deve contenere il valore di espansione automatica, se disponibile, per questo tipo di oggetto.  
  
 DEBUGREF_INFO_NONE  
 Indica che nessun flag impostato.  
  
 DEBUGREF_INFO_ALL  
 Indica una maschera dei flag.  
  
## <a name="remarks"></a>Note  
 Questi flag vengono passati al [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) e [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) metodi per indicare quali campi del [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) struttura devono essere inizializzati.  
  
 Utilizzato per il `dwFields` appartenente il `DEBUG_REFERENCE_INFO` struttura per indicare quali campi sono validi e utilizzate quando viene restituita la struttura.  
  
 Questi valori possono essere combinati con un bit per bit `OR`.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)   
 [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)