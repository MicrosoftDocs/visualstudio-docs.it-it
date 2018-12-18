---
title: 'Idiasymbol:: Get_addresssection | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_addressSection method
ms.assetid: fe80d479-3bb5-4f55-9b62-1bd58d0a60ce
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f5b4ed00e11cc994006ee91fd315e33fadbe6bd3
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiasymbolgetaddresssection"></a>IDiaSymbol::get_addressSection
Recupera la parte della sezione di un percorso di indirizzo. Utilizzo di [LocationType (enumerazione)](../../debugger/debug-interface-access/locationtype.md) è impostato su `LocIsStatic`.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT get_addressSection (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 [out] Restituisce la parte della sezione di un percorso di indirizzo.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.  
  
> [!NOTE]
>  Valore restituito di `S_FALSE` significa che la proprietà non è disponibile per il simbolo.  
  
## <a name="remarks"></a>Note  
 Per i membri statici che si trova in una DLL esterna, la sezione restituita da questo metodo può essere 0, questo metodo si basa su come ottenere l'indirizzo virtuale del membro. Gli indirizzi virtuali sono validi solo se il [idiasession:: Put_loadaddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) metodo il [IDiaSession](../../debugger/debug-interface-access/idiasession.md) interfaccia è stata chiamata con un parametro diverso da zero che specifica l'indirizzo di caricamento della DLL.  
  
 Per ottenere la parte offset di un indirizzo, chiamare il [idiasymbol:: Get_addressoffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md) metodo.  
  
## <a name="requirements"></a>Requisiti  
  
|Requisito|Descrizione|  
|-----------------|-----------------|  
|Intestazione:|DIA2.h|  
|Versione:|Versione 7.0 DIA SDK|  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [LocationType (enumerazione)](../../debugger/debug-interface-access/locationtype.md)