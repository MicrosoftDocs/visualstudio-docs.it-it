---
title: Metodo push (Array) (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: push
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: Push method
ms.assetid: fa6e5799-dabe-4b3d-bd1f-0afc68c77134
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ddb49f310eaff51fe9e9ba584281fdf07bc2e818
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="push-method-array-javascript"></a>Metodo push (Array) (JavaScript)
Aggiunge nuovi elementi a una matrice e restituisce la nuova lunghezza della matrice.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
arrayObj.push([item1 [item2 [. . . [itemN ]]]])  
```  
  
## <a name="parameters"></a>Parametri  
 `arrayObj`  
 Obbligatorio. Oggetto `Array`.  
  
 `item, item2,. . ., itemN`  
 Parametro facoltativo. Nuovi elementi del `Array`.  
  
## <a name="remarks"></a>Note  
 Il `push` e `pop` metodi consentono di simulare una last-in, innanzitutto out dello stack.  
  
 Il `push` metodo aggiunge gli elementi nell'ordine in cui appaiono. Se uno degli argomenti è una matrice, viene aggiunto come un singolo elemento. Utilizzare il `concat` metodo per unire gli elementi di due o più matrici.  
  
## <a name="example"></a>Esempio  
 Nell'esempio riportato di seguito viene illustrato l'utilizzo del metodo `push`.  
  
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
  
// Output:  
// 9 8 7 6 5  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo concat (Array)](../../javascript/reference/concat-method-array-javascript.md)   
 [Metodo pop (Array)](../../javascript/reference/pop-method-array-javascript.md)