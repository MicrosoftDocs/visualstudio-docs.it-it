---
title: DISASSEMBLY_STREAM_FIELDS | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- DISASSEMBLY_STREAM_FIELDS
helpviewer_keywords:
- DISASSEMBLY_STREAM_FIELDS enumeration
ms.assetid: cfc9b4de-c756-4844-bea7-d9f186a51d1b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1a8735992574699ba2b108fc493e9003ca52c9b2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="disassemblystreamfields"></a>DISASSEMBLY_STREAM_FIELDS
Specifica le informazioni da recuperare relativi a un campo di disassembly.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
enum enum_DISASSEMBLY_STREAM_FIELDS {   
   DSF_ADDRESS          = 0x00000001,  
   DSF_ADDRESSOFFSET    = 0x00000002,  
   DSF_CODEBYTES        = 0x00000004,  
   DSF_OPCODE           = 0x00000008,  
   DSF_OPERANDS         = 0x00000010,  
   DSF_SYMBOL           = 0x00000020,  
   DSF_CODELOCATIONID   = 0x00000040,  
   DSF_POSITION         = 0x00000080,  
   DSF_DOCUMENTURL      = 0x00000100,  
   DSF_BYTEOFFSET       = 0x00000200,  
   DSF_FLAGS            = 0x00000400,  
   DSF_OPERANDS_SYMBOLS = 0x00010000,  
   DSF_ALL              = 0x000107ff  
};  
typedef DWORD DISASSEMBLY_STREAM_FIELDS;  
```  
  
```csharp  
public enum enum_DISASSEMBLY_STREAM_FIELDS {   
   DSF_ADDRESS          = 0x00000001,  
   DSF_ADDRESSOFFSET    = 0x00000002,  
   DSF_CODEBYTES        = 0x00000004,  
   DSF_OPCODE           = 0x00000008,  
   DSF_OPERANDS         = 0x00000010,  
   DSF_SYMBOL           = 0x00000020,  
   DSF_CODELOCATIONID   = 0x00000040,  
   DSF_POSITION         = 0x00000080,  
   DSF_DOCUMENTURL      = 0x00000100,  
   DSF_BYTEOFFSET       = 0x00000200,  
   DSF_FLAGS            = 0x00000400,  
   DSF_OPERANDS_SYMBOLS = 0x00010000,  
   DSF_ALL              = 0x000107ff  
};  
```  
  
## <a name="members"></a>Membri  
 DSF_ADDRESS  
 Inizializzazione/Usa il `bstrAddress` campo.  
  
 DSF_ADDRESSOFFSET  
 Inizializzazione/Usa il `bstrAddressOffset` campo.  
  
 DSF_CODEBYTES  
 Inizializzazione/Usa il `bstrCodeBytes` campo.  
  
 DSF_OPCODE  
 Inizializzazione/Usa il `bstrOpCode` campo.  
  
 DSF_OPERANDS  
 Inizializzazione/Usa il `bstrOperands` campo.  
  
 DSF_SYMBOL  
 Inizializzazione/Usa il `bstrSymbol` campo.  
  
 DSF_CODELOCATIONID  
 Inizializzazione/Usa il `uCodeLocationId` campo.  
  
 DSF_POSITION  
 Inizializzazione/Usa il `posBeg` e `posEnd` campi.  
  
 DSF_DOCUMENTURL  
 Inizializzazione/Usa il `bstrDocumentUrl` campo.  
  
 DSF_BYTEOFFSET  
 Inizializzazione/Usa il `dwByteOffset` campo.  
  
 DSF_FLAGS  
 Inizializzazione/Usa il `dwFlags` ([DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)) campo.  
  
 DSF_OPERANDS_SYMBOLS  
 Includere i nomi dei simboli nel `bstrOperands` campo.  
  
 DSF_ALL  
 Specifica tutti i campi per il flusso del disassembly.  
  
## <a name="remarks"></a>Note  
 Passato come parametro per il [lettura](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) metodo per indicare quali campi del [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) struttura devono essere inizializzati.  
  
 Utilizzato per il `dwFields` appartenente il `DisassemblyData` struttura per indicare quali campi sono validi e utilizzate quando viene restituita la struttura.  
  
 Questi valori possono essere combinati con un bit per bit `OR`.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)   
 [Lettura](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)   
 [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)