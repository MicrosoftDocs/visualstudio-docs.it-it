---
title: IDiaSymbol::get_addressTaken | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_addressTaken method
ms.assetid: 0d366188-f5e1-4226-b392-58c09539d097
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dc5fae2b172299c79b730f75320b9b7b05c3cf4f
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiasymbolgetaddresstaken"></a>IDiaSymbol::get_addressTaken
Recupera un flag che indica se un altro simbolo fa riferimento all'indirizzo di questo simbolo.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT get_addressTaken (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 [out] Restituisce `TRUE` se un altro simbolo fa riferimento a questo indirizzo; in caso contrario, restituisce `FALSE`.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.  
  
> [!NOTE]
>  Valore restituito di `S_FALSE` significa che la proprietà non è disponibile per il simbolo.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente, `B` riferimenti `A`. Pertanto, simbolo `A`del `get_addressTaken` restituisce `TRUE`.  
  
```C++  
int A  = 0;  
int* B = &A;  
```  
  
## <a name="requirements"></a>Requisiti  
  
|Requisito|Descrizione|  
|-----------------|-----------------|  
|Intestazione:|DIA2.h|  
|Versione:|Versione 7.0 DIA SDK|  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)