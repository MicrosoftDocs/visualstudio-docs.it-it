---
title: "Proprietà prototype (Date) | Documenti Microsoft"
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
ms.assetid: 44f9c637-7da7-4833-906d-358506f32ced
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8c0b337964d2a2fe17a4e9a7906d81069470e61b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-date"></a>Proprietà prototype (Date)
Restituisce un riferimento al prototipo per una data.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
date.prototype  
```  
  
## <a name="remarks"></a>Note  
 L'argomento `date` è il nome di un oggetto.  
  
 Utilizzare il `prototype` proprietà per fornire un set di funzionalità di base a una data. Le nuove istanze di un oggetto "ereditano" il comportamento del prototipo assegnato all'oggetto.  
  
 Per aggiungere, ad esempio, un metodo all'oggetto `Date` che restituisce il valore dell'elemento più grande della matrice, dichiarare la funzione, aggiungerla a `Date.prototype` e quindi usarla.  
  
```JavaScript  
function max( ){  
    var max = new Date();  
    max.setFullYear(2200, 01, 01);  
    return max;  
}  
Date.prototype.maxDate = max;  
var myDate = new Date();  
  
if (myDate < myDate.maxDate())  
    document.write("today isn't the max");  
else if (myDate == myDate.maxDate())  
    document.write("today is the max");   
  
// Output:  
// today isn't the max  
  
```  
  
 Tutti gli intrinseci [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] gli oggetti hanno una `prototype` proprietà che è di sola lettura. È possibile aggiungere proprietà e metodi al prototipo, ma l'oggetto non può essere assegnato un prototipo diverso. Tuttavia, gli oggetti definiti dall'utente possono essere assegnati un nuovo prototipo.  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]