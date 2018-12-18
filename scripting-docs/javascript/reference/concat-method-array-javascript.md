---
title: Metodo concat (Array) (JavaScript) | Documenti Microsoft
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
- concat
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- concat method (array)
- Concat method
ms.assetid: bc2b4a6a-209e-4d59-8c24-59db01d53b1e
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 19f3a216a36f9ad8c422036476e46b89b6ee488c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="concat-method-array-javascript"></a>Metodo concat (Array) (JavaScript)
Consente di combinare due o più matrici.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
array1.concat([item1[, item2[, . . . [, itemN]]]])   
```  
  
## <a name="parameters"></a>Parametri  
 `array1`  
 Obbligatorio. Il `Array` l'oggetto in cui vengono concatenati altre matrici.  
  
 `item1,. . ., itemN`  
 Parametro facoltativo. Altri elementi da aggiungere alla fine di `array1`.  
  
## <a name="remarks"></a>Note  
 Il `concat` metodo restituisce un `Array` oggetto contenente la concatenazione di `array1` e degli altri elementi specificati.  
  
 Gli elementi da aggiungere (*item1 itemN*) nella matrice vengono aggiunti, a partire dal primo elemento nell'elenco. Se uno degli elementi è una matrice, il relativo contenuto viene aggiunti alla fine di `array1`. Se l'elemento è diverso da una matrice, viene aggiunto alla fine della matrice come un singolo elemento di matrice.  
  
 Gli elementi delle matrici di origine vengono copiati nella matrice risultante come indicato di seguito:  
  
-   Se un oggetto viene copiato da qualsiasi delle matrici di essere concatenate a una nuova matrice, il riferimento all'oggetto continua a puntare allo stesso oggetto. Una modifica nella nuova matrice o matrice originale comporterà una modifica a altro.  
  
-   Se nella nuova matrice viene aggiunto un valore di numero o stringa, viene copiato solo il valore. La modifica del valore in una matrice non influirà sul valore a altro.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come utilizzare il `concat` metodo con una matrice:  
  
```JavaScript  
var a, b, c, d;  
a = new Array(1,2,3);  
b = "dog";  
c = new Array(42, "cat");  
d = a.concat(b, c);  
document.write(d);  
  
//Output:   
1, 2, 3, "dog", 42, "cat"  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo concat (String)](../../javascript/reference/concat-method-string-javascript.md)   
 [Metodo join (Array)](../../javascript/reference/join-method-array-javascript.md)