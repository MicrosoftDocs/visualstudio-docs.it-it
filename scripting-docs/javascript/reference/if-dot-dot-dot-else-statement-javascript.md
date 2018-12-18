---
title: if... istruzione else (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- else_JavaScriptKeyword
- if_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- if statement, if...else
- loop structures, if...else statements
ms.assetid: dfbe86e8-9c1e-4ef5-bb9c-7d1db7ce2506
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fad12b970f69a15040acb59195f957a2a6eec3e0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="ifelse-statement-javascript"></a>Istruzione if...else (JavaScript)
Esegue un gruppo di istruzioni in base a determinate condizioni, a seconda del valore di un'espressione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
if (condition1) {  
    statement1  
}  
[else if (condition2) {  
    statement2  
}]  
[else {  
    statement3]   
}]  
```  
  
## <a name="parameters"></a>Parametri  
 `condition1`  
 Obbligatorio. Espressione booleana. Se `condition1` è `null` o `undefined`, `condition1` viene trattato come `false`.  
  
 `statement1`  
 Parametro facoltativo. L'istruzione da eseguire se `condition1` è **true**. Può essere un'istruzione composta.  
  
 `condition2`  
 La condizione da valutare.  
  
 `statement2`  
 Parametro facoltativo. L'istruzione da eseguire se `condition2` è `true`. Può essere un'istruzione composta.  
  
 `statement3`  
 Se entrambi `condition1` e `condition2` sono `false`, questa istruzione viene eseguita.  
  
## <a name="example"></a>Esempio  
 Il codice seguente viene illustrato come utilizzare `if`, `if else`, e `else`.  
  
 È consigliabile racchiudere `statement1` e `statement2` tra parentesi graffe ({}) per maggiore chiarezza e per evitare errori involontari.  
  
```JavaScript  
var z = 3;  
if (x == 5) {  
    z = 10;  
}  
else if (x == 10) {  
    z = 15;  
}  
else {  
    z = 20;  
}  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Operatore condizionale ternario (?:)](../../javascript/reference/conditional-ternary-operator-decrement-javascript.md)