---
title: CONTEXT_COMPARE | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CONTEXT_COMPARE
helpviewer_keywords: CONTEXT_COMPARE enumeration
ms.assetid: 701ed61c-a320-4c20-a335-0b840024abc0
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: beba9f612024a63f8f302411982442df19e0bbd4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="contextcompare"></a>CONTEXT_COMPARE
Specifica i criteri per il confronto tra due contesti di memoria.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
enum enum_CONTEXT_COMPARE {   
   CONTEXT_EQUAL                 = 0x0001,  
   CONTEXT_LESS_THAN             = 0x0002,  
   CONTEXT_GREATER_THAN          = 0x0003,  
   CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,  
   CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,  
   CONTEXT_SAME_SCOPE            = 0x0006,  
   CONTEXT_SAME_FUNCTION         = 0x0007,  
   CONTEXT_SAME_MODULE           = 0x0008,  
   CONTEXT_SAME_PROCESS          = 0x0009  
};  
typedef DWORD CONTEXT_COMPARE;  
```  
  
```csharp  
public enum enum_CONTEXT_COMPARE {   
   CONTEXT_EQUAL                 = 0x0001,  
   CONTEXT_LESS_THAN             = 0x0002,  
   CONTEXT_GREATER_THAN          = 0x0003,  
   CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,  
   CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,  
   CONTEXT_SAME_SCOPE            = 0x0006,  
   CONTEXT_SAME_FUNCTION         = 0x0007,  
   CONTEXT_SAME_MODULE           = 0x0008,  
   CONTEXT_SAME_PROCESS          = 0x0009  
};  
```  
  
## <a name="members"></a>Membri  
 CONTEXT_EQUAL  
 Trovare il primo contesto di memoria dell'elenco che corrisponde al contesto di memoria di destinazione.  
  
 CONTEXT_LESS_THAN  
 Trovare il primo contesto di memoria dell'elenco che è minore rispetto al contesto di memoria di destinazione.  
  
 CONTEXT_GREATER_THAN  
 Trovare il primo contesto di memoria dell'elenco che è maggiore rispetto al contesto di memoria di destinazione.  
  
 CONTEXT_LESS_THAN_OR_EQUAL  
 Trovare il primo contesto di memoria dell'elenco che è minore o uguale al contesto di memoria di destinazione.  
  
 CONTEXT_GREATER_THAN_OR_EQUAL  
 Trovare il primo contesto di memoria dell'elenco che è maggiore o uguale al contesto di memoria di destinazione.  
  
 CONTEXT_SAME_SCOPE  
 Individuare il primo contesto di memoria nell'elenco presente nello stesso ambito come contesto di memoria di destinazione.  
  
 CONTEXT_SAME_FUNCTION  
 Trovare il primo contesto di memoria dell'elenco che è la stessa funzione dell'ambito della memoria di destinazione.  
  
 CONTEXT_SAME_MODULE  
 Individuare il primo contesto di memoria nell'elenco presente nello stesso modulo come contesto di memoria di destinazione.  
  
 CONTEXT_SAME_PROCESS  
 Trovare il primo contesto di memoria dell'elenco che è dello stesso processo come contesto di memoria di destinazione.  
  
## <a name="remarks"></a>Note  
 Passata come argomento per il [confrontare](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md) metodo.  
  
 Questi valori vengono utilizzati per individuare il primo contesto di memoria in un elenco che soddisfa i criteri di confronto specificate. Un contesto di memoria viene fornito un elenco di contesti di memoria per confrontare solo in tramite il `IDebugMemoryContext2::Compare` metodo. Il primo contesto di memoria nell'elenco per il quale l'operatore di confronto è `true` viene quindi restituito.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Compare](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)