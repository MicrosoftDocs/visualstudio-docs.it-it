---
title: Condizionale operatore ternario (?:) (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '?:'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- conditional operators
- conditional (Ternary) operator
- ternary
ms.assetid: 7399ac32-9324-4a9a-ae76-be9c0f9df81c
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1dc34b5c633cfc02219cb01061e1aaa017e0f7f2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="conditional-ternary-operator--javascript"></a>Operatore condizionale ternario (?:) (JavaScript)
Restituisce una di due espressioni a seconda che una condizione risulti vera o falsa.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
test ? expression1 : expression2  
```  
  
## <a name="parameters"></a>Parametri  
 `test`  
 Espressione booleana qualsiasi.  
  
 `expression1`  
 Espressione restituita se `test` è `true`. Può essere un'espressione delimitata da virgole.  
  
 `expression2`  
 Espressione restituita se `test` è `false`. Un'espressione delimitata da virgole può collegare più espressioni.  
  
## <a name="remarks"></a>Note  
 L'operatore `?:` può essere utilizzato come alternativa rapida all'istruzione `if...else`. Viene infatti utilizzato come parte di un'espressione più ampia in cui l'utilizzo dell'istruzione `if...else` risulterebbe più complesso. Ad esempio:  
  
```JavaScript  
var now = new Date();  
var greeting = "Good" + ((now.getHours() > 17) ? " evening." : " day.");  
```  
  
 Nell'esempio viene creata una stringa contenente "Good evening." Se è successivo alle 18.00. Il codice equivalente utilizzando un'istruzione `if...else` sarebbe analogo al seguente:  
  
```JavaScript  
var now = new Date();  
var greeting = "Good";  
if (now.getHours() > 17)  
   greeting += " evening.";  
else  
   greeting += " day.";  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [if... istruzione else](../../javascript/reference/if-dot-dot-dot-else-statement-javascript.md)   
 [Precedenza tra operatori](../../javascript/operator-subtractprecedence-javascript.md)   
 [Riepilogo degli operatori (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)   
 [App di esempio di script Junkie configurazione widget](http://code.msdn.microsoft.com/Script-Junkie-Configuration-543ece24)