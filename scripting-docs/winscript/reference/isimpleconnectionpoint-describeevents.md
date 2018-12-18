---
title: ISimpleConnectionPoint::DescribeEvents | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- ISimpleConnectionPoint.DescribeEvents
apilocation:
- pdm.dll
helpviewer_keywords:
- ISimpleConnectionPoint::DescribeEvents
ms.assetid: 659ea05f-d41e-424a-bb38-df7672b2d135
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 42dab9558d46eae0fbb640c60264a79877708321
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="isimpleconnectionpointdescribeevents"></a>ISimpleConnectionPoint::DescribeEvents
Restituisce il nome per ogni evento e i DISPID in un intervallo specificato di eventi.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT DescribeEvents(  
   ULONG    iEvent,  
   ULONG    cEvents,  
   DISPID*  prgid,  
   BSTR*    prgbstr,  
   ULONG*   pcEventsFetched  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `iEvent`  
 [in] Indice del primo evento da recuperare.  
  
 `cEvents`  
 [in] Numero di eventi da recuperare.  
  
 `prgid`  
 [out] Matrice di valori DISPID evento.  
  
 `prgbstr`  
 [out] Matrice di nomi di evento.  
  
 `pcEventsFetched`  
 [out] Il numero effettivo di eventi recuperati.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`S_FALSE`|Numero di eventi sono stati richiesti che non erano disponibili. Gli eventi disponibili sono rappresentati con DISPID_NULL e BSTR null.|  
|`E_INVALIDARG`|È non stato possibile recuperare alcun elemento.|  
  
## <a name="remarks"></a>Note  
 Questo metodo restituisce il DISPID e il nome per ogni evento in un intervallo specificato di eventi.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia ISimpleConnectionPoint](../../winscript/reference/isimpleconnectionpoint-interface.md)