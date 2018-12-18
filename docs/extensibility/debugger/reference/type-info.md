---
title: TYPE_INFO | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: TYPE_INFO
helpviewer_keywords: TYPE_INFO structure
ms.assetid: d725cb68-a565-49d1-a16f-ff0445c587a0
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0d6888d2680cffbde132885d730cd35f6e509c2e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="typeinfo"></a>TYPE_INFO
Questa struttura consente di specificare vari tipi di informazioni sul tipo di un campo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
struct _tagTYPE_INFO_UNION {  
   dwTYPE_KIND dwKind;  
   union {  
      METADATA_TYPE typeMeta;  
      PDB_TYPE      typePdb;  
      BUILT_TYPE    typeBuilt;  
      DWORD         unused;  
   } type;  
} TYPE_INFO;  
```  
  
```csharp  
public struct TYPE_INFO {  
   public uint   dwKind;  
   public IntPtr unionmember;  
};  
```  
  
#### <a name="parameters"></a>Parametri  
 dwKind  
 Un valore di [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) enumerazione che determina come interpretare l'unione.  
  
 type.typeMeta  
 [Solo C++] Contiene un [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) struttura se `dwKind` è `TYPE_KIND_METADATA`.  
  
 type.typePdb  
 [Solo C++] Contiene un [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) struttura se `dwKind` è `TYPE_KIND_PDB`.  
  
 type.typeBuilt  
 [Solo C++] Contiene un [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) struttura se `dwKind` è `TYPE_KIND_BUILT`.  
  
 Type.Unused  
 Riempimento inutilizzato.  
  
 tipo  
 Nome dell'unione.  
  
 UnionMember  
 [Solo in c#] Effettuare il marshalling per il tipo di struttura appropriata in base `dwKind`.  
  
## <a name="remarks"></a>Note  
 Questa struttura viene passata per il [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) (metodo) in cui viene compilato. Come interpretare il contenuto della struttura si basa sul `dwKind` campo.  
  
> [!NOTE]
>  [Solo C++] Se `dwKind` è uguale a `TYPE_KIND_BUILT`, è necessario rilasciare sottostante [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) caso di eliminazione dell'oggetto di `TYPE_INFO` struttura. Questa operazione viene effettuata chiamando `typeInfo.type.typeBuilt.pUnderlyingField->Release()`.  
  
 [Solo in c#] Nella tabella seguente viene illustrato come interpretare il `unionmember` membro per ogni tipo di elemento. Nell'esempio viene illustrato come questa operazione viene eseguita per un tipo di elemento.  
  
|`dwKind`|`unionmember`interpretato come|  
|--------------|----------------------------------|  
|`TYPE_KIND_METADATA`|[METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)|  
|`TYPE_KIND_PDB`|[PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)|  
|`TYPE_KIND_BUILT`|[BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)|  
  
## <a name="example"></a>Esempio  
 Questo esempio viene illustrato come interpretare il `unionmember` appartenente il `TYPE_INFO` struttura in c#. Questo esempio viene illustrato un solo tipo di interpretazione (`TYPE_KIND_METADATA`), ma gli altri vengono interpretati esattamente nello stesso modo.  
  
```csharp  
using System;  
using System.Runtime.Interop.Services;  
using Microsoft.VisualStudio.Debugger.Interop;  
  
namespace MyPackage  
{  
    public class MyClass  
    {  
        public void Interpret(TYPE_INFO ti)  
        {  
            if (ti.dwKind == (uint)enum_dwTypeKind.TYPE_KIND_METADATA)  
            {  
                 METADATA_TYPE dataType = (METADATA_TYPE)Marshal.PtrToStructure(ti.unionmember,  
                                               typeof(METADATA_TYPE));  
            }  
        }  
    }  
}  
```  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)   
 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)   
 [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)   
 [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)   
 [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)