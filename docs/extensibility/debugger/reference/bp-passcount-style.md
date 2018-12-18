---
title: BP_PASSCOUNT_STYLE | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- BP_PASSCOUNT_STYLE
helpviewer_keywords:
- BP_PASSCOUNT_STYLE structure
ms.assetid: 0a647047-e2d5-4724-a0b8-68108425ecad
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2b238012a844016324bbdee4df3cc167051815f3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="bppasscountstyle"></a>BP_PASSCOUNT_STYLE
Specifica la condizione associata con il punto di interruzione passaggio che fa sì che il punto di interruzione da attivare.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
enum enum_BP_PASSCOUNT_STYLE {   
   BP_PASSCOUNT_NONE             = 0x0000,  
   BP_PASSCOUNT_EQUAL            = 0x0001,  
   BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,  
   BP_PASSCOUNT_MOD              = 0x0003  
};  
typedef DWORD BP_PASSCOUNT_STYLE;  
```  
  
```csharp  
public enum enum_BP_PASSCOUNT_STYLE {   
   BP_PASSCOUNT_NONE             = 0x0000,  
   BP_PASSCOUNT_EQUAL            = 0x0001,  
   BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,  
   BP_PASSCOUNT_MOD              = 0x0003  
};  
```  
  
## <a name="members"></a>Membri  
 BP_PASSCOUNT_NONE  
 Specifica nessuno stile di conteggio di passaggio di punto di interruzione.  
  
 BP_PASSCOUNT_EQUAL  
 Imposta lo stile di conteggio di passaggio di punto di interruzione deve essere uguale a. Il punto di interruzione viene generato quando il numero di volte in cui che viene raggiunto il punto di interruzione è uguale al conteggio di passaggio.  
  
 BP_PASSCOUNT_EQUAL_OR_GREATER  
 Imposta lo stile di conteggio di passaggio di punto di interruzione su uguale o maggiore. Il punto di interruzione viene generato quando il numero di volte in cui che viene raggiunto il punto di interruzione è uguale o maggiore del numero di passaggio.  
  
 BP_PASSCOUNT_MOD  
 Specifica un modulo di conteggio esecuzioni di test. Ad esempio, se il conteggio della sessione è di tipo `BP_PASSCOUNT_MOD` e passare il valore del conteggio è 4, il punto di interruzione di generato ogni volta che il numero di passaggi è un multiplo di 4.  
  
## <a name="remarks"></a>Note  
 Utilizzato per il `stylePassCount` appartenente il [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) struttura che a sua volta è un membro del [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) e [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) strutture.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)