---
title: IProcessDebugManager::GetDefaultApplication | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IProcessDebugManager.GetDefaultApplication
apilocation:
- pdm.dll
helpviewer_keywords:
- IProcessDebugManager::GetDefaultApplication
ms.assetid: 6c991faa-ea40-4d18-a1b8-6e7d0de6dd43
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 27fc46e8a5e07c4eb25c5e246db138a27e5511ae
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iprocessdebugmanagergetdefaultapplication"></a>IProcessDebugManager::GetDefaultApplication
Restituisce un oggetto di applicazione predefinito per il processo corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetDefaultApplication(  
   IDebugApplication**  ppda  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppda`  
 [out] L'oggetto di applicazione di debug per questa applicazione.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo crea un nuovo oggetto di applicazione di debug e lo aggiunge all'esecuzione elenco di applicazioni, se necessario.  
  
 Motori di linguaggio devono utilizzare l'applicazione specificata dal `GetDefaultApplication` metodo se sono in esecuzione in un host che non fornisce un'applicazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IProcessDebugManager](../../winscript/reference/iprocessdebugmanager-interface.md)