---
title: IDebugDisassemblyStream2::Seek | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDisassemblyStream2::Seek
helpviewer_keywords: IDebugDisassemblyStream2::Seek
ms.assetid: afec3008-b1e0-4803-ad24-195dbfb6497e
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2725eb876cf66665c27027dd4d9b250ed7e866e7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugdisassemblystream2seek"></a>IDebugDisassemblyStream2::Seek
Sposta il puntatore di lettura nel flusso di disassembly un determinato numero di istruzioni rispetto alla posizione specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT Seek(   
   SEEK_START          dwSeekStart,  
   IDebugCodeContext2* pCodeContext,  
   UINT64              uCodeLocationId,  
   INT64               iInstructions  
);  
```  
  
```csharp  
int Seek(   
   enum_SEEK_START    dwSeekStart,  
   IDebugCodeContext2 pCodeContext,  
   ulong              uCodeLocationId,  
   long               iInstructions  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwSeekStart`  
 [in] Un valore di [SEEK_START](../../../extensibility/debugger/reference/seek-start.md) enumerazione che specifica la posizione relativa per iniziare il processo di ricerca.  
  
 `pCodeContext`  
 [in] Il [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) oggetto che rappresenta il contesto del codice che l'operazione di ricerca è relativo. Questo parametro viene utilizzato solo se `dwSeekStart`  =  `SEEK_START_CODECONTEXT`; in caso contrario, questo parametro viene ignorato e può essere un valore null.  
  
 `uCodeLocationId`  
 [in] Identificatore della posizione di codice che l'operazione di ricerca è relativo. Questo parametro viene utilizzato se `dwSeekStart`  =  `SEEK_START_CODELOCID`; in caso contrario, questo parametro viene ignorato e può essere impostato su 0. Vedere la sezione Osservazioni per il [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) metodo per una descrizione di un identificatore del percorso di codice.  
  
 `iInstructions`  
 [in] Il numero di istruzioni per spostare rispetto alla posizione specificata `dwSeekStart`. Questo valore può essere negativo per spostarsi all'indietro.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`. Restituisce `S_FALSE` se la posizione di ricerca di un punto successivo nell'elenco di istruzioni disponibili. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="remarks"></a>Note  
 Se la ricerca in una posizione prima dell'inizio dell'elenco, la posizione di lettura è la prima istruzione nell'elenco. Se il componente, vedere è in una posizione dopo la fine dell'elenco, la posizione di lettura viene impostata all'ultima istruzione nell'elenco.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [SEEK_START](../../../extensibility/debugger/reference/seek-start.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)