---
title: "Proprietà prototype (String) | Documenti Microsoft"
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
ms.assetid: 437ce478-9c45-45f7-8952-bd71856cfcd8
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: df8c6abbd64fce9172d805c2e22dee51f4fbbee4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-string"></a>Proprietà prototype (String)
Restituisce un riferimento al prototipo per una classe di stringa.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
string.prototype  
```  
  
## <a name="remarks"></a>Note  
 Il `string` argomento è il nome di una stringa.  
  
 Usare la proprietà `prototype` per fornire un set di funzionalità di base a una classe di oggetti. Le nuove istanze di un oggetto "ereditano" il comportamento del prototipo assegnato all'oggetto.  
  
 Ad esempio, per aggiungere un metodo per il `String` che restituisce il valore dell'ultimo elemento della stringa dell'oggetto, dichiarare la funzione, aggiungerla a `String.prototype`e quindi usarla.  
  
```JavaScript  
function string_last( ){  
    return this.charAt(this.length - 1);  
}  
String.prototype.last = string_last;  
var myString = new String("every good boy does fine");  
document.write(myString.last());  
  
// Output:  
// e  
```  
  
 Tutti gli intrinseci [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] gli oggetti hanno una `prototype` proprietà che è di sola lettura. È possibile aggiungere proprietà e metodi al prototipo, ma l'oggetto non può essere assegnato un prototipo diverso. Tuttavia, gli oggetti definiti dall'utente possono essere assegnati un nuovo prototipo.  
  
 Gli elenchi di metodo e proprietà per ogni oggetto intrinseco in questa Guida di riferimento indicano quali fanno parte del prototipo dell'oggetto e non.  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]