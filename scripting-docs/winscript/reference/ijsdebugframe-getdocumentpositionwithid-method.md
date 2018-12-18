---
title: 'Metodo ijsdebugframe:: Getdocumentpositionwithid | Documenti Microsoft'
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugFrame.GetDocumentPositionWithId
apilocation: jscript9diag.dll
ms.assetid: 48f8eb26-8ae4-4d5c-bd94-796023b03bcb
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f11e9ad51094522adec99ef82681f42ac500a251
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugframegetdocumentpositionwithid-method"></a>Metodo IJsDebugFrame::GetDocumentPositionWithId
Restituisce la posizione corrente dello stack frame corrente all'interno del documento a livello di utente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetDocumentPositionWithId(  
   UINT64 *pDocumentId,  
   DWORD *pCharacterOffset,  
   DWORD *pStatementCharCount  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pDocumentId`  
 [out] ID univoco per un documento di origine (puntatore al IDebugDocumentText).  
  
 `pCharacterOffset`  
 [out] L'offset carattere in base zero dall'inizio dello script.  
  
 `pStatementCharCount`  
 [out] La lunghezza dell'istruzione corrente, che inizia da * pCharacterOffset, in caratteri.  
  
## <a name="return-value"></a>Valore restituito  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IJsDebugFrame](../../winscript/reference/ijsdebugframe-interface.md)