---
title: IActiveScriptSite::OnEnterScript | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptSite.OnEnterScript
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnEnterScript
ms.assetid: 1ed9178c-fe80-41c4-b74d-23b85f9cddbf
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eb4514770faaaad46c8590e6df03488e3d5bc679
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsiteonenterscript"></a>IActiveScriptSite::OnEnterScript
Comunica all'host che il motore di script ha iniziato a eseguire il codice di script.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT OnEnterScript(void);  
```  
  
## <a name="return-value"></a>Valore restituito  
 Se l'esito è positivo, restituisce `S_OK`.  
  
## <a name="remarks"></a>Note  
 Il motore di script è necessario chiamare questo metodo per ogni singola voce o il rientro nel motore di scripting. Ad esempio, se lo script chiama un oggetto che viene generato un evento gestito dal motore di script, il motore di script deve chiamare `IActiveScriptSite::OnEnterScript` prima esecuzione dell'evento e deve chiamare il [IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md) metodo dopo l'esecuzione dell'evento, ma prima di restituire l'oggetto che ha generato l'evento. Chiamate a questo metodo possono essere nidificate. Ogni chiamata a questo metodo richiede una chiamata corrispondente a `IActiveScriptSite::OnLeaveScript`.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)