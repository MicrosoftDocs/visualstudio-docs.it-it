---
title: Istruzione Let (JavaScript) | Documenti Microsoft
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
- let_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- let statement
- declaring variables, let statement
ms.assetid: c7e4f8a9-8f54-47b6-aed2-956959c1ecfd
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c447a1bf0c430771ff146965a592f7e160e2055b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="let-statement-javascript"></a>Istruzione let (JavaScript)
Dichiara una variabile con ambito blocco.  
  
## <a name="syntax"></a>Sintassi  
  
```  
let variable1 = value1  
```  
  
#### <a name="parameters"></a>Parametri  
 `variable1`  
 Il nome della variabile viene dichiarata.  
  
 `value1`  
 Il valore iniziale assegnato alla variabile.  
  
## <a name="remarks"></a>Note  
 Utilizzare il `let` istruzione per dichiarare una variabile, l'ambito dei quali è limitato al blocco in cui è dichiarato. È possibile assegnare valori alle variabili di dichiarazione o in un secondo momento nello script.  
  
 Una variabile dichiarata con `let` non può essere utilizzato prima che genererà un errore o la relativa dichiarazione.  
  
 Se non si inizializza la variabile nel `let` istruzione, gli viene assegnato automaticamente il [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] valore `undefined`.  
  
## <a name="example"></a>Esempio  
 Nel codice seguente viene illustrato l'utilizzo dell'istruzione `let`.  
  
```JavaScript  
var  l = 10;  
{  
    let l = 2;  
   // At this point, l = 2.  
}  
// At this point, l = 10.  
  
// Additional ways to declare a variable using let.  
let index;  
let name = "Thomas Jefferson";  
let answer = 42, counter, numpages = 10;  
let myarray = new Array();  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [const (istruzione)](../../javascript/reference/const-statement-javascript.md)   
 [Operatore new](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Oggetto Array](../../javascript/reference/array-object-javascript.md)   
 [Variabili](../../javascript/variables-javascript.md)