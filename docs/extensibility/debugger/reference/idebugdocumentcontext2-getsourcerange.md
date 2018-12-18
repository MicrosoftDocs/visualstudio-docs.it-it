---
title: IDebugDocumentContext2::GetSourceRange | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDocumentContext2::GetSourceRange
helpviewer_keywords:
- IDebugDocumentContext2::GetSourceRange
ms.assetid: 5903c75e-5390-4d13-9314-1ee276255313
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f003ba3f97f053c4617408bfc9334da057bb98ef
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugdocumentcontext2getsourcerange"></a>IDebugDocumentContext2::GetSourceRange
Ottiene l'intervallo di codice sorgente di questo contesto di documento.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetSourceRange(   
   TEXT_POSITION* pBegPosition,  
   TEXT_POSITION* pEndPosition  
);  
```  
  
```csharp  
int GetSourceRange(   
   TEXT_POSITION[] pBegPosition,  
   TEXT_POSITION[] pEndPosition  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pBegPosition`  
 [in, out] Oggetto [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) struttura che viene compilato con la posizione iniziale. Impostare questo argomento per un valore null se tali informazioni non sono necessarie.  
  
 `pEndPosition`  
 [in, out] Oggetto [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) struttura che viene compilato con la posizione finale. Impostare questo argomento per un valore null se tali informazioni non sono necessarie.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Un intervallo di origine è l'intero intervallo del codice sorgente, dall'oggetto corrente istruzione subito dopo l'istruzione precedente che hanno contribuito codice. L'intervallo di origine viene in genere utilizzato per la combinazione di istruzioni di origine, comprensivo di commenti, con il codice nella finestra disassembly.  
  
 Per ottenere l'intervallo per solo le istruzioni di codice contenute in questo contesto di documento, chiamare il [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)