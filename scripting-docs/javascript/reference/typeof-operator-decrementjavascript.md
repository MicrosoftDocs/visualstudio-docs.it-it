---
title: Operatore typeof (JavaScript) | Documenti Microsoft
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
- typeof_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- typeof operator
ms.assetid: ee8a1036-119f-486f-b034-b07bdba87f0c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a9ff8c7942c773d138dd599956c41d1e583e6288
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/15/2018
---
# <a name="typeof-operator-javascript"></a>Operatore typeof (JavaScript)
Restituisce una stringa che identifica il tipo di dati di un'espressione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
typeof[(]expression[)] ;  
```  
  
## <a name="remarks"></a>Note  
 Il *espressione* argomento è un'espressione per il tipo di informazioni viene ricercate.  
  
 Il `typeof` operatore restituisce informazioni sul tipo sotto forma di stringa. Esistono sette possibili valori `typeof` restituisce: "number", "string", "booleano", ","oggetto "function," "undefined" e "sconosciuto".  
  
 Le parentesi sono facoltative nel `typeof` sintassi.  

 Potrebbe restituire un oggetto come un tipo sconosciuto in un evento XMLHTTPRequest. Un oggetto COM con nessun analogico in JavaScript può restituire anche come un tipo sconosciuto.
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente verifica il tipo di dati delle variabili.  
  
```JavaScript  
var index = 5;  
var result = (typeof index === 'number');  
// Output: true  
  
var description = "abc";  
var result = (typeof description === 'string');  
// Output: true  
```  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente verifica per un tipo di dati di `undefined` per le variabili dichiarate e non dichiarate.  
  
```JavaScript  
var declared;  
var result = (declared === undefined);  
// Output: true  
  
var result = (typeof declared === 'undefined');  
// Output: true  
  
var result = (typeof notDeclared === 'undefined')  
// Output: true  
  
var obj = {};  
var result = (typeof obj.propNotDeclared === 'undefined');  
// Output: true  
  
// An undeclared variable cannot be used in a comparison without  
// the typeof operator, so the next line generates an error.  
//  var result = (notDeclared === undefined);  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione Array. IsArray](../../javascript/reference/array-isarray-function-javascript.md)   
 [Funzione Object. getprototypeof](../../javascript/reference/object-getprototypeof-function-javascript.md)   
 [Costante undefined](../../javascript/reference/undefined-constant-javascript.md)   
 [Operatori di confronto](../../javascript/reference/comparison-operators-javascript.md)   
 [Riepilogo dei tipi di dati](../../javascript/data-types-javascript.md)   
 [Precedenza tra operatori](../../javascript/operator-subtractprecedence-javascript.md)   
 [Riepilogo degli operatori (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)