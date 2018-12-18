---
title: Funzione Number. IsNaN (Number) (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 2d9813d6-ec9c-433b-b060-8e3c3ff62ca4
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7c11abe2dd2fc70431800d31f4c44279a88cd75d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="numberisnan-function-number-javascript"></a>Funzione Number.isNaN (Number) (JavaScript)
Restituisce un valore booleano che indica se un valore è il valore riservato `NaN` (non un numero).  
  
## <a name="syntax"></a>Sintassi  
  
```  
Number.isNaN(numValue)   
```  
  
#### <a name="parameters"></a>Parametri  
 `numValue`  
 Obbligatorio. Valore da testare rispetto a `NaN`.  
  
## <a name="return-value"></a>Valore restituito  
 `true` se il valore convertito nel tipo `Number` è `NaN` in caso contrario, `false`.  
  
## <a name="remarks"></a>Note  
 In genere, si usa questo metodo per testare i valori restituiti dai metodi `parseInt` e `parseFloat`.  
  
 `Number.isNaN` corregge i problemi della funzione globale `isNaN`. `Number.isNaN` converte solo il relativo argomento nel tipo Number dopo averlo confrontato con `NaN`. Di conseguenza, restituisce `true` solo se l'argomento passato ha esattamente lo stesso valore di `NaN`. La funzione globale `isNaN` converte il relativo argomento nel tipo Number prima del confronto. Ciò può comportare la restituzione di `true` da parte di valori non numerici, mentre non potrebbero restituire `true` per `Number.isNaN`.  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **Si applica a**: [numero oggetto](../../javascript/reference/number-object-javascript.md)  
  
## <a name="example"></a>Esempio  
  
```JavaScript  
// Returns true.  
Number.isNaN(NaN);  
Number.isNaN(Number.NaN);  
Number.isNaN(0 / 0);  
  
// Returns false.  
Number.isNaN(100);  
// Returns false.  
// Strings are converted to numbers and return false.  
Number.isNaN("100");  
Number.isNaN("ABC");  
Number.isNaN("10C");  
Number.isNaN("abc123");  
  
```