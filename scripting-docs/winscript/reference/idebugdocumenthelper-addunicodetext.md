---
title: IDebugDocumentHelper::AddUnicodeText | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugDocumentHelper.AddUnicodeText
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::AddUnicodeText
ms.assetid: f4ef648e-c55d-4ef0-8df3-e808b798d3b8
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f387142675b0def99fb2cc0695bd3f9416d66809
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthelperaddunicodetext"></a>IDebugDocumentHelper::AddUnicodeText
Aggiunge una stringa Unicode alla fine di questo documento.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT AddUnicodeText(  
   LPCOLESTR  pszText  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pszText`  
 [in] Puntatore a una stringa con terminazione null contenente il testo.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_FAIL`|Il metodo è riuscito ad aggiungere i caratteri.|  
  
## <a name="remarks"></a>Note  
 Questo metodo genera `IDebugDocumentTextEvents` notifiche.  
  
> [!NOTE]
>  Se questo metodo viene chiamato dopo `AddDeferredText` è stato chiamato, `E_FAIL` viene restituito.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)   
 [Interfaccia IDebugDocumentTextEvents](../../winscript/reference/idebugdocumenttextevents-interface.md)