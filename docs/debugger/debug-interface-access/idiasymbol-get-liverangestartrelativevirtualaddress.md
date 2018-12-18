---
title: IDiaSymbol::get_liveRangeStartRelativeVirtualAddress | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_liveRangeStartRelativeVirtualAddress
ms.assetid: 1da52539-9872-4c20-8eaa-74b6cb5f3b02
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 94041c195d608b0641ab500dc8ab066adc87db36
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiasymbolgetliverangestartrelativevirtualaddress"></a>IDiaSymbol::get_liveRangeStartRelativeVirtualAddress
Restituisce l'inizio dell'intervallo di indirizzi in cui il simbolo locale è valido.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT get_liveRangeStartRelativeVirtualAddress (   
   DWORD* address  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `address`  
 [out] Restituisce l'inizio dell'intervallo di indirizzi.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore. L'indirizzo virtuale relativo restituito è l'inizio dell'intervallo in cui il simbolo è valido.  
  
> [!NOTE]
>  Un codice di errore restituito significa che il simbolo non dispone di informazioni di intervallo in tempo reale.  
  
## <a name="remarks"></a>Note  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Dia2.h  
  
 Libreria: diaguids.lib  
  
 DLL: msdia100.dll  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)