---
title: 'Metodo ijsdebugbreakpoint:: Getdocumentposition | Documenti Microsoft'
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJSDebugBreakPoint.GetDocumentPosition
apilocation: jscript9diag.dll
ms.assetid: 886df8ba-a59a-48a7-87f2-3b669e71528f
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3c33751b0173626814f042fdc54a7d496b644573
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugbreakpointgetdocumentposition-method"></a>Metodo IJsDebugBreakPoint::GetDocumentPosition
Restituisce la posizione dell'istruzione in cui è stato associato il punto di interruzione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetDocumentPosition(  
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
 [Interfaccia IJsDebugBreakPoint](../../winscript/reference/ijsdebugbreakpoint-interface.md)