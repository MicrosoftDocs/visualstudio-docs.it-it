---
title: MODULE_INFO_FIELDS | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: MODULE_INFO_FIELDS
helpviewer_keywords: MODULE_INFO_FIELDS enumeration
ms.assetid: 8bed85f4-235f-4192-b58f-5fad7a4d7a78
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: d96175501d0e75ee1949847c69909c23a3b08582
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="moduleinfofields"></a>MODULE_INFO_FIELDS
Specifica i flag per le informazioni sul modulo di debug.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
enum enum_MODULE_INFO_FIELDS {   
   MIF_NONE              = 0x0000,  
   MIF_NAME              = 0x0001,  
   MIF_URL               = 0x0002,  
   MIF_VERSION           = 0x0004,  
   MIF_DEBUGMESSAGE      = 0x0008,  
   MIF_LOADADDRESS       = 0x0010,  
   MIF_PREFFEREDADDRESS  = 0x0020,  
   MIF_SIZE              = 0x0040,  
   MIF_LOADORDER         = 0x0080,  
   MIF_TIMESTAMP         = 0x0100,  
   MIF_URLSYMBOLLOCATION = 0x0200,  
   MIF_FLAGS             = 0x0400,  
   MIF_ALLFIELDS         = 0x07ff  
};  
typedef DWORD MODULE_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_MODULE_INFO_FIELDS {   
   MIF_NONE              = 0x0000,  
   MIF_NAME              = 0x0001,  
   MIF_URL               = 0x0002,  
   MIF_VERSION           = 0x0004,  
   MIF_DEBUGMESSAGE      = 0x0008,  
   MIF_LOADADDRESS       = 0x0010,  
   MIF_PREFFEREDADDRESS  = 0x0020,  
   MIF_SIZE              = 0x0040,  
   MIF_LOADORDER         = 0x0080,  
   MIF_TIMESTAMP         = 0x0100,  
   MIF_URLSYMBOLLOCATION = 0x0200,  
   MIF_FLAGS             = 0x0400,  
   MIF_ALLFIELDS         = 0x07ff  
};  
```  
  
## <a name="members"></a>Membri  
 MIF_NONE  
 Utilizzare o inizializzare nessuno dei campi nella struttura.  
  
 MIF_NAME  
 Inizializzazione/Usa il `m_bstrName` campo il [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) struttura.  
  
 MIF_URL  
 Inizializzazione/Usa il `m_bstrUrl` campo il `MODULE_INFO` struttura.  
  
 MIF_VERSION  
 Inizializzazione/Usa il `m_bstrVersion` campo il `MODULE_INFO` struttura.  
  
 MIF_DEBUGMESSAGE  
 Inizializzazione/Usa il `m_bstrDebugMessage` campo il `MODULE_INFO` struttura.  
  
 MIF_LOADADDRESS  
 Inizializzazione/Usa il `m_addrLoadAddress` campo il `MODULE_INFO` struttura.  
  
 MIF_PREFFEREDADDRESS  
 Inizializzazione/Usa il `m_addrPreferredLoadAddress` campo il `MODULE_INFO` struttura.  
  
 MIF_SIZE  
 Inizializzazione/Usa il `m_dwSize` campo il `MODULE_INFO` struttura.  
  
 MIF_LOADORDER  
 Inizializzazione/Usa il `m_dwLoadOrder` campo il `MODULE_INFO` struttura.  
  
 MIF_TIMESTAMP  
 Inizializzazione/Usa il `m_TimeStamp` campo il `MODULE_INFO` struttura.  
  
 MIF_URLSYMBOLLOCATION  
 Inizializzazione/Usa il `m_bstrUrlSymbolLocation` campo il `MODULE_INFO` struttura.  
  
 MIF_FLAGS  
 Inizializzazione/Usa il `m_dwModuleFlags` campo il `MODULE_INFO` struttura.  
  
 MIF_ALLFIELDS  
 Inizializzazione/Usa tutti i campi nel `MODULE_INFO` struttura.  
  
## <a name="remarks"></a>Note  
 Questi valori vengono passati come argomento per il [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) metodo per indicare quali campi del [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) struttura devono essere inizializzati.  
  
 Questi valori vengono utilizzati anche nel `MODULE_INFO` struttura per indicare quali campi vengono utilizzati e valido.  
  
 Questi flag possono essere combinati con un bit per bit `OR`.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)