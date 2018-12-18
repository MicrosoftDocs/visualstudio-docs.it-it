---
title: IActiveScriptSiteDebug::GetApplication | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteDebug.GetApplication
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteDebug::GetApplication
ms.assetid: 4400f1b1-3108-4a71-b1f1-43586fe1227c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e33bf254d2e688451f1b69a3b3eb1b676a9e9b1a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitedebuggetapplication"></a>IActiveScriptSiteDebug::GetApplication
Restituisce l'oggetto di debug dell'applicazione associata a questo sito di script.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetApplication(  
   IDebugApplication**  ppda  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppda`  
 [out] Puntatore all'oggetto dell'applicazione di debug associato al sito di script.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_NOTIMPL`|L'host non supporta direttamente il debug.|  
  
## <a name="remarks"></a>Note  
 Il `GetApplication` metodo fornisce un modo per un host intelligente definire l'oggetto di applicazione a cui appartiene ogni script. Motori di script devono tentare di chiamare questo metodo per ottenere le applicazioni che lo contiene e ricorrere a `IProcessDebugManager::GetDefaultApplication` in caso di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptSiteDebug](../../winscript/reference/iactivescriptsitedebug-interface.md)   
 [IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)