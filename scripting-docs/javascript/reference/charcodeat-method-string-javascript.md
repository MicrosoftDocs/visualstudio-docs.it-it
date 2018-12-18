---
title: Metodo charCodeAt (String) (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: charCodeAt
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: charCodeAt method
ms.assetid: 5b0290a7-ee4d-4738-a909-c02ef64a2f1a
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8e7b8e62dfd29aa42d9816d0c5e27cc90440751a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="charcodeat-method-string-javascript"></a>Metodo charCodeAt (String) (JavaScript)
Restituisce il valore Unicode del carattere nella posizione specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
strObj. charCodeAt(index)  
```  
  
## <a name="parameters"></a>Parametri  
 `strObj`  
 Obbligatorio. Qualsiasi `String` o valore letterale stringa.  
  
 `index`  
 Obbligatorio. Indice in base zero del carattere desiderato. Se non è presente alcun carattere in corrispondenza dell'indice specificato, `NaN` viene restituito.  
  
## <a name="remarks"></a>Note  
  
## <a name="example"></a>Esempio  
 Nell'esempio riportato di seguito viene illustrato l'utilizzo del metodo `charCodeAt`.  
  
```JavaScript  
var str = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";   
document.write(str.charCodeAt(str.length - 1));  
  
// Output: 90   
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione String.fromCharCode](../../javascript/reference/string-fromcharcode-function-javascript.md)