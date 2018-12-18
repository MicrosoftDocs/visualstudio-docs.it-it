---
title: IActiveScript::GetScriptSite | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScript.GetScriptSite
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptSite
ms.assetid: 83a2a89d-93d0-4cbd-9244-91a730cb406b
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 961483d45c72018bc216306d6c1aba0400a367ad
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptgetscriptsite"></a>IActiveScript::GetScriptSite
Recupera l'oggetto sito associato con il motore di Script di Windows.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetScriptSite(  
    REFIID iid,           // interface identifier  
    void **ppvSiteObject  // address of host site interface  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `iid`  
 [in] Identificatore dell'interfaccia richiesta.  
  
 `ppvSiteObject`  
 [out] Indirizzo della posizione che riceve il puntatore a interfaccia per l'oggetto sito dell'host.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|Valore restituito|Significato|  
|------------------|-------------|  
|`S_OK`|Operazione completata.|  
|`E_INVALIDARG`|Un argomento non valido.|  
|`E_NOINTERFACE`|L'interfaccia specificata non è supportata.|  
|`E_POINTER`|È stato specificato un puntatore non valido.|  
|`S_FALSE`|Non è stato impostato alcun sito. il `ppvSiteObject` parametro è impostato su `NULL`.|  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScript](../../winscript/reference/iactivescript.md)