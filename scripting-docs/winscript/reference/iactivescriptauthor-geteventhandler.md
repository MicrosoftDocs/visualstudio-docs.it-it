---
title: IActiveScriptAuthor::GetEventHandler | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptAuthor.GetEventHandler
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptAuthor::GetEventHandler
ms.assetid: 87c7a71d-46b9-448c-b34d-394105e20982
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2b09f900162b6dba82696c946b53ab131691530c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthorgeteventhandler"></a>IActiveScriptAuthor::GetEventHandler
Restituisce lo scriptlet che ha gli attributi specificati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetEventHandler(  
   IDispatch          *pdisp,  
   LPCOLESTR          pszItem,  
   LPCOLESTR          pszSubItem,  
   LPCOLESTR          pszEvent,  
   IScriptEntry       **ppse  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pdisp`  
 [in] Il `IDispatch` oggetto che corrisponde alla `NamedItem` a cui è collegato lo scriptlet.  
  
 `pszItem`  
 [in] Ottiene o imposta l'indirizzo del buffer dell'identificatore del nome completo scriptlet nell'host di primo livello.  
  
 `pszSubItem`  
 [in] Ottiene o imposta l'indirizzo del buffer dell'identificatore del nome completo scriptlet nell'host di secondo livello. Impostare su NULL se il nome contiene un solo livello.  
  
 `pszEvent`  
 [in] L'indirizzo di un buffer che contiene il nome dell'evento. Lo scriptlet è un gestore eventi per questo evento.  
  
 `ppse`  
 [out] L'indirizzo di una variabile che riceve un puntatore di `IScriptEntry` interfaccia di scriptlet che ha gli attributi specificati.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)   
 [Interfaccia IScriptEntry](../../winscript/reference/iscriptentry-interface.md)