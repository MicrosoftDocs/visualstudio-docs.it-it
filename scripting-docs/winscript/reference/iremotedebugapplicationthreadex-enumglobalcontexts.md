---
title: IRemoteDebugApplicationThreadEx:EnumGlobalContexts | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IRemoteDebugApplicationThreadEx:EnumGlobalContexts
apilocation:
- scrobj.dll
helpviewer_keywords:
- IRemoteDebugApplicationThreadEx:EnumGlobalContexts
ms.assetid: a6c0bc3f-4afc-41e1-b734-06e252c5b171
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c57dc014e9f448e58db5fe6509536db5023b22dd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplicationthreadexenumglobalcontexts"></a>IRemoteDebugApplicationThreadEx:EnumGlobalContexts
Enumera i contesti di espressione globale per tutte le lingue in esecuzione in questo thread.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT EnumGlobalExpressionContexts(  
   IEnumDebugExpressionContexts**  ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppEnum`  
 [out] Enumeratore che elenca i contesti di espressione globale per tutte le lingue in esecuzione in questo thread.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note