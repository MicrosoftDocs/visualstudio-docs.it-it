---
title: Funzione String. fromCharCode (JavaScript) | Documenti Microsoft
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
- fromCharCode
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- fromCharCodeAt method
- characters, from Unicode
ms.assetid: f64120c1-23a7-48ca-8d1c-db3e8856cab4
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dbcd9062d7da0b73647c1d9eb6cc207af23c3532
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="stringfromcharcode-function-javascript"></a>Funzione String.fromCharCode (JavaScript)
Restituisce una stringa a partire da un numero di valori dei caratteri Unicode.  
  
## <a name="syntax"></a>Sintassi  
  
```  
String.fromCharCode([code1[, code2[, ...[, codeN]]]])   
```  
  
## <a name="parameters"></a>Parametri  
 `String`  
 Obbligatorio. Oggetto `String`.  
  
 `code1`, . . . , `codeN`  
 Parametro facoltativo. Una serie di valori di tipo carattere Unicode da convertire in una stringa. Se non vengono forniti argomenti, il risultato è una stringa vuota.  
  
## <a name="remarks"></a>Note  
 Chiamare questa funzione nel `String` oggetto anziché in un'istanza di stringa.  
  
 Nell'esempio seguente viene illustrato come utilizzare questo metodo:  
  
```JavaScript  
var test = String.fromCharCode(112, 108, 97, 105, 110);  
document.write(test);  
  
// Output: plain  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo charCodeAt (String)](../../javascript/reference/charcodeat-method-string-javascript.md)