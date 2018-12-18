---
title: IDiaSymbol::get_baseSymbol | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: cabb5a18-bda7-47e8-9e46-5f4718579fc9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 81cf7e2c924aac3be16774b98bb85eb220256113
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiasymbolgetbasesymbol"></a>IDiaSymbol::get_baseSymbol
Recupera il simbolo da cui è basato il puntatore del mouse.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT get_baseSymbol(   
   IDiaSymbol** pRetVal);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 [out] Un puntatore per il simbolo da cui è basato il puntatore del mouse.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get_baseSymbolId](../../debugger/debug-interface-access/idiasymbol-get-basesymbolid.md)