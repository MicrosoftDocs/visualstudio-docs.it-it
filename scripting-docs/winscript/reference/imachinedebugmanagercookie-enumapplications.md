---
title: IMachineDebugManagerCookie::EnumApplications | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IMachineDebugManagerCookie.EnumApplications
apilocation: scrobj.dll
helpviewer_keywords: IMachineDebugManagerCookie::EnumApplications
ms.assetid: 03f863cf-fa7f-4ec4-b1a1-1ae0ad296c39
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 927457fca1972148798b543dceefa19e107f45d6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="imachinedebugmanagercookieenumapplications"></a>IMachineDebugManagerCookie::EnumApplications
Restituisce un enumeratore dell'elenco corrente delle applicazioni in esecuzione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT EnumApplications(  
   IEnumRemoteDebugApplications**  ppeda  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppeda`  
 [out] Enumeratore che contiene l'elenco corrente delle applicazioni in esecuzione.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo restituisce un enumeratore dell'elenco corrente delle applicazioni in esecuzione. Il debugger IDE utilizza questo metodo per visualizzare e associare le applicazioni a scopo di debug.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IMachineDebugManagerCookie](../../winscript/reference/imachinedebugmanagercookie-interface.md)