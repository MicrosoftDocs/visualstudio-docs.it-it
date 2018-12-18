---
title: IDiaSymbol::get_rank | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_rank method
ms.assetid: 14cc9c4b-a5ec-414a-b01f-4a142c17b7cc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9b78ba89b56c6d8c473060e39d402ee46e4ae15f
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiasymbolgetrank"></a>IDiaSymbol::get_rank
Recupera il rango (numero di dimensioni) di una matrice multidimensionale di FORTRAN.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT get_rank (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 [out] Restituisce il numero di dimensioni in una matrice multidimensionale di FORTRAN.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.  
  
> [!NOTE]
>  Valore restituito di `S_FALSE` significa che la proprietà non è disponibile per il simbolo.  
  
## <a name="remarks"></a>Note  
 Numero di dimensioni si riferisce al numero di dimensioni in una matrice in cui è dichiarata come `myarray[1,2,3]`. L'esempio include una classificazione di dimensioni 3 e 3. Numero di dimensioni non si applica a C++ che utilizza il concetto di una matrice di matrici per ogni dimensione (vale a dire `myarray[1][2][3]`).  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)