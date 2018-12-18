---
title: IDebugDocumentHelper::AddDBCSText | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentHelper.AddDBCSText
apilocation: pdm.dll
helpviewer_keywords: IDebugDocumentHelper::AddDBCSText
ms.assetid: 5e5011b2-bbb4-491b-9a11-eb2846be44aa
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 37cd0f2953483e23636c3a17d7726bc2c438b303
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthelperadddbcstext"></a>IDebugDocumentHelper::AddDBCSText
Aggiunge una stringa DBCS alla fine di questo documento.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT AddDBCSText(  
   LPCSTR  pszText  
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
>  Se questo metodo viene chiamato dopo `IDebugDocumentHelper::AddDeferredText` è stato chiamato, `E_FAIL` viene restituito.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)   
 [Interfaccia IDebugDocumentTextEvents](../../winscript/reference/idebugdocumenttextevents-interface.md)