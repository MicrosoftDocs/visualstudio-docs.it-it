---
description: Consente al client di abilitare o disabilitare il calcolo e l'utilizzo di indirizzi RVA (relative Virtual Address).
title: IDiaAddressMap::put_relativeVirtualAddressEnabled | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_relativeVirtualAddressEnabled method
ms.assetid: 767c078e-8ad7-4940-9e00-cae7704aadee
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7c3aab1379a39ee6abfd977350743e36c9792efb
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158322"
---
# <a name="idiaaddressmapput_relativevirtualaddressenabled"></a>IDiaAddressMap::put_relativeVirtualAddressEnabled
Consente al client di abilitare o disabilitare il calcolo e l'utilizzo di indirizzi RVA (relative Virtual Address).

## <a name="syntax"></a>Sintassi

```C++
HRESULT put_relativeVirtualAddressEnabled ( 
   BOOL NewVal
);
```

#### <a name="parameters"></a>Parametri
 NewVal

in Impostare su `TRUE` per abilitare o `FALSE` disabilitare.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 È possibile recuperare gli indirizzi per gli oggetti di debug descritti dalle interfacce DIA e relativi alla base dell'immagine eseguibile come indirizzi virtuali relativi.

 L'uso di RVA è abilitato quando i segmenti vengono inizialmente caricati da un file PDB. Per ottenere lo stato corrente dell'uso di RVA, chiamare il metodo [IDiaAddressMap:: get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) .

 Il `put_relativeVirtualAddress` metodo deve essere chiamato per abilitare RVA dopo una chiamata riuscita al metodo [IDiaAddressMap:: set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) hanno stabilito nuove intestazioni di immagine.

## <a name="see-also"></a>Vedi anche
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)
- [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)
