---
title: 'Metodo ijsdebugframe:: Evaluate | Documenti Microsoft'
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugFrame.Evaluate
apilocation: jscript9diag.dll
ms.assetid: 0ee61340-37b8-4fbb-a028-748b5315e279
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 38e826048e85456ca63e069de67701b1fc3e9f04
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugframeevaluate-method"></a>Metodo IJsDebugFrame::Evaluate
Valutare un'espressione nel contesto dello stack frame corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT Evaluate(  
   LPCOLESTR pExpressionText,  
   IJsDebugProperty **ppDebugProperty,  
   BSTR *pError  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pExpressionText`  
 [in] L'espressione da valutare.  
  
 `ppDebugProperty`  
 [out] Oggetto che rappresenta il Visualizzatore proprietà.  
  
 `pError`  
 [out] Il messaggio di errore, se si verifica un errore.  
  
## <a name="return-value"></a>Valore restituito  
  
## <a name="remarks"></a>Note  
 Restituisce le operazioni seguenti: S_OK: esito positivo della valutazione, * ppDebugProperty contiene i risultati della valutazione. Valutazione di S_FALSE: Genera un errore o l'operazione di valutazione non è supportata, \*pError contiene il messaggio di errore.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IJsDebugFrame](../../winscript/reference/ijsdebugframe-interface.md)