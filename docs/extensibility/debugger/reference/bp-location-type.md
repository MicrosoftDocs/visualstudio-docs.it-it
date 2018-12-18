---
title: BP_LOCATION_TYPE | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BP_LOCATION_TYPE
helpviewer_keywords: BP_LOCATION_TYPE structure
ms.assetid: 0248430a-3b61-4809-87a9-e9b6bb7d1130
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 919cef75834c6606cf4980b3a0e861302f29b73a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="bplocationtype"></a>BP_LOCATION_TYPE
Specifica il tipo di posizione del punto di interruzione per una richiesta di punto di interruzione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
enum enum_BP_LOCATION_TYPE {   
   BPLT_NONE               = 0x00000000,  
   BPLT_FILE_LINE          = 0x00010000,  
   BPLT_FUNC_OFFSET        = 0x00020000,  
   BPLT_CONTEXT            = 0x00030000,  
   BPLT_STRING             = 0x00040000,  
   BPLT_ADDRESS            = 0x00050000,  
   BPLT_RESOLUTION         = 0x00060000,  
   BPLT_CODE_FILE_LINE     = BPT_CODE | BPLT_FILE_LINE,  
   BPLT_CODE_FUNC_OFFSET   = BPT_CODE | BPLT_FUNC_OFFSET,  
   BPLT_CODE_CONTEXT       = BPT_CODE | BPLT_CONTEXT,  
   BPLT_CODE_STRING        = BPT_CODE | BPLT_STRING,  
   BPLT_CODE_ADDRESS       = BPT_CODE | BPLT_ADDRESS ,  
   BPLT_DATA_STRING        = BPT_DATA | BPLT_STRING,  
   BPLT_TYPE_MASK          = 0x0000FFFF,  
   BPLT_LOCATION_TYPE_MASK = 0xFFFF0000  
};  
typedef DWORD BP_LOCATION_TYPE;  
```  
  
```csharp  
public enum enum_BP_LOCATION_TYPE {   
   BPLT_NONE               = 0x00000000,  
   BPLT_FILE_LINE          = 0x00010000,  
   BPLT_FUNC_OFFSET        = 0x00020000,  
   BPLT_CONTEXT            = 0x00030000,  
   BPLT_STRING             = 0x00040000,  
   BPLT_ADDRESS            = 0x00050000,  
   BPLT_RESOLUTION         = 0x00060000,  
   BPLT_CODE_FILE_LINE     = BPT_CODE | BPLT_FILE_LINE,  
   BPLT_CODE_FUNC_OFFSET   = BPT_CODE | BPLT_FUNC_OFFSET,  
   BPLT_CODE_CONTEXT       = BPT_CODE | BPLT_CONTEXT,  
   BPLT_CODE_STRING        = BPT_CODE | BPLT_STRING,  
   BPLT_CODE_ADDRESS       = BPT_CODE | BPLT_ADDRESS ,  
   BPLT_DATA_STRING        = BPT_DATA | BPLT_STRING,  
   BPLT_TYPE_MASK          = 0x0000FFFF,  
   BPLT_LOCATION_TYPE_MASK = 0xFFFF0000  
};  
```  
  
## <a name="members"></a>Membri  
 BPLT_NONE  
 Non specifica il percorso di alcun punto di interruzione.  
  
 BPLT_FILE_LINE  
 Specifica il tipo di posizione del punto di interruzione come un file di riga.  
  
 BPLT_FUNC_OFFSET  
 Specifica il tipo di posizione del punto di interruzione come un offset della funzione.  
  
 BPLT_CONTEXT  
 Specifica il tipo di posizione del punto di interruzione come un contesto.  
  
 BPLT_STRING  
 Specifica il tipo di posizione del punto di interruzione come stringa.  
  
 BPLT_ADDRESS  
 Specifica il tipo di posizione del punto di interruzione come un indirizzo.  
  
 BPLT_RESOLUTION  
 Specifica il tipo di posizione del punto di interruzione come una risoluzione.  
  
 BPLT_CODE_FILE_LINE  
 Specifica il tipo di posizione del punto di interruzione come una riga del codice sorgente.  
  
 BPLT_CODE_FUNC_OFFSET  
 Specifica il tipo di posizione del punto di interruzione come un offset di funzione di codice.  
  
 BPLT_CODE_CONTEXT  
 Specifica il tipo di posizione del punto di interruzione come un contesto di codice.  
  
 BPLT_CODE_STRING  
 Specifica il tipo di posizione del punto di interruzione come una stringa di codice.  
  
 BPLT_CODE_ADDRESS  
 Specifica il tipo di posizione del punto di interruzione come un indirizzo di codice.  
  
 BPLT_DATA_STRING  
 Specifica il tipo di posizione del punto di interruzione come una stringa di dati.  
  
 BPLT_TYPE_MASK  
 Specifica una maschera di bit, in modo che il tipo di punto di interruzione può estrarre il valore.  
  
 BPLT_LOCATION_TYPE_MASK  
 Specifica una maschera di bit, in modo che il tipo di posizione del punto di interruzione può estrarre il valore.  
  
## <a name="remarks"></a>Note  
 Passato come parametro per il [GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md) metodo.  
  
 Un tipo di posizione del punto di interruzione è costituito da un tipo di punto di interruzione e un tipo di posizione. Ciò significa che un tipo di posizione del punto di interruzione non è un tipo di punto di interruzione (ad esempio, `BPT_CODE`) o un tipo di posizione (ad esempio, `BPLT_FILE_LINE`). Costanti predefinite per tutti i tipi di posizione punto di interruzione attualmente supportati sono inclusi in questa enumerazione (`BPLT_CODE_FILE_LINE` tramite `BPLT_DATA_STRING`).  
  
 `BPT_CODE`e `BPT_DATA` sono membri del [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) enumerazione.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)   
 [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)