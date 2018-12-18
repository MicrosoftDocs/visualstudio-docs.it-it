---
title: Funzione Symbol.for (JavaScript) | Documenti Microsoft
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
ms.assetid: 27db15f3-9108-4892-8f89-e84031729cb6
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b7e47c00fbaa321d71a3eeba79e523eee719fb2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="symbolfor-function-javascript"></a>Funzione Symbol.for (JavaScript)
Restituisce il simbolo relativo a una chiave specificata o, se la chiave non è presente, crea un nuovo oggetto simbolo con la nuova chiave.  
  
## <a name="syntax"></a>Sintassi  
  
```vb  
Symbol.for(key);  
```  
  
#### <a name="parameters"></a>Parametri  
 `key`  
 Obbligatorio. Chiave per il simbolo che viene usata anche come descrizione.  
  
## <a name="remarks"></a>Note  
 Questo metodo cerca il simbolo nel registro dei simboli globali. Se si serializzano i simboli sotto forma di stringhe, usare il registro dei simboli globali per assicurare il mapping di una particolare stringa al simbolo corretto per tutte le ricerche.  
  
## <a name="example"></a>Esempio  
  
```JavaScript  
var sym = Symbol.for("desc");  
  
console.log(sym.toString());  
  
// Two different object references.  
console.log(Symbol("symbol") === Symbol.for("symbol");)  
// Single object reference.   
console.log(Symbol.for("symbol") === Symbol.for("symbol");)  
  
// Output:  
// Symbol(desc);  
// false  
// true  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]