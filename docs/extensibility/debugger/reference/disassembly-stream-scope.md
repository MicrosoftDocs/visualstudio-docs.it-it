---
title: DISASSEMBLY_STREAM_SCOPE | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- DISASSEMBLY_STREAM_SCOPE
helpviewer_keywords:
- DISASSEMBLY_STREAM_SCOPE enumeration
ms.assetid: 43e2b364-cbbe-4755-a7e6-a03f3054c965
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a0c72d0f14da9840c0a77d5ae88cb0acb5b54cba
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="disassemblystreamscope"></a>DISASSEMBLY_STREAM_SCOPE
Specifica l'ambito del flusso di disassembly.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
enum enum_DISASSEMBLY_STREAM_SCOPE {   
   DSS_HUGE     = 0x10000000,  
   DSS_FUNCTION = 0x0001,  
   DSS_MODULE   = (DSS_HUGE) | 0x0002,  
   DSS_ALL      = (DSS_HUGE) | 0x0003  
};  
typedef DWORD DISASSEMBLY_STREAM_SCOPE;  
```  
  
```csharp  
public enum enum_DISASSEMBLY_STREAM_SCOPE {   
   DSS_HUGE     = 0x10000000,  
   DSS_FUNCTION = 0x0001,  
   DSS_MODULE   = (DSS_HUGE) | 0x0002,  
   DSS_ALL      = (DSS_HUGE) | 0x0003  
};  
```  
  
## <a name="members"></a>Membri  
 DSS_HUGE  
 Specifica che il contesto del codice di disassemblaggio genera più output di un client in genere è necessario recuperare in una singola chiamata.  
  
 DSS_FUNCTION  
 Specifica che la funzione contenuta dal contesto del codice deve essere disassemblata. Specifica che il flusso di disassembly rappresenta una funzione, quando viene restituito dal [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) metodo.  
  
 DSS_MODULE  
 Quando viene restituito dal `IDebugDisassemblyStream2::GetScope` metodo, specifica che il flusso di disassembly rappresenta un modulo.  
  
 DSS_ALL  
 Specifica il disassembly per l'intero spazio di indirizzi.  
  
## <a name="remarks"></a>Note  
 Passata come argomento per il [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) metodo e restituito dal [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) metodo.  
  
 Questi valori possono essere combinati con un bit per bit `OR`.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)