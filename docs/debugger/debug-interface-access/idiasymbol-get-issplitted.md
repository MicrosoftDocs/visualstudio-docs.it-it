---
title: IDiaSymbol::get_isSplitted | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isSplitted method
ms.assetid: ff160cf6-003b-4ef5-a406-20a7b287b2bf
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 15420c56dfa16f1bbb4566b1afe3fc7ac958fc07
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiasymbolgetissplitted"></a>IDiaSymbol::get_isSplitted
Recupera un flag che specifica se il simbolo di dati è stata suddivisa in un'aggregazione o una raccolta di altri simboli. il compilatore considera i simboli come entità distinte, anche se sono effettivamente parte di un simbolo di dimensioni maggiore.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT get_isSplitted(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pFlag`  
 [out] Restituisce `TRUE` se il simbolo è stata suddivisa in un'aggregazione di simboli; in caso contrario, restituisce `FALSE`.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o codice di errore.  
  
> [!NOTE]
>  Valore restituito di `S_FALSE` significa che la proprietà non è disponibile per il simbolo.  
  
## <a name="remarks"></a>Note  
 Il [IDiaSymbol::get_isAggregated](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md) restituisce `TRUE` per tutti i simboli che fanno parte di un simbolo di divisione.  
  
## <a name="requirements"></a>Requisiti  
  
|Requisito|Descrizione|  
|-----------------|-----------------|  
|Intestazione:|DIA2.h|  
|Versione:|Versione 8.0 DIA SDK|  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get_isAggregated](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md)