---
title: IDiaSymbol::get_isAcceleratorPointerTagLiveRange | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: d195aec4-6d3c-42e0-88a5-3d463539f0b8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 91fc97cafdb3037bb3cca4c93ee874ee329d794c
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiasymbolgetisacceleratorpointertagliverange"></a>IDiaSymbol::get_isAcceleratorPointerTagLiveRange
Recupera un flag che indica se il simbolo corrisponde alla *simbolo intervallo definizione* per il componente di tag di una variabile puntatore nel codice compilato per un tasto di scelta rapida di C++ AMP. Il simbolo di intervallo di definizione è il percorso di una variabile per un intervallo di indirizzi.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT get_isAcceleratorPointerTagLiveRange(   
   BOOL* pFlag);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pFlag`  
 [out] Un puntatore a un `BOOL` che indica se il simbolo corrisponde al simbolo di intervallo di definizione.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)