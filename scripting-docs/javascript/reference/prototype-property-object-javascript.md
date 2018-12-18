---
title: "Proprietà prototype (Object) (JavaScript) | Documenti Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Prototype
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- inheritance, objects
- Prototype property
ms.assetid: 9fc434a1-5995-4fcb-a4e8-00e7f615aaa2
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a73d213b6b17f5046eb1f4c498aeb223f942f2d8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-object-javascript"></a>Proprietà prototype (Object) (JavaScript)
Restituisce un riferimento al prototipo per una classe di oggetti.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
objectName.prototype  
```  
  
## <a name="remarks"></a>Note  
 L'argomento `objectName` è il nome di un oggetto.  
  
 Usare la proprietà `prototype` per fornire un set di funzionalità di base a una classe di oggetti. Le nuove istanze di un oggetto "ereditano" il comportamento del prototipo assegnato all'oggetto.  
  
 Per aggiungere, ad esempio, un metodo all'oggetto `Array` che restituisce il valore dell'elemento più grande della matrice, dichiarare la funzione, aggiungerla a `Array.prototype` e quindi usarla.  
  
```JavaScript  
function array_max( ){  
    var i, max = this[0];  
    for (i = 1; i < this.length; i++)  
    {  
    if (max < this[i])  
    max = this[i];  
    }  
    return max;  
}  
Array.prototype.max = array_max;  
var myArray = new Array(7, 1, 3, 11, 25, 9  
);  
document.write(myArray.max());  
  
// Output:  
// 25  
  
```  
  
 Tutti gli intrinseci [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] gli oggetti hanno una `prototype` proprietà che è di sola lettura. È possibile aggiungere proprietà e metodi al prototipo, ma l'oggetto non può essere assegnato un prototipo diverso. Tuttavia, gli oggetti definiti dall'utente possono essere assegnati un nuovo prototipo.  
  
 Gli elenchi di metodo e proprietà per ogni oggetto intrinseco in questa Guida di riferimento indicano quali fanno parte del prototipo dell'oggetto e non.  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà constructor (Object)](../../javascript/reference/constructor-property-object-javascript.md)