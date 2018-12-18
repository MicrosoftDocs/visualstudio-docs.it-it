---
title: ISimpleConnectionPoint::Advise | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- ISimpleConnectionPoint.Advise
apilocation:
- pdm.dll
helpviewer_keywords:
- ISimpleConnectionPoint::Advise
ms.assetid: 59ded60d-b938-4110-aca3-e69ba234ca9a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7ec43d135401386a3f54f2c047040897f038ba19
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="isimpleconnectionpointadvise"></a>ISimpleConnectionPoint::Advise
Stabilisce una connessione tra l'oggetto punto di connessione semplice e il sink del client.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT Advise(  
   IDispatch*  pdisp,  
   DWORD*      pdwCookie  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pdisp`  
 [in] Puntatore al `IDispatch` del sink di notifica dell'interfaccia sul client. Il sink del client riceve le chiamate in uscita dal punto di connessione semplice.  
  
 `pdwCookie`  
 [out] Puntatore al token restituito che identifica in modo univoco questa connessione. Il chiamante utilizza il token in un secondo momento per eliminare la connessione tramite il passaggio al `ISimpleConnectionPoint::Unadvise` metodo. Se la connessione non è stata stabilita correttamente, questo valore è zero.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo consente di stabilire una connessione tra l'oggetto punto di connessione semplice e il sink del client.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia ISimpleConnectionPoint](../../winscript/reference/isimpleconnectionpoint-interface.md)   
 [ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)