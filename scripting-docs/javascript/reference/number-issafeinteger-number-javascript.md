---
title: Funzione Number. issafeinteger (Number) (JavaScript) | Documenti Microsoft
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
ms.assetid: c7ef6ce8-fe71-4e53-be44-4dd440aef21d
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eebc2147bc5043341be7e883548af825922036f9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="numberissafeinteger-number-javascript"></a>Number.isSafeInteger (Number) (JavaScript)
Restituisce un valore booleano che indica se un numero può essere rappresentato senza problemi in JavaScript.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Number.isSafeInteger(numValue)   
```  
  
## <a name="return-value"></a>Valore restituito  
 `true` se il numero è compreso tra `Number.MIN_SAFE_INTEGER` e `Number.MAX_SAFE_INTEGER`, inclusi; in caso contrario `false`.  
  
## <a name="remarks"></a>Note  
 Un valore integer sicuro in JavaScript è un numero con precisione doppia IEEE-754 prima dell'applicazione di qualsiasi arrotondamento.  
  
## <a name="example"></a>Esempio  
  
```JavaScript  
// Returns true  
Number.isSafeInteger(-100)  
Number.isSafeInteger(9007199254740991)  
  
// Returns false  
Number.isSafeInteger(Number.NaN)  
Number.isSafeInteger(Infinity)  
Number.isSafeInteger("100")  
Number.isSafeInteger(9007199254740992);  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **Si applica a**: [numero oggetto](../../javascript/reference/number-object-javascript.md)