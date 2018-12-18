---
title: DOCCONTEXT_COMPARE | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- DOCCONTEXT_COMPARE
helpviewer_keywords:
- DOCCONTEXT_COMPARE enumeration
ms.assetid: ed947c34-b07e-4b69-8381-b6e7cb842862
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 966d31889d7979732af20f5e3f95546e87af6598
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="doccontextcompare"></a>DOCCONTEXT_COMPARE
Specifica i criteri per il confronto tra due contesti di documento.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
enum enum_DOCCONTEXT_COMPARE {   
   DOCCONTEXT_EQUAL         = 0x0001,  
   DOCCONTEXT_LESS_THAN     = 0x0002,  
   DOCCONTEXT_GREATER_THAN  = 0x0003,  
   DOCCONTEXT_SAME_DOCUMENT = 0x0004  
};  
typedef DWORD DOCCONTEXT_COMPARE;  
```  
  
```csharp  
enum enum_DOCCONTEXT_COMPARE {   
   DOCCONTEXT_EQUAL         = 0x0001,  
   DOCCONTEXT_LESS_THAN     = 0x0002,  
   DOCCONTEXT_GREATER_THAN  = 0x0003,  
   DOCCONTEXT_SAME_DOCUMENT = 0x0004  
};  
```  
  
## <a name="members"></a>Membri  
 DOCCONTEXT_EQUAL  
 Trovare il contesto del documento prima nell'elenco che corrisponde al contesto di documento di destinazione.  
  
 DOCCONTEXT_LESS_THAN  
 Trovare il contesto del documento prima nell'elenco che è minore rispetto al contesto di documento di destinazione.  
  
 DOCCONTEXT_GREATER_THAN  
 Trovare il contesto del documento prima nell'elenco che è maggiore rispetto al contesto di documento di destinazione.  
  
 DOCCONTEXT_SAME_DOCUMENT  
 Trovare il contesto del documento prima nell'elenco presente nel contesto di documento di destinazione nello stesso documento.  
  
## <a name="remarks"></a>Note  
 Passata come argomento per il [confrontare](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md) metodo.  
  
 Questi valori vengono utilizzati per specificare un criterio di confronto per trovare il primo contesto di documento in un elenco. Un contesto di documento viene fornito un elenco di contesti di documento da confrontare solo in tramite il `IDebugDocumentContext2::Compare` metodo. Il contesto del documento prima nell'elenco per il quale l'operatore di confronto è `true` viene quindi restituito.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Compare](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)