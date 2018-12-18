---
title: IActiveScriptSite::OnLeaveScript | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptSite.OnLeaveScript
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnLeaveScript
ms.assetid: 79af0e22-fbe3-4fae-8a5f-7af8b857678d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aba20c13dc5568165641c5c7b8e871e0b5e8f322
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsiteonleavescript"></a>IActiveScriptSite::OnLeaveScript
Comunica all'host che il motore di script ha restituito dall'esecuzione di codice di script.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT OnLeaveScript(void);  
```  
  
## <a name="return-value"></a>Valore restituito  
 Se l'esito è positivo, restituisce `S_OK`.  
  
## <a name="remarks"></a>Note  
 Il motore di script è necessario chiamare questo metodo prima di restituire il controllo a un'applicazione chiamante immesso il motore di script. Ad esempio, se lo script chiama un oggetto che viene generato un evento gestito dal motore di script, il motore di script deve chiamare il [IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md) metodo prima di eseguire l'evento e deve chiamare `IActiveScriptSite::OnLeaveScript`dopo l'esecuzione dell'evento prima di restituire l'oggetto che ha generato l'evento. Chiamate a questo metodo possono essere nidificate. Ogni chiamata a `IActiveScriptSite::OnEnterScript` richiede una chiamata corrispondente a questo metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)