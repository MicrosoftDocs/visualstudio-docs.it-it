---
title: Funzione parseInt (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- parseInt
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- parseInt method
ms.assetid: e86471af-2a0e-4359-83af-f1ac81e51421
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 54ee77470d32410ae46a628d54fc3bda97fecc51
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="parseint-function-javascript"></a>Funzione parseInt (JavaScript)
Converte una stringa in un intero.  
  
## <a name="syntax"></a>Sintassi  
  
```  
parseInt(numString, [radix])   
```  
  
## <a name="parameters"></a>Parametri  
 `numString`  
 Obbligatorio. Stringa da convertire in un numero.  
  
 `radix`  
 Parametro facoltativo. Un valore compreso tra 2 e 36 che specifica la base del numero in `numString`. Se questo argomento viene omesso, le stringhe con il prefisso "0x" sono considerate esadecimale. Tutte le altre stringhe vengono considerati come decimale.  
  
## <a name="remarks"></a>Note  
 Il `parseInt` funzione restituisce un valore intero uguale al numero contenuto `numString`. Se nessun prefisso di `numString` può essere analizzato correttamente in un numero intero, `NaN` viene restituito (not a number).  
  
```JavaScript  
parseInt("abc");     // Returns NaN.  
parseInt("12abc");   // Returns 12.  
```  
  
 È possibile testare `NaN` utilizzando il `isNaN` (funzione).  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Si applica a**: [oggetto globale](../../javascript/reference/global-object-javascript.md)  
  
> [!NOTE]
>  A partire da [!INCLUDE[jsv9textspecific](../../javascript/reference/includes/jsv9textspecific-md.md)], `parseInt` funzione non considera una stringa che contiene un prefisso '0' come un ottale. Quando non si utilizza il `parseInt` funzionare, tuttavia, le stringhe con il prefisso '0' possono essere interpretate ancora come octals. Vedere [tipi di dati](../../javascript/data-types-javascript.md) per informazioni su valori Integer ottale.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione isNaN](../../javascript/reference/isnan-function-javascript.md)   
 [Funzione parseFloat](../../javascript/reference/parsefloat-function-javascript.md)   
 [Oggetto String](../../javascript/reference/string-object-javascript.md)   
 [Metodo valueOf (Object)](../../javascript/reference/valueof-method-object-javascript.md)