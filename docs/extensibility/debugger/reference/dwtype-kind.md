---
title: dwTYPE_KIND | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- dwTYPE_KIND
helpviewer_keywords:
- dwTYPE_KIND enumeration
ms.assetid: 6ff56b0f-c502-4e6c-9829-bfa05361b783
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5eaa1b9edc128b5e13641bb5b38296fd96740ab4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="dwtypekind"></a>dwTYPE_KIND
Specifica come interpretare il tipo di un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
enum enum_dwTYPE_KIND {  
   TYPE_KIND_METADATA = 0x0001,  
   TYPE_KIND_PDB      = 0x0002,  
   TYPE_KIND_BUILT    = 0x0003,  
};  
  
typedef DWORD dwTYPE_KIND;  
```  
  
```csharp  
public enum enum_dwTYPE_KIND {  
   TYPE_KIND_METADATA = 0x0001,  
   TYPE_KIND_PDB      = 0x0002,  
   TYPE_KIND_BUILT    = 0x0003,  
};  
```  
  
#### <a name="parameters"></a>Parametri  
 TYPE_KIND_METADATA  
 Il [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) unione deve essere interpretata come un [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) struttura.  
  
 TYPE_KIND_PDB  
 Il `TYPE_INFO` unione deve essere interpretata come un [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) struttura.  
  
 TYPE_KIND_BUILT  
 Il `TYPE_INFO` unione deve essere interpretata come un [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) struttura.  
  
## <a name="remarks"></a>Note  
 I valori di questa enumerazione sono il `dwKind` campo il [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) struttura e vengono utilizzati per determinare come interpretare il `type` membro dell'unione. Il `TYPE_INFO` struttura viene restituita da una chiamata al [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) metodo.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)   
 [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)   
 [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)   
 [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)