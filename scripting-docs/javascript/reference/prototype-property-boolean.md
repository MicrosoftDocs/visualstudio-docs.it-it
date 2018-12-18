---
title: "Proprietà prototype (Boolean) | Documenti Microsoft"
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
ms.assetid: e4f07cb5-3462-488c-a418-76064ab10eae
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 52d2d241c4d550fe4491ea827fab9d586281242d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-boolean"></a>Proprietà prototype (Boolean)
Restituisce un riferimento al prototipo per un valore booleano.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
boolean.prototype  
```  
  
## <a name="remarks"></a>Note  
 L'argomento `boolean` è il nome di un oggetto.  
  
 La proprietà `prototype` fornisce un set di base di funzionalità a una classe di oggetti. Le nuove istanze di un oggetto "ereditano" il comportamento del prototipo assegnato all'oggetto. È possibile aggiungere proprietà e metodi al prototipo, ma non assegnare gli oggetti incorporati a un prototipo diverso.  
  
 Per aggiungere, ad esempio, un metodo all'oggetto `Boolean` che restituisce il valore dell'elemento più grande della matrice, dichiarare la funzione, aggiungerla a `Boolean.prototype` e quindi usarla.  
  
```JavaScript  
function isFalse( ){  
    if (this.toString() == "false")  
         return true;  
    else  
        return false;  
}  
Boolean.prototype.isFalse = isFalse;  
var bool = new Boolean(1);  
document.write(bool.isFalse());  
  
// Output:  
// false  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]