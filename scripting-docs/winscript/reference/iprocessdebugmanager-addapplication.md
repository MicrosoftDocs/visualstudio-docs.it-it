---
title: IProcessDebugManager::AddApplication | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IProcessDebugManager.AddApplication
apilocation: pdm.dll
helpviewer_keywords: IProcessDebugManager::AddApplication
ms.assetid: 73828299-11eb-4c58-ad70-f80f2d0eede8
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a221aa0038b0b3fd5046b9ada08e2de86f33a895
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iprocessdebugmanageraddapplication"></a>IProcessDebugManager::AddApplication
Aggiunge un'applicazione all'elenco del gestore di machine debug delle applicazioni in esecuzione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT AddApplication(  
   IDebugApplication*  pda,  
   DWORD*              pdwAppCookie  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pda`  
 [in] Applicazione di debug da aggiungere all'elenco delle applicazioni in esecuzione.  
  
 `pdwAppCookie`  
 [out] Un cookie utilizzato per rimuovere l'applicazione di debug machine manager.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo aggiunge un'applicazione per l'esecuzione elenco di applicazioni in Gestione computer debug.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IProcessDebugManager](../../winscript/reference/iprocessdebugmanager-interface.md)   
 [IProcessDebugManager::RemoveApplication](../../winscript/reference/iprocessdebugmanager-removeapplication.md)