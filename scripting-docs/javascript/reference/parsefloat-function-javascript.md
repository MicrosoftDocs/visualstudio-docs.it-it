---
title: Funzione parseFloat (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: parseFloat
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: parseFloat method
ms.assetid: a7d87a69-1919-4623-be85-972e6376dd2d
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eb8f6d179abba887542e59d083141534732ed42a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="parsefloat-function-javascript"></a>Funzione parseFloat (JavaScript)
Converte una stringa in un numero a virgola mobile.  
  
## <a name="syntax"></a>Sintassi  
  
```  
parseFloat(numString)   
```  
  
## <a name="remarks"></a>Note  
 Obbligatorio `numString` argomento è una stringa che contiene un numero a virgola mobile.  
  
 Il `parseFloat` funzione restituisce un valore numerico uguale al numero contenuto `numString`. Se nessun prefisso di `numString` può essere analizzato correttamente in un numero a virgola mobile, `NaN` viene restituito (not a number).  
  
```JavaScript  
parseFloat("abc")      // Returns NaN.  
parseFloat("1.2abc")   // Returns 1.2.  
```  
  
 È possibile testare `NaN` utilizzando il `isNaN` (funzione).  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Si applica a**: [oggetto globale](../../javascript/reference/global-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione isNaN](../../javascript/reference/isnan-function-javascript.md)   
 [Funzione parseInt](../../javascript/reference/parseint-function-javascript.md)   
 [Oggetto String](../../javascript/reference/string-object-javascript.md)