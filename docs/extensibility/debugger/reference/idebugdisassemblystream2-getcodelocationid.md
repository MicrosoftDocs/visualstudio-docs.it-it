---
title: IDebugDisassemblyStream2::GetCodeLocationId | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDisassemblyStream2::GetCodeLocationId
helpviewer_keywords: IDebugDisassemblyStream2::GetCodeLocationId
ms.assetid: 567adfb8-2f54-499a-a027-e4ecb82277ef
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: b042a3a88ed1e64bf7093c0e1ce52da746186921
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugdisassemblystream2getcodelocationid"></a>IDebugDisassemblyStream2::GetCodeLocationId
Restituisce un identificatore del percorso di codice per un contesto di codice specifico.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetCodeLocationId(   
   IDebugCodeContext2* pCodeContext,  
   UINT64*             puCodeLocationId  
);  
```  
  
```csharp  
int GetCodeLocationId(   
   IDebugCodeContext2 pCodeContext,  
   out ulong          puCodeLocationId  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pCodeContext`  
 [in] Un [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) oggetto da convertire in un identificatore.  
  
 `puCodeLocationId`  
 [out] Restituisce l'identificatore percorso codice. Vedere la sezione Osservazioni.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore. Restituisce `E_CODE_CONTEXT_OUT_OF_SCOPE` se il contesto del codice è valido, ma all'esterno dell'ambito.  
  
## <a name="remarks"></a>Note  
 Identificatore della posizione di codice è specifico per il motore di debug (DE), che supporta il disassembly. Questo identificatore viene utilizzato internamente per la Germania per tenere traccia delle posizioni nel codice e viene in genere, un indirizzo o un offset di qualche tipo. L'unico requisito è che se il contesto del codice di un'unica posizione è minore di contesto del codice di un altro percorso, quindi l'identificatore della posizione di codice corrispondente del primo contesto codice inoltre deve essere minore di identificatore della posizione di codice di contesto del codice secondo.  
  
 Per recuperare il contesto del codice di un identificatore di percorso di codice, chiamare il [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md) metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)