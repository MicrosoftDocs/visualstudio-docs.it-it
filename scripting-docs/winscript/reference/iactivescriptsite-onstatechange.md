---
title: IActiveScriptSite::OnStateChange | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.OnStateChange
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnStateChange
ms.assetid: 3e9c5cbe-ca8e-426a-84fd-04e9c2daac7e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fae7782d713ab226e57e687cda8eb4ccdb54cf20
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsiteonstatechange"></a>IActiveScriptSite::OnStateChange
Comunica all'host che il motore di script è stato modificato gli stati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT OnStateChange(  
    SCRIPTSTATE ssScriptState  // new state of engine  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ssScriptState`  
 [in] Valore che indica il nuovo stato di script. Vedere il [IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md) metodo per una descrizione degli stati.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'esito è positivo, restituisce `S_OK`.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)