---
title: IActiveScriptAuthor::GetChars | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetChars
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetChars
ms.assetid: a73ba263-12f7-4d5f-b4c8-9ad7e2d5d3cb
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: abc9c819c2dd4a75d6223af86b4fe89baebc186b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthorgetchars"></a>IActiveScriptAuthor::GetChars
Restituisce il set di caratteri di completamento per un contesto di richiesta di completamento.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetChars(  
   DWORD            fRequestedList,  
   BSTR             *pbstrChars  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `fRequestedList`  
 [in] Il contesto di richiesta di completamento.  
  
|Costante|Valore|Descrizione|  
|--------------|-----------|-----------------|  
|SCRIPT_CMPL_ENUM_TRIGGER|0x0001|Richiede l'enumerazione di sinistra.|  
|SCRIPT_CMPL_MEMBER_TRIGGER|0x0002|Richiede il contesto di completamento del membro.|  
|SCRIPT_CMPL_PARAM_TRIGGER|0x0003|Richiede l'elenco di parametri.|  
|SCRIPT_CMPL_COMMIT|0x0004|Completamento delle richieste dell'elenco di parametri.|  
  
 `pbstrChars`  
 [out] I caratteri che corrispondono al contesto di richiesta di completamento.  
  
|`fRequestedList`parametro|Caratteri restituiti|  
|--------------------------------|-------------------------|  
|SCRIPT_CMPL_ENUM_TRIGGER|"."|  
|SCRIPT_CMPL_MEMBER_TRIGGER|"="|  
|SCRIPT_CMPL_PARAM_TRIGGER|"(,"|  
|SCRIPT_CMPL_COMMIT|"()"|  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)