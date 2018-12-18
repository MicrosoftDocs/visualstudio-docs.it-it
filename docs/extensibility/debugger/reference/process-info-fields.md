---
title: PROCESS_INFO_FIELDS | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- PROCESS_INFO_FIELDS
helpviewer_keywords:
- PROCESS_INFO_FIELDS enumeration
ms.assetid: 0d9cc345-3d3a-44d8-ae15-a67acb97a828
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3376db379e4e911bcaa8e865a16c63d1251229f6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="processinfofields"></a>PROCESS_INFO_FIELDS
Specificare il tipo di informazioni da recuperare per un processo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
enum enum_PROCESS_INFO_FIELDS {   
   PIF_FILE_NAME             = 0x00000001,  
   PIF_BASE_NAME             = 0x00000002,  
   PIF_TITLE                 = 0x00000004,  
   PIF_PROCESS_ID            = 0x00000008,  
   PIF_SESSION_ID            = 0x00000010,  
   PIF_ATTACHED_SESSION_NAME = 0x00000020,  
   PIF_CREATION_TIME         = 0x00000040,  
   PIF_FLAGS                 = 0x00000080,  
   PIF_ALL                   = 0x000000ff  
};  
typedef DWORD PROCESS_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_PROCESS_INFO_FIELDS {   
   PIF_FILE_NAME             = 0x00000001,  
   PIF_BASE_NAME             = 0x00000002,  
   PIF_TITLE                 = 0x00000004,  
   PIF_PROCESS_ID            = 0x00000008,  
   PIF_SESSION_ID            = 0x00000010,  
   PIF_ATTACHED_SESSION_NAME = 0x00000020,  
   PIF_CREATION_TIME         = 0x00000040,  
   PIF_FLAGS                 = 0x00000080,  
   PIF_ALL                   = 0x000000ff  
};  
```  
  
## <a name="members"></a>Membri  
 PIF_FILE_NAME  
 Inizializzazione/Usa il `bstrFileName` campo il [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) struttura.  
  
 PIF_BASE_NAME  
 Inizializzazione/Usa il `bstrBaseName` campo il `PROCESS_INFO` struttura.  
  
 PIF_TITLE  
 Inizializzazione/Usa il `bstrTitle` campo il `PROCESS_INFO` struttura.  
  
 PIF_PROCESS_ID  
 Inizializzazione/Usa il `ProcessId` campo il `PROCESS_INFO` struttura.  
  
 PIF_SESSION_ID  
 Inizializzazione/Usa il `dwSessionId` campo il `PROCESS_INFO` struttura.  
  
 PIF_ATTACHED_SESSION_NAME  
 Inizializzazione/Usa il `bstrAttachedSessionName` campo il `PROCESS_INFO` struttura.  
  
 PIF_CREATION_TIME  
 Inizializzazione/Usa il `CreationTime` campo il `PROCESS_INFO` struttura.  
  
 PIF_FLAGS  
 Inizializzazione/Usa il `Flags` campo il `PROCESS_INFO` struttura.  
  
 PIF_ALL  
 Compila tutti i campi.  
  
## <a name="remarks"></a>Note  
 Passare il [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) metodo per indicare quali campi del [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) struttura devono essere inizializzati.  
  
 Usato anche in `Fields` campo il `PROCESS_INFO` struttura per indicare quali campi vengono utilizzati e valido.  
  
 Questi flag possono essere combinati con un bit per bit `OR`.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)