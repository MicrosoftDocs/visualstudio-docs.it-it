---
title: Metodo pop (Array) (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: pop
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: Pop method
ms.assetid: 4fae7f98-29f1-4041-ba43-601f2e5145ec
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f7635ddcc1b3d336f5e3de66e62714bd93a06158
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="pop-method-array-javascript"></a>Metodo pop (Array) (JavaScript)
Rimuove l'ultimo elemento di una matrice e lo restituisce.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
arrayObj.pop( )  
```  
  
## <a name="remarks"></a>Note  
 Il [push](../../javascript/reference/push-method-array-javascript.md) e `pop` metodi consentono di simulare uno stack in cui viene utilizzato il principio Last in, first out (LIFO) per archiviare i dati.  
  
 Obbligatorio `arrayObj` riferimento è un `Array` oggetto.  
  
 Se la matrice è vuota, `undefined` viene restituito.  
  
## <a name="example"></a>Esempio  
 Nell'esempio riportato di seguito viene illustrato l'utilizzo del metodo `pop`.  
  
```JavaScript  
var number;  
var my_array = new Array();  
  
my_array.push (5, 6, 7);  
my_array.push (8, 9);  
  
number = my_array.pop();  
while (number != undefined)  
   {  
   document.write (number + " ");  
   number = my_array.pop();  
   }  
  
// Output: 9 8 7 6 5  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo push (Array)](../../javascript/reference/push-method-array-javascript.md)