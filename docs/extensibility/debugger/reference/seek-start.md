---
title: SEEK_START | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SEEK_START
helpviewer_keywords:
- SEEK_START enumeration
ms.assetid: 55bd8901-626e-428b-a263-23b14417f4c6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 55be60c35ea3af97cb9129670ef422d1a649fead
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="seekstart"></a>SEEK_START
Specifica la posizione da cui iniziare la ricerca in un flusso del disassembly.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
enum enum_SEEK_START {   
   SEEK_START_BEGIN       = 0x0001,  
   SEEK_START_END         = 0x0002,  
   SEEK_START_CURRENT     = 0x0003,  
   SEEK_START_CODECONTEXT = 0x0004,  
   SEEK_START_CODELOCID   = 0x0005  
};  
typedef DWORD SEEK_START;  
```  
  
```csharp  
public enum enum_SEEK_START {   
   SEEK_START_BEGIN       = 0x0001,  
   SEEK_START_END         = 0x0002,  
   SEEK_START_CURRENT     = 0x0003,  
   SEEK_START_CODECONTEXT = 0x0004,  
   SEEK_START_CODELOCID   = 0x0005  
};  
```  
  
## <a name="members"></a>Membri  
 SEEK_START_BEGIN  
 Inizia la ricerca all'inizio del documento corrente.  
  
 SEEK_START_END  
 Inizia la ricerca alla fine del documento corrente.  
  
 SEEK_START_CURRENT  
 Inizia la ricerca in corrispondenza della posizione corrente del documento corrente.  
  
 SEEK_START_CODECONTEXT  
 Inizia la ricerca nel contesto del codice specificata del documento corrente.  
  
 SEEK_START_CODELOCID  
 Inizia la ricerca nell'identificatore percorso codice specificata. Identificatori di percorso di codice vengono ottenuti chiamando [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md).  
  
## <a name="remarks"></a>Note  
 Passata come argomento per il [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md) metodo.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Ricerca](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)   
 [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)