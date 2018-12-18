---
title: MODULE_INFO_FLAGS | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- MODULE_INFO_FLAGS
helpviewer_keywords:
- MODULE_INFO_FLAGS enumeration
ms.assetid: e22d3723-b4d4-4524-8a2f-3adb55bbd273
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ee2676b85889226e2fbb9665462d83aa4b0d6520
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="moduleinfoflags"></a>MODULE_INFO_FLAGS
Specifica lo stato dei simboli per un modulo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
enum enum_MODULE_INFO_FLAGS {  
   MIF_SYMBOLS_LOADED = 0x0001  
};  
typedef DWORD MODULE_INFO_FLAGS;  
```  
  
```csharp  
public enum enum_MODULE_INFO_FLAGS {  
   MIF_SYMBOLS_LOADED = 0x0001  
};  
```  
  
## <a name="members"></a>Membri  
 MIF_SYMBOLS_LOADED  
 Almeno un set di simboli è stato caricato il modulo (in caso contrario non vi sono simboli caricati).  
  
## <a name="remarks"></a>Note  
 Questo valore viene restituito dal [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md) metodo.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)