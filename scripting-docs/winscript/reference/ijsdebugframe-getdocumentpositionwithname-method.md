---
title: 'Metodo ijsdebugframe:: Getdocumentpositionwithname | Documenti Microsoft'
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugFrame.GetDocumentPositionWithName
apilocation: jscript9diag.dll
ms.assetid: 1d994714-2c87-4a9e-ae14-a15eec9520c7
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 49afb5903e190280d226a24b22dc389041861c52
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugframegetdocumentpositionwithname-method"></a>Metodo IJsDebugFrame::GetDocumentPositionWithName
Restituisce la posizione corrente dello stack frame corrente all'interno del documento a livello di utente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetDocumentPositionWithName(  
   BSTR *pDocumentName,  
   DWORD *pLine,  
   DWORD *pColumn  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pDocumentName`  
 [out] Per gli script statici, un URL al documento. Per gli script dinamici, viene restituito un nome contenente il tipo di script (ad esempio, codice eval, il codice di funzione e così via).  
  
 `pLine`  
 [out] posizione della riga in base 1 all'interno del documento.  
  
 `pColumn`  
 [out] posizione della riga in base 1 all'interno del documento.  
  
## <a name="return-value"></a>Valore restituito  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IJsDebugFrame](../../winscript/reference/ijsdebugframe-interface.md)