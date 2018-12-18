---
title: Percorsi dei simboli | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- LocationType values
- symbols [DIA SDK], locations
ms.assetid: 7c8cd8fe-169e-4161-9cff-5e9015984add
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 021911c01a7cd98e157f6c216ae28feffcaf7096
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="symbol-locations"></a>Percorsi dei simboli
La maggior parte dei simboli dispongono di un percorso definito all'interno del file di immagine. Percorso di un simbolo viene specificato con un valore di [LocationType (enumerazione)](../../debugger/debug-interface-access/locationtype.md) enumerazione. Il simbolo può supportare proprietà aggiuntive in base al relativo percorso.  
  
 La tabella seguente illustra più comunemente utilizzati tipi di percorsi e le relative proprietà aggiuntive.  
  
|Tipo di posizione|Proprietà aggiuntive|  
|-------------------|---------------------------|  
|`LocIsNull`|none|  
|`LocIsStatic`|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)<br /><br /> [IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)<br /><br /> [Get_relativevirtualaddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md) (se sono abilitati gli indirizzi virtuali relativi)<br /><br /> [Get_virtualaddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md) (se la base dell'immagine è stata impostata a diverso da zero)|  
|`LocIsTLS`|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)<br /><br /> [IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|  
|`LocIsRegRel`|[IDiaSymbol::get_registerId](../../debugger/debug-interface-access/idiasymbol-get-registerid.md)<br /><br /> [IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|  
|`LocIsThisRel`|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|  
|`LocIsEnregistered`|[IDiaSymbol::get_registerId](../../debugger/debug-interface-access/idiasymbol-get-registerid.md)|  
|`LocIsBitField`|[IDiaSymbol::get_bitPosition](../../debugger/debug-interface-access/idiasymbol-get-bitposition.md)<br /><br /> [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)<br /><br /> [IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|  
|`LocIsSlot`|[IDiaSymbol::get_slot](../../debugger/debug-interface-access/idiasymbol-get-slot.md)|  
|`LocIsIlRel`|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|  
|`LocInMetaData`|[IDiaSymbol::get_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)|  
|`LocIsConstant`|[IDiaSymbol::get_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Get_addressoffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)   
 [Get_addresssection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)   
 [Get_bitposition](../../debugger/debug-interface-access/idiasymbol-get-bitposition.md)   
 [Get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)   
 [Get_locationtype](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)   
 [Get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)   
 [Get_registerid](../../debugger/debug-interface-access/idiasymbol-get-registerid.md)   
 [Get_relativevirtualaddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)   
 [Get_slot](../../debugger/debug-interface-access/idiasymbol-get-slot.md)   
 [Get_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)   
 [Get_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)   
 [Get_virtualaddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)   
 [LocationType (enumerazione)](../../debugger/debug-interface-access/locationtype.md)   
 [Simboli e relativi tag](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)