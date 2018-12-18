---
title: IActiveScriptSiteDebug32::GetApplication | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 533d770d-06a4-4693-873e-255c9c6f0df0
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: bb7fdf5a6d0b380a8024cfdfa70282bcf80ba16d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitedebug32getapplication"></a>IActiveScriptSiteDebug32::GetApplication
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
 [Interfaccia IActiveScriptSiteDebug32](../../winscript/reference/iactivescriptsitedebug32-interface.md)   
 [IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)