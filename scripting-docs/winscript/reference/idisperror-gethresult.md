---
title: IDispError::GetHresult | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispError.GetHresult
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDispError::GetHresult
ms.assetid: a14d566e-473f-497b-a2f9-85331433e6c9
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 859708b8aec4f89dd1ea49bf6e248d7bcade7624
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idisperrorgethresult"></a>IDispError::GetHresult
Recupera il codice di errore di `IDispError` oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetHresult(  
   HRESULT*  phr  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `phr`  
 [out] Specifica il codice di errore.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo recupera il codice di errore di `IDispError` oggetto.  
  
> [!NOTE]
>  Questo metodo non è implementato.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDispError](../../winscript/reference/idisperror-interface.md)