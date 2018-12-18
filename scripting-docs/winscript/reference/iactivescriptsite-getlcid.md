---
title: IActiveScriptSite::GetLCID | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptSite.GetLCID
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptSite_GetLCID
ms.assetid: 7b4a2dc1-bcf6-4bbf-884e-97b305a28eb7
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a6e128f5ac5de11b45af59c83750411c35e6efa7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitegetlcid"></a>IActiveScriptSite::GetLCID
Recupera l'identificatore delle impostazioni locali associato all'interfaccia utente dell'host. Il motore di script utilizza l'identificatore per assicurarsi che le stringhe di errore e altri elementi dell'interfaccia utente generati dal motore vengano visualizzati nella lingua corrispondente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetLCID(  
    LCID *plcid  // address of variable for language identifier  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `plcid`  
 [out] Indirizzo di una variabile che riceve l'identificatore delle impostazioni locali per gli elementi dell'interfaccia utente visualizzata dal motore di scripting.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|Valore restituito|Significato|  
|------------------|-------------|  
|`S_OK`|Operazione completata.|  
|`E_NOTIMPL`|Questo metodo non è implementato. Utilizzare le impostazioni locali definiti dal sistema.|  
|`E_POINTER`|È stato specificato un puntatore non valido.|  
  
## <a name="remarks"></a>Note  
 Se questo metodo restituisce `E_NOTIMPL`, utilizzare l'identificatore delle impostazioni locali definiti dal sistema.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)