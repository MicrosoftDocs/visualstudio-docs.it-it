---
title: IDebugDocumentPositionOffset2::GetRange | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugDocumentPositionOffset2::GetRange
ms.assetid: 27da7130-0932-4f97-abde-05e6fb018606
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 60d7ee73be7ccd421c7f5e0b4861e9cd935fbdb0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugdocumentpositionoffset2getrange"></a>IDebugDocumentPositionOffset2::GetRange
Recupera l'intervallo per la posizione del documento corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetRange(  
   DWORD* pdwBegOffset,  
   DWORD* pdwEndOffset  
);  
```  
  
```csharp  
public int GetRange(  
   ref uint pdwBegOffset,  
   ref uint pdwEndOffset  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pdwBegOffset`  
 [in, out] Offset per la posizione iniziale dell'intervallo. Impostare questo parametro su un valore null se tali informazioni non sono necessarie.  
  
 `pdwEndOffset`  
 [in, out] Offset per la posizione finale dell'intervallo. Impostare questo parametro su un valore null se tali informazioni non sono necessarie.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 L'intervallo specificato in una posizione di documento per un punto di interruzione del percorso viene utilizzato dal motore di debug (DE) per la ricerca con un'istruzione che effettivamente fornisce codice. Si consideri il codice di esempio seguente:  
  
```  
Line 5: // comment  
Line 6: x = 1;  
```  
  
 Riga 5 non contribuisce a nessun codice di programma sottoposto a debug. Se il debugger che imposta il punto di interruzione nella riga 5 desidera DE per eseguire la ricerca di una determinata quantità per la prima riga di codice, il debugger specificare un intervallo che include righe candidato aggiuntivo in un punto di interruzione potrebbe essere posizionato in modo corretto. La Germania viene quindi eseguita la ricerca in avanti tramite le righe fino a quando non trovata una riga in grado di accettare un punto di interruzione.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)   
 [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)