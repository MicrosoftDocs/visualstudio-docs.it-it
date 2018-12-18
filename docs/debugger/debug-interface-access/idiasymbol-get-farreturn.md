---
title: IDiaSymbol::get_farReturn | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_farReturn method
ms.assetid: 141df0e9-f4d9-4330-a043-5d9ea865257f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3efe5a7bef592ef441d30116ed91e61f8f14fd16
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiasymbolgetfarreturn"></a>IDiaSymbol::get_farReturn
Recupera un flag che specifica se la funzione contiene una misura restituito.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT get_farReturn(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pFlag`  
 [in] Restituisce `TRUE` se la funzione utilizza una misura restituito, in caso contrario, restituisce `FALSE`.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.  
  
> [!NOTE]
>  Valore restituito di `S_FALSE` significa che la proprietà non è disponibile per il simbolo.  
  
## <a name="requirements"></a>Requisiti  
  
|Requisito|Descrizione|  
|-----------------|-----------------|  
|Intestazione:|DIA2.h|  
|Versione:|Versione 8.0 DIA SDK|  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)