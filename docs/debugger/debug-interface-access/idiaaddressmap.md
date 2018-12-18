---
title: IDiaAddressMap | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap interface
ms.assetid: e6467529-508c-4328-85d7-89444ae4d1c1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fb1593f59125c4b6325bfd97015485cc2a4d85f6
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiaaddressmap"></a>IDiaAddressMap
Consente di controllare come il DIA SDK calcola virtuali e relativi indirizzi virtuali per gli oggetti di debug.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDiaAddressMap : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDiaAddressMap`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)|Indica se una mappa di indirizzo è stata definita per una determinata sessione.|  
|[IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)|Specifica se la mappa indirizzi deve essere utilizzata per convertire gli indirizzi di simbolo.|  
|[IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)|Indica se è abilitato il calcolo e l'utilizzo di indirizzi virtuali relativi.|  
|[IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)|Consente al client abilitare o disabilitare il calcolo di indirizzi virtuali relativi.|  
|[IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)|Recupera l'allineamento dell'immagine corrente.|  
|[IDiaAddressMap::put_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)|Imposta l'allineamento dell'immagine.|  
|[IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)|Set di intestazioni per abilitare la conversione di indirizzi virtuali relativi di immagine.|  
|[IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)|Fornisce un mapping di indirizzi per supportare le traduzioni di layout di immagine.|  
  
## <a name="remarks"></a>Note  
 Il controllo fornito da questa interfaccia è incapsulato in due set di dati è fornire: immagine intestazioni ed esegue il mapping di indirizzi. La maggior parte dei client utilizzano il [idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) metodo per trovare le informazioni di debug corretto per un'immagine e il metodo può in genere individuati tutti i dati di intestazioni e le mappe necessari se stesso. Tuttavia, alcuni client implementare specializzate, l'elaborazione e la ricerca di dati. Tali client utilizzano i metodi del `IDiaAddressMap` interfaccia per fornire il DIA SDK con i risultati della ricerca.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Questa interfaccia è disponibile dall'oggetto sessione DIA. Il client chiama il `QueryInterface` metodo DIA oggetto interfaccia della sessione, in genere [IDiaSession](../../debugger/debug-interface-access/idiasession.md)per recuperare il `IDiaAddressMap` interfaccia.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Dia2.h  
  
 Libreria: diaguids.lib  
  
 DLL: MSDIA80  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)