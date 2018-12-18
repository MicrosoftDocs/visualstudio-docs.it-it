---
title: MACHINE_INFO_FIELDS | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- MACHINE_INFO_FIELDS
helpviewer_keywords:
- MACHINE_INFO_FIELDS enumeration
ms.assetid: 2d61d206-7d40-4df1-8c88-1b3c9c78821e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5d0ff6f75c0ee17bef57b1f2632c4d6926948528
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="machineinfofields"></a>MACHINE_INFO_FIELDS
Specifica il tipo di informazioni da recuperare per un determinato computer.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
enum enum_MACHINE_INFO_FIELDS {   
   MCIF_NAME  = 0x00000001,  
   MCIF_FLAGS = 0x00000002,  
   MCIF_ALL   = 0x00000003  
};  
typedef DWORD MACHINE_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_MACHINE_INFO_FIELDS {   
   MCIF_NAME  = 0x00000001,  
   MCIF_FLAGS = 0x00000002,  
   MCIF_ALL   = 0x00000003  
};  
```  
  
## <a name="members"></a>Membri  
 MCIF_NAME  
 Inizializzazione/Usa il `bstrName` campo nella struttura.  
  
 MCIF_FLAGS  
 Inizializzazione/Usa il `Flags` campo nella struttura.  
  
 MIF_ALL  
 Utilizzare o inizializzare tutti i campi della struttura.  
  
## <a name="remarks"></a>Note  
 Questi valori vengono passati per la [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md) metodo per indicare i membri del [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) struttura devono essere inizializzati.  
  
 Usato anche nel `Fields` appartenente il `MACHINE_INFO` struttura per indicare quali campi vengono utilizzati e valido.  
  
 Questi flag possono essere combinati con un bit per bit `OR`.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md)   
 [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)