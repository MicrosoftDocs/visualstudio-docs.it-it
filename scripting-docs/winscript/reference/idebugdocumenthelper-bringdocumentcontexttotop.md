---
title: IDebugDocumentHelper::BringDocumentContextToTop | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.BringDocumentContextToTop
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::BringDocumentContextToTop
ms.assetid: cf9751c5-e9b7-45c6-b084-3f3873dbf01d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 665d194abd2eed02096a2295ec0683a03830fb8d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthelperbringdocumentcontexttotop"></a>IDebugDocumentHelper::BringDocumentContextToTop
Inserisce un contesto di questo documento nella parte superiore nell'interfaccia utente del debugger.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT BringDocumentContextToTop(  
   IDebugDocumentContext*  pddc  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pddc`  
 Contesto di documento per portare in primo piano nell'interfaccia utente del debugger.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo inserisce un contesto di questo documento nella parte superiore nell'interfaccia utente del debugger.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)