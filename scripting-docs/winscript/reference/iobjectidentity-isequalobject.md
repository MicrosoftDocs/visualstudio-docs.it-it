---
title: IObjectIdentity::IsEqualObject | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IObjectIdentity.IsEqualObject
apilocation:
- scrobj.dll
helpviewer_keywords:
- IsEqualObject method
ms.assetid: 78c5c5c2-d299-4036-986c-7c1d87cbe7cd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 52e386055e458568f8d4076a37489b7b2397f399
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iobjectidentityisequalobject"></a>IObjectIdentity::IsEqualObject
Determina se un oggetto è uguale all'oggetto corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT IsEqualObject(  
  IUnknown*punk  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `punk`  
 [in] Indirizzo dell'oggetto da confrontare con l'oggetto corrente.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Gli oggetti sono uguali.|  
|`S_FALSE`|Gli oggetti non sono uguali.|  
  
## <a name="remarks"></a>Note  
 Un'implementazione del `IsEqualObject` metodo dovrebbe restituire `S_OK` solo se gli oggetti sono identici.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IObjectIdentity](../../winscript/reference/iobjectidentity-interface.md)