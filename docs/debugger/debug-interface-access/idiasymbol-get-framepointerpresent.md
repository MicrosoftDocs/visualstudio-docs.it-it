---
title: IDiaSymbol::get_framePointerPresent | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_framePointerPresent method
ms.assetid: d036090a-1651-454d-9130-b798f58ba053
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 28c3201cc8580159fcf30ea364adb8a4f1837a37
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idiasymbolgetframepointerpresent"></a>IDiaSymbol::get_framePointerPresent
Recupera un flag che specifica se è presente il puntatore ai frame. Utilizzo di [SymTagEnum (enumerazione)](../../debugger/debug-interface-access/symtagenum.md) è impostato su `SymTagFunction`.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT get_framePointerPresent(   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 [out]] Restituisce `TRUE` se il puntatore ai frame è presente; in caso contrario, restituisce `FALSE`.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.  
  
> [!NOTE]
>  Valore restituito di `S_FALSE` significa che la proprietà non è disponibile per il simbolo.  
  
## <a name="remarks"></a>Note  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Dia2.h  
  
 Libreria: diaguids.lib  
  
 DLL: msdia100.dll  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)