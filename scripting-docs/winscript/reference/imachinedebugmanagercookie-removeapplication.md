---
title: IMachineDebugManagerCookie::RemoveApplication | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IMachineDebugManagerCookie.RemoveApplication
apilocation:
- scrobj.dll
helpviewer_keywords:
- IMachineDebugManagerCookie::RemoveApplication
ms.assetid: af8f4a52-ec5e-48fa-87de-234d5e6528d0
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fe0849b2f580eac7759db36335823a737a198e55
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="imachinedebugmanagercookieremoveapplication"></a>IMachineDebugManagerCookie::RemoveApplication
Rimuove l'esecuzione di un'applicazione elenco di applicazioni.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT RemoveApplication(  
   DWORD  dwDebugAppCookie,  
   DWORD  dwAppCookie  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwDebugAppCookie`  
 [in] Cookie che identifica l'applicazione di debug.  
  
 `dwAppCookie`  
 [in] Il cookie specificato quando l'applicazione è stato aggiunto all'elenco di applicazioni.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo viene chiamato dal gestore di debug del processo ogni volta che `IProcessDebugManager::RemoveApplication` viene chiamato.  
  
## <a name="see-also"></a>Vedere anche  
 [IMachineDebugManagerCookie::AddApplication](../../winscript/reference/imachinedebugmanagercookie-addapplication.md)   
 [Interfaccia IMachineDebugManagerCookie](../../winscript/reference/imachinedebugmanagercookie-interface.md)   
 [IProcessDebugManager::RemoveApplication](../../winscript/reference/iprocessdebugmanager-removeapplication.md)