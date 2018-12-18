---
title: Metodo slice (String) (JavaScript) | Documenti Microsoft
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
- slice
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- strings [Visual Studio], returning characters
- slice method
ms.assetid: 80cd77a6-3718-492e-8e96-f909d8721d91
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1baa0a05a2d6aa8c06cc962761c8e557632d034c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="slice-method-string-javascript"></a>Metodo slice (String) (JavaScript)
Restituisce una sezione di una stringa.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
stringObj.slice(start, [end])   
```  
  
## <a name="parameters"></a>Parametri  
 `stringObj`  
 Obbligatorio. Oggetto `String` o valore letterale stringa.  
  
 `start`  
 Obbligatorio. L'indice dell'inizio della parte specificata di `stringObj`.  
  
 `end`  
 Parametro facoltativo. L'indice alla fine della parte specificata di `stringObj`. La sottostringa include i caratteri fino a, ma non è incluso, il carattere indicato da `end`. Se questo valore viene omesso, la sottostringa continua fino alla fine di `stringObj`.  
  
## <a name="remarks"></a>Note  
 Il `slice` metodo restituisce un `String` contenente la parte specificata dell'oggetto `stringObj`.  
  
 Il `slice` metodo copia fino al punto, ma non include il carattere indicato da `end`.  
  
 Se `start` è negativo, viene considerato come *lunghezza*  +  `start` in *lunghezza* è la lunghezza della stringa. Se `end` è negativo, viene considerato come *lunghezza* + `end`. Se `end` viene omesso, la copia continua fino alla fine di `stringObj`. Se `end` si verifica prima `start`, non caratteri vengono copiati nella nuova stringa.  
  
## <a name="example"></a>Esempio  
 Nel primo esempio, il `slice` metodo restituisce l'intera stringa. Nel secondo esempio, il `slice` metodo restituisce l'intera stringa, tranne l'ultimo carattere.  
  
```JavaScript  
var str1 = "all good boys do fine";  
  
var slice1 = str1.slice(0);  
var slice2 = str1.slice(0,-1);  
var slice3 = str1.slice(4);  
var slice4 = str1.slice(4, 8);  
  
document.write(slice1 + "<br/>");  
document.write(slice2 + "<br/>");  
document.write(slice3 + "<br/>");  
document.write(slice4);  
  
// Output:  
// all good boys do fine  
// all good boys do fin  
// good boys do fine  
// good  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Si applica a**: [oggetto stringa](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo slice (Array)](../../javascript/reference/slice-method-array-javascript.md)