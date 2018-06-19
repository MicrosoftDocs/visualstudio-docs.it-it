---
title: IDebugDocumentPosition2::GetRange | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDocumentPosition2::GetRange
helpviewer_keywords:
- IDebugDocumentPosition2::GetRange
ms.assetid: 91a06ee7-253a-4215-be22-04bf57305aa8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d4a80bebba1000c73af2d7e2cfd05e67fa44b1b7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
ms.locfileid: "31109201"
---
# <a name="idebugdocumentposition2getrange"></a>IDebugDocumentPosition2::GetRange
Ottiene l'intervallo per la posizione del documento.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetRange(   
   TEXT_POSITION* pBegPosition,  
   TEXT_POSITION* pEndPosition  
);  
```  
  
```csharp  
int GetRange(   
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
 L'intervallo specificato in una posizione di documento per un punto di interruzione del percorso viene utilizzato dal motore di debug (DE) per la ricerca con un'istruzione che effettivamente fornisce codice. Si consideri il codice di esempio seguente:  
  
```  
Line 5: // comment  
Line 6: x = 1;  
```  
  
 Riga 5 non contribuisce a nessun codice di programma sottoposto a debug. Se il debugger che imposta il punto di interruzione nella riga 5 desidera DE per eseguire la ricerca di una determinata quantità per la prima riga di codice, il debugger specificare un intervallo che include righe candidato aggiuntivo in un punto di interruzione potrebbe essere posizionato in modo corretto. La Germania viene quindi eseguita la ricerca in avanti tramite le righe fino a quando non trovata una riga in grado di accettare un punto di interruzione.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)