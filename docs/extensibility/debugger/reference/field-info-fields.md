---
title: FIELD_INFO_FIELDS | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- FIELD_INFO_FIELDS
helpviewer_keywords:
- FIELD_INFO_FIELDS enumeration
ms.assetid: a69487d2-e701-4165-804a-8a011df9a3bd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d74f39ce8e9e350c791371f20b7401d685fb1d18
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="fieldinfofields"></a>FIELD_INFO_FIELDS
Specifica le informazioni da recuperare su un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
enum enum_FIELD_INFO_FIELDS {   
   FIF_FULLNAME  = 0x0001,  
   FIF_NAME      = 0x0002,  
   FIF_TYPE      = 0x0004,  
   FIF_MODIFIERS = 0x0008,  
   FIF_ALL       = 0xffffffff,  
   FIF_NONE      = 0x0000  
};  
typedef DWORD FIELD_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_FIELD_INFO_FIELDS {  
   FIF_FULLNAME  = 0x0001,  
   FIF_NAME      = 0x0002,  
   FIF_TYPE      = 0x0004,  
   FIF_MODIFIERS = 0x0008,  
   FIF_ALL       = 0xffffffff,  
   FIF_NONE      = 0x0000  
};  
```  
  
## <a name="members"></a>Membri  
 FIF_FULLNAME  
 Inizializzazione/Usa il `bstrFullName` campo il [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) struttura.  
  
 FIF_NAME  
 Inizializzazione/Usa il `bstrName` campo il `FIELD_INFO` struttura.  
  
 FIF_TYPE  
 Inizializzazione/Usa il `bstrType` campo il `FIELD_INFO` struttura.  
  
 FIF_MODIFIERS  
 Inizializzazione/Usa il `bstrModifiers` campo il `FIELD_INFO` struttura.  
  
## <a name="remarks"></a>Note  
 Questi valori vengono anche passati come argomento per il [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) per specificare quali campi del [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) struttura devono essere inizializzati.  
  
 Questi valori vengono utilizzati anche nel `dwFields` appartenente il `FIELD_INFO` struttura per indicare quali campi vengono utilizzati e valido.  
  
 Questi flag possono essere combinati con un bit per bit `OR`.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)