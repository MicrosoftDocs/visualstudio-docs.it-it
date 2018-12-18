---
title: ISimpleConnectionPoint::Unadvise | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- ISimpleConnectionPoint.Unadvise
apilocation:
- pdm.dll
helpviewer_keywords:
- ISimpleConnectionPoint::Unadvise
ms.assetid: eae06a58-ed42-4839-aad4-14420b15343f
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7f926f206bb8a27e6265fd147909a5adb13c3543
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="isimpleconnectionpointunadvise"></a>ISimpleConnectionPoint::Unadvise
Termina una connessione consultiva precedentemente stabilita tramite `ISimpleConnectionPoint::Advise`.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT Unadvise(  
   DWORD  dwCookie  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwCookie`  
 [in] Token di connessione per terminare, come restituito dal `ISimpleConnectionPoint::Advise`.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Quando una connessione consultiva è terminata, il punto di connessione chiamate di `Release` metodo sul puntatore che è stato salvato per la connessione durante il `ISimpleConnectionPoint::Advise` metodo. Che chiamano inverte il `AddRef` che è stata eseguita durante il `ISimpleConnectionPoint::Advise` quando il punto di connessione chiama il sink consultivo `QueryInterface`.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia ISimpleConnectionPoint](../../winscript/reference/isimpleconnectionpoint-interface.md)