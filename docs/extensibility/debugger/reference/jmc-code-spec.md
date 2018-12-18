---
title: JMC_CODE_SPEC | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- JMC_CODE_SPEC
helpviewer_keywords:
- JMC_CODE_SPEC structure
ms.assetid: d89498f1-4234-46d9-b4e2-abbcbca5068a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d3abf59cb55bd64004750be7b24e00e42eb79d9e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="jmccodespec"></a>JMC_CODE_SPEC
Questa struttura viene utilizzata per impostare le informazioni di JustMyCode per un modulo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
typedef struct _JMC_CODE_SPEC {  
   BOOL fIsUserCode;  
   BSTR bstrModuleName;  
} JMC_CODE_SPEC;  
```  
  
```csharp  
public struct JMC_CODE_SPEC {  
   public int    fIsUserCode;  
   public string bstrModuleName;  
};  
```  
  
## <a name="members"></a>Membri  
 fIsUserCode  
 Diverso da zero (`TRUE`) se il modulo viene considerato codice utente; in caso contrario, zero (`FALSE`) se il modulo venga trattata come codice esterno e non deve essere sottoposto a debug.  
  
 bstrModuleName  
 Nome del modulo in questione.  
  
## <a name="remarks"></a>Note  
 Questa struttura viene passata come un elenco di tali strutture per la [SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md) metodo.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)