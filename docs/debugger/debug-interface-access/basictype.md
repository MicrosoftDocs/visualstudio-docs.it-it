---
title: BasicType | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: BasicType enumeration
ms.assetid: 19ae53ba-cd6e-47b6-9f94-27ae663ce955
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 302e935c1b9f772735612e731503f84ccc3e468f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="basictype"></a>BasicType
Specifica tipo di base del simbolo.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
enum BasicType {   
   btNoType   = 0,  
   btVoid     = 1,  
   btChar     = 2,  
   btWChar    = 3,  
   btInt      = 6,  
   btUInt     = 7,  
   btFloat    = 8,  
   btBCD      = 9,  
   btBool     = 10,  
   btLong     = 13,  
   btULong    = 14,  
   btCurrency = 25,  
   btDate     = 26,  
   btVariant  = 27,  
   btComplex  = 28,  
   btBit      = 29,  
   btBSTR     = 30,  
   btHresult  = 31  
};  
```  
  
## <a name="elements"></a>Elementi  
 btNoType  
 Viene specificato alcun tipo di base.  
  
 btVoid  
 Tipo di base è un `void`.  
  
 btChar  
 Tipo di base è un `char` (tipo di C/C++).  
  
 btWChar  
 Tipo di base sono un carattere (Unicode) wide (`WCHAR`).  
  
 btInt  
 Tipo di base è `signed int` (tipo di C/C++).  
  
 btUInt  
 Tipo di base è `unsigned int` (tipo di C/C++).  
  
 btFloat  
 Tipo di base sono un numero a virgola mobile (`FLOAT`).  
  
 btBCD  
 Tipo di base sono un numero decimale a livello di codice binario (`BCD`).  
  
 btBool  
 Tipo di base sono un valore booleano (`BOOL`).  
  
 btLong  
 Tipo di base è un `long int` (tipo di C/C++).  
  
 btULong  
 Tipo di base è un `unsigned long int` (tipo di C/C++).  
  
 btCurrency  
 Tipo di base sono di tipo valuta.  
  
 btDate  
 Tipo di base sono data/ora (`DATE`).  
  
 btVariant  
 Tipo di base sono una struttura di tipo di variabile (`VARIANT`).  
  
 btComplex  
 Tipo di base sono un numero complesso.  
  
 btBit  
 Tipo di base è un po'.  
  
 btBSTR  
 Tipo di base sono una stringa di base o binary (`BSTR`).  
  
 btHresult  
 Tipo di base è un `HRESULT`.  
  
## <a name="remarks"></a>Note  
 I valori di questa enumerazione sono restituiti dal [idiasymbol:: Get_basetype](../../debugger/debug-interface-access/idiasymbol-get-basetype.md) metodo.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: cvconst.h  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Idiasymbol:: Get_basetype](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)   
 [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)