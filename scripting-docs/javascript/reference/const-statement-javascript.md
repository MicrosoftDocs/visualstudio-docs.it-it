---
title: Istruzione const (JavaScript) | Documenti Microsoft
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
- const_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- declaring variables, const statement
- const statement
ms.assetid: 3ad0840f-437f-4163-9571-86ecc5ddb987
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 68130cec4f1b1fe89d2fe3e673b28963d79aebde
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="const-statement-javascript"></a>Istruzione const (JavaScript)
Dichiara una variabile con ambito blocco con un valore costante.  
  
## <a name="syntax"></a>Sintassi  
  
```  
const constant1 = value1  
```  
  
#### <a name="parameters"></a>Parametri  
 `constant1`  
 Il nome della variabile viene dichiarata.  
  
 `value1`  
 Il valore iniziale assegnato alla variabile.  
  
## <a name="remarks"></a>Note  
 Utilizzare il `const` istruzione per dichiarare una variabile con un valore costante, l'ambito dei quali è limitato al blocco in cui è dichiarato. Il valore della variabile non può essere modificato.  
  
 Una variabile dichiarata con `const` deve essere inizializzato quando vengono dichiarati.  
  
## <a name="example"></a>Esempio  
 Nel codice seguente viene illustrato l'utilizzo dell'istruzione `const`.  
  
```JavaScript  
var c = 10;  
{  
    const c = 2;  
   // At this point, c = 2.  
}  
// At this point, c = 10.  
  
// Additional ways to declare a variable using const.  
const name = "Thomas Jefferson";  
const answer = 42, numpages = 10;  
const myarray = new Array();  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [let (istruzione)](../../javascript/reference/let-statement-javascript.md)   
 [Operatore new](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Oggetto Array](../../javascript/reference/array-object-javascript.md)   
 [Variabili](../../javascript/variables-javascript.md)