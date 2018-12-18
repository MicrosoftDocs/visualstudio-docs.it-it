---
title: IDebugDisassemblyStream2::Read | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDisassemblyStream2::Read
helpviewer_keywords:
- IDebugDisassemblyStream2::Read
ms.assetid: 7db5f6bb-73ee-45bc-b187-c1b6aa2dfdd5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d9143abac4ce10a2b7305889e1d1a5236c1e9b07
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugdisassemblystream2read"></a>IDebugDisassemblyStream2::Read
Legge le istruzioni a partire dalla posizione corrente nel flusso del disassembly.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT Read(   
   DWORD                     dwInstructions,  
   DISASSEMBLY_STREAM_FIELDS dwFields,  
   DWORD*                    pdwInstructionsRead,  
   DisassemblyData*          prgDisassembly  
);  
```  
  
```csharp  
int Read(   
   uint                           dwInstructions,  
   enum_DISASSEMBLY_STREAM_FIELDS dwFields,  
   out uint                       pdwInstructionsRead,  
   DisassemblyData[]              prgDisassembly  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwInstructions`  
 [in] Il numero di istruzioni da disassemblare. Questo valore corrisponde anche la lunghezza massima del `prgDisassembly` matrice.  
  
 `dwFields`  
 [in] Una combinazione di flag dal [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) enumerazione che indicano quali campi della `prgDisassembly` devono essere compilati.  
  
 `pdwInstructionsRead`  
 [out] Restituisce il numero di istruzioni effettivamente disassemblato.  
  
 `prgDisassembly`  
 [out] Matrice di [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) strutture che viene riempito con il codice disassemblato, una struttura per ogni istruzione disassemblato. La lunghezza di questa matrice è dettata dal `dwInstructions` parametro.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Il numero massimo di istruzioni disponibili nell'ambito corrente può essere ottenuto chiamando il [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md) metodo.  
  
 La posizione corrente in cui leggere la successiva istruzione può essere modificata chiamando il [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md) metodo.  
  
 Il `DSF_OPERANDS_SYMBOLS` flag possono essere aggiunti al `DSF_OPERANDS` flag nel `dwFields` parametro per indicare che i nomi dei simboli da utilizzare quando le istruzioni di disassemblaggio.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)   
 [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)   
 [Ricerca](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)