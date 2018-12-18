---
title: IDiaAddressMap::get_relativeVirtualAddressEnabled | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::get_relativeVirtualAddressEnabled method
ms.assetid: 4c48af81-7148-4d9a-818e-dbe62cbfc638
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 25159556d44ca37d7938e67e67f1b9900a05010b
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiaaddressmapgetrelativevirtualaddressenabled"></a>IDiaAddressMap::get_relativeVirtualAddressEnabled
Indica se è abilitato il calcolo e l'utilizzo di indirizzi virtuali relativi (RVA).  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT get_relativeVirtualAddressEnabled (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pRetVal  
 [out] Restituisce `TRUE` se è abilitato il calcolo di RVA.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 RVA viene abilitati se i segmenti sono state inizialmente caricati da un file PDB. L'utilizzo di RVA può essere disabilitata temporaneamente chiamando il [idiaaddressmap:: Put_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md) metodo.  
  
 Inoltre, nuove intestazioni immagine possono essere stabilite chiamando il [idiaaddressmap:: Set_imageheaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) metodo seguita da una chiamata al `put_relativeVirtualAddressEnabled` metodo per consentire l'utilizzo di RVA utilizzando nuove intestazioni di immagine.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [Set_imageheaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)   
 [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)