---
title: 'Idiaaddressmap:: Put_relativevirtualaddressenabled | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_relativeVirtualAddressEnabled method
ms.assetid: 767c078e-8ad7-4940-9e00-cae7704aadee
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dbbe2c2299a26834ac40c787aea5504ae7d0ed8a
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiaaddressmapputrelativevirtualaddressenabled"></a>IDiaAddressMap::put_relativeVirtualAddressEnabled
Consente al client abilitare o disabilitare il calcolo e l'utilizzo di indirizzi virtuali relativi (RVA).  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT put_relativeVirtualAddressEnabled (   
   BOOL NewVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 NewVal  
 [in] Impostare su `TRUE` per abilitare, o `FALSE` disabilitare.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Gli indirizzi per gli oggetti di debug descritti dalle interfacce DIA e rispetto alla base, dell'immagine dell'eseguibile possono essere recuperati come indirizzi virtuali relativi.  
  
 L'utilizzo di RVA è abilitato quando segmenti vengono inizialmente caricati da un file PDB. Per ottenere lo stato corrente dell'utilizzo di RVA, chiamare il [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) metodo.  
  
 Il `put_relativeVirtualAddress` metodo deve essere chiamato per abilitare RVA dopo una chiamata per il [idiaaddressmap:: Set_imageheaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) metodo stabilito nuove intestazioni di immagine.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [Get_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)   
 [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)