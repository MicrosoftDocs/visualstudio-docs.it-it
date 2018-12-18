---
title: IDiaSymbol::get_callingConvention | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_callingConvention method
ms.assetid: 355d3877-b6b6-45fd-a1d8-baed428d8f96
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f32f8678eadd23fff8b0bb65d6131d70815c34aa
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiasymbolgetcallingconvention"></a>IDiaSymbol::get_callingConvention
Restituisce un indicatore di una convenzione di chiamata di metodi.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT get_callingConvention (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 [out] Restituisce un valore di [CV_call_e (enumerazione)](../../debugger/debug-interface-access/cv-call-e.md) convenzione di chiamata dell'enumerazione che specifica un metodo.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.  
  
> [!NOTE]
>  Valore restituito di `S_FALSE` significa che la proprietà non è disponibile per il simbolo.  
  
## <a name="requirements"></a>Requisiti  
  
|Requisito|Descrizione|  
|-----------------|-----------------|  
|Intestazione:|DIA2.h|  
|Versione:|Versione 7.0 DIA SDK|  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [CV_call_e (enumerazione)](../../debugger/debug-interface-access/cv-call-e.md)