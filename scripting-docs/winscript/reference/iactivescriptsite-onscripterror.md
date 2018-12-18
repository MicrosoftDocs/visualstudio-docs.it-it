---
title: IActiveScriptSite::OnScriptError | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptSite.OnScriptError
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptSite_OnScriptError
ms.assetid: 5c9c85cc-21ad-4232-be83-a24cc7570108
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4ae066fe7fa04a5c97dec618c65ccee3f90984a0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsiteonscripterror"></a>IActiveScriptSite::OnScriptError
Comunica all'host che si è verificato un errore di esecuzione durante l'esecuzione il motore di script.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT OnScriptError(  
    IActiveScriptError *pase  // address of error interface  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pase`  
 [in] Indirizzo dell'oggetto errore [IActiveScriptError](../../winscript/reference/iactivescripterror.md) interfaccia. Un host può utilizzare questa interfaccia per ottenere informazioni relative all'errore di esecuzione.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce `S_OK` se l'errore è stato gestito correttamente o codice di errore è stato definito in caso contrario OLE.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)