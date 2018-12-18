---
title: IProcessDebugManager::RemoveApplication | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IProcessDebugManager.RemoveApplication
apilocation: pdm.dll
helpviewer_keywords: IProcessDebugManager::RemoveApplication
ms.assetid: 334e869d-81ae-4d30-9e89-89763ad4f184
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b8d95be6227f192596e174095744a4e0247e0c37
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iprocessdebugmanagerremoveapplication"></a>IProcessDebugManager::RemoveApplication
Rimuove l'esecuzione di un'applicazione elenco di applicazioni.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT RemoveApplication(  
   DWORD  dwAppCookie  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwAppCookie`  
 [in] Cookie fornito da `IProcessDebugManager::AddApplication` quando l'applicazione è stato aggiunto all'elenco di applicazioni.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo rimuove l'esecuzione di un'applicazione elenco di applicazioni.  
  
## <a name="see-also"></a>Vedere anche  
 [IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)   
 [Interfaccia IProcessDebugManager](../../winscript/reference/iprocessdebugmanager-interface.md)