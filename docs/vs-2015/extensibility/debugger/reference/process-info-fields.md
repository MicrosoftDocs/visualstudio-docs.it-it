---
title: PROCESS_INFO_FIELDS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FIELDS
helpviewer_keywords:
- PROCESS_INFO_FIELDS enumeration
ms.assetid: 0d9cc345-3d3a-44d8-ae15-a67acb97a828
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7700670774dcb38b054cf28275f64c0c3046f741
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205032"
---
# <a name="process_info_fields"></a>PROCESS_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Specifica il tipo di informazioni da recuperare per un processo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
enum enum_PROCESS_INFO_FIELDS {   
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
public enum enum_PROCESS_INFO_FIELDS {   
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
 Inizializza/usa il `bstrFileName` campo della struttura [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) .  
  
 PIF_BASE_NAME  
 Inizializza/usa il `bstrBaseName` campo della `PROCESS_INFO` struttura.  
  
 PIF_TITLE  
 Inizializza/usa il `bstrTitle` campo della `PROCESS_INFO` struttura.  
  
 PIF_PROCESS_ID  
 Inizializza/usa il `ProcessId` campo della `PROCESS_INFO` struttura.  
  
 PIF_SESSION_ID  
 Inizializza/usa il `dwSessionId` campo della `PROCESS_INFO` struttura.  
  
 PIF_ATTACHED_SESSION_NAME  
 Inizializza/usa il `bstrAttachedSessionName` campo della `PROCESS_INFO` struttura.  
  
 PIF_CREATION_TIME  
 Inizializza/usa il `CreationTime` campo della `PROCESS_INFO` struttura.  
  
 PIF_FLAGS  
 Inizializza/usa il `Flags` campo della `PROCESS_INFO` struttura.  
  
 PIF_ALL  
 Compila tutti i campi.  
  
## <a name="remarks"></a>Osservazioni  
 Passato al metodo [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) per indicare quali campi della struttura [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) devono essere inizializzati.  
  
 Usato anche nel `Fields` campo della `PROCESS_INFO` struttura per indicare quali campi vengono usati e validi.  
  
 Questi flag possono essere combinati con un bit per bit `OR` .  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg. h  
  
 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
