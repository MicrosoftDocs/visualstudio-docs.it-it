---
description: Consente di controllare il modo in cui il DIA SDK calcola gli indirizzi virtuali virtuali e relativi per gli oggetti di debug.
title: IDiaAddressMap | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap interface
ms.assetid: e6467529-508c-4328-85d7-89444ae4d1c1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 085ba4e75eab1dd67585b3926b71edd5dce88d72
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159467"
---
# <a name="idiaaddressmap"></a>IDiaAddressMap
Consente di controllare il modo in cui il DIA SDK calcola gli indirizzi virtuali virtuali e relativi per gli oggetti di debug.

## <a name="syntax"></a>Sintassi

```
IDiaAddressMap : IUnknown
```

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 La tabella seguente illustra i metodi di `IDiaAddressMap` .

|Metodo|Descrizione|
|------------|-----------------|
|[IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)|Indica se è stata stabilita una mappa degli indirizzi per una determinata sessione.|
|[IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)|Specifica se la mappa degli indirizzi deve essere utilizzata per tradurre gli indirizzi dei simboli.|
|[IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)|Indica se il calcolo e l'utilizzo di indirizzi virtuali relativi sono abilitati.|
|[IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)|Consente al client di abilitare o disabilitare il calcolo degli indirizzi virtuali relativi.|
|[IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)|Recupera l'allineamento dell'immagine corrente.|
|[IDiaAddressMap::put_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)|Imposta l'allineamento dell'immagine.|
|[IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)|Imposta le intestazioni dell'immagine per abilitare la conversione degli indirizzi virtuali relativi.|
|[IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)|Fornisce una mappa degli indirizzi per supportare le traduzioni del layout dell'immagine.|

## <a name="remarks"></a>Commenti
 Il controllo fornito da questa interfaccia è incapsulato in due set di dati forniti: intestazioni di immagine e mappe di indirizzi. La maggior parte dei client usa il metodo [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) per trovare le informazioni di debug appropriate per un'immagine e il metodo può in genere individuare tutte le intestazioni necessarie e mappare i dati stessi. Tuttavia, alcuni client implementano l'elaborazione specializzata e la ricerca di dati. Tali client utilizzano i metodi dell' `IDiaAddressMap` interfaccia per fornire la DIA SDK con i risultati della ricerca.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Questa interfaccia è disponibile dall'oggetto di sessione DIA. Il client chiama il `QueryInterface` metodo sull'interfaccia dell'oggetto della sessione dia, in genere [IDiaSession](../../debugger/debug-interface-access/idiasession.md), per recuperare l' `IDiaAddressMap` interfaccia.

## <a name="requirements"></a>Requisiti
 Intestazione: dia2. h

 Libreria: diaguids. lib

 DLL: msdia80.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
