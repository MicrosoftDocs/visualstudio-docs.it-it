---
title: "Proprietà prototype (Array) | Documenti Microsoft"
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
ms.assetid: 5fedf632-8316-4e5d-ab20-10e41aa4d9f8
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4fd5102fe2f49218de76c498a11256a6ef24ff0f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-array"></a>Proprietà prototype (Array)
Restituisce un riferimento al prototipo per una classe della matrice.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
array.prototype  
```  
  
## <a name="remarks"></a>Note  
 Il `array` argomento è il nome di una matrice.  
  
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
  
// Output: 25  
```  
  
 Tutti gli intrinseci [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] gli oggetti hanno una `prototype` proprietà che è di sola lettura. È possibile aggiungere proprietà e metodi al prototipo, ma l'oggetto non può essere assegnato un prototipo diverso. Tuttavia, gli oggetti definiti dall'utente possono essere assegnati un nuovo prototipo.  
  
 Gli elenchi di metodo e proprietà per ogni oggetto intrinseco in questa Guida di riferimento indicano quali fanno parte del prototipo dell'oggetto e non.  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]