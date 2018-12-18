---
title: CV_call_e | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CV_call_e enumeration
ms.assetid: f230560b-4243-432d-8f19-46df112043b9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ccdc9df86180883a5a3891563b22625fab4a2ad2
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="cvcalle"></a>CV_call_e
Specifica la convenzione di chiamata per una funzione.  
  
> [!NOTE]
>  Solo i valori di enumerazione più comuni sono documentati di seguito. L'enumerazione completo è disponibile nel file di intestazione cvconst.h.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
typedef enum CV_call_e {   
   CV_CALL_NEAR_C    = 0x00,  
   CV_CALL_NEAR_FAST = 0x04,  
   CV_CALL_NEAR_STD  = 0x07,  
   CV_CALL_NEAR_SYS  = 0x09,  
   CV_CALL_THISCALL  = 0x0b,  
   CV_CALL_CLRCALL   = 0x16  
} CV_call_e;  
```  
  
## <a name="elements"></a>Elementi  
 CV_CALL_NEAR_C  
 Specifica una convenzione di chiamata di funzione utilizzando un vicino push da destra a sinistra. La funzione chiamata pulisce lo stack.  
  
 CV_CALL_NEAR_FAST  
 Specifica una convenzione di chiamata di funzione con un push da sinistra a destra vicino registri. La funzione chiamata Usa la somma di byte di parametri per cancellare lo stack.  
  
 CV_CALL_NEAR_STD  
 Specifica una convenzione di chiamata di funzioni tramite una chiamata standard quasi (push da destra a sinistra).  
  
 CV_CALL_NEAR_SYS  
 Specifica una convenzione di chiamata di funzioni tramite una chiamata di sistema vicino.  
  
 CV_CALL_THISCALL  
 Specifica una convenzione di chiamata di funzione utilizzando `this` chiamare (`this` puntatore passato nel registro).  
  
 CV_CALL_CLRCALL  
 Specifica una convenzione di chiamata di funzione utilizzata per il Common Language Runtime (CLR) (noto anche come un codice gestito la convenzione di chiamata).  
  
## <a name="remarks"></a>Note  
 I valori di questa enumerazione vengono restituiti da una chiamata al [IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md) metodo.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: cvconst.h  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)