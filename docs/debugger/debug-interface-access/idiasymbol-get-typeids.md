---
title: IDiaSymbol::get_typeIds | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_typeIds method
ms.assetid: 5166e647-fde5-4efe-92bf-77f8ae3fbc9b
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b186c9f2f8b3ad49808669c1fd04b1fdefe3b82d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idiasymbolgettypeids"></a>IDiaSymbol::get_typeIds
Recupera una matrice di valori di identificatore di tipo specifici del compilatore per questo simbolo.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT get_typeIds (   
   DWORD  cTypeIds,  
   DWORD* pcTypeIds,  
   DWORD  typeIds[]  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `cTypeIds`  
 [in] Dimensione del buffer per contenere i dati.  
  
 `pcTypeIds`  
 [out] Restituisce il numero di `typeIds` scritto, in alternativa, se `typeIds` è `NULL`, quindi il numero totale di identificatori di tipo disponibili.  
  
 `typeIds[]`  
 [out] Matrice che deve essere compilato con gli identificatori di tipo.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.  
  
> [!NOTE]
>  Valore restituito di `S_FALSE` significa che la proprietà non è disponibile per il simbolo.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)