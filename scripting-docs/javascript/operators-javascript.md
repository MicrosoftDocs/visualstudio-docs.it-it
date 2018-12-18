---
title: Operatori (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: JavaScript, operators
ms.assetid: b8602b69-aba9-46e8-86e1-cb533ad41410
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9d0a098418399dba19b77a12c057a3fba334e31
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="operators-javascript"></a>Operatori (JavaScript)
[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] dispone di una gamma completa di operatori: aritmetici, logici, di assegnazione, bit per bit e misti. Per le descrizioni e gli esempi d'uso vedere gli argomenti relativi ai singoli operatori.  
  
## <a name="computational-operators"></a>Operatori di calcolo  
  
|Descrizione|Simbolo|  
|-----------------|------------|  
|[Negazione unaria](../javascript/reference/subtraction-operator-decrement-javascript.md)|-|  
|[Incremento](../javascript/reference/increment-and-decrement-operators-javascript.md)|++|  
|[Decremento](../javascript/reference/increment-and-decrement-operators-javascript.md)|--|  
|[Moltiplicazione](../javascript/reference/multiplication-operator-decrement-javascript.md)|*|  
|[Divisione](../javascript/reference/division-operator-decrement-javascript.md)|/|  
|[Modulo aritmetico](../javascript/reference/modulus-operator-decrementjavascript.md)|%|  
|[Addizione](../javascript/reference/addition-operator-decrement-javascript.md)|+|  
|[Sottrazione](../javascript/reference/subtraction-operator-decrement-javascript.md)|-|  
  
## <a name="logical-operators"></a>Operatori logici  
  
|Descrizione|Simbolo|  
|-----------------|------------|  
|[NOT logico](../javascript/reference/logical-not-operator-decrement-exclpt-javascript.md)|!|  
|[Minore di](../javascript/reference/comparison-operators-javascript.md)|\<|  
|[Maggiore di](../javascript/reference/comparison-operators-javascript.md)|>|  
|[Minore o uguale a](../javascript/reference/comparison-operators-javascript.md)|\<=|  
|[Maggiore o uguale a](../javascript/reference/comparison-operators-javascript.md)|>=|  
|[Uguaglianza](../javascript/reference/comparison-operators-javascript.md)|==|  
|[Disuguaglianza](../javascript/reference/comparison-operators-javascript.md)|!=|  
|[AND logico](../javascript/reference/logical-and-operator-decrement-javascript.md)|&&|  
|[OR logico](../javascript/reference/logical-or-operator-decrement-javascript.md)|&#124;&#124;|  
|[Condizionale ternario](../javascript/reference/conditional-ternary-operator-decrement-javascript.md)|?:|  
|[Virgola](../javascript/reference/comma-operator-decrement-javascript.md)|,|  
|[Uguaglianza con vincolo](../javascript/reference/comparison-operators-javascript.md)|===|  
|[Disuguaglianza con vincolo](../javascript/reference/comparison-operators-javascript.md)|!==|  
  
## <a name="bitwise-operators"></a>Operatori bit per bit  
  
|Descrizione|Simbolo|  
|-----------------|------------|  
|[NOT bit per bit](../javascript/reference/bitwise-not-operator-decrement-tilde-javascript.md)|~|  
|[Spostamento a sinistra bit per bit](../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)|<\<|  
|[Spostamento a destra bit per bit](../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)|>>|  
|[Spostamento a destra senza segno](../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)|>>>|  
|[AND bit per bit](../javascript/reference/bitwise-and-operator-decrement-javascript.md)|&|  
|[XOR bit per bit](../javascript/reference/bitwise-xor-operator-decrement-hat-javascript.md)|^|  
|[OR bit per bit](../javascript/reference/bitwise-or-operator-decrement-javascript.md)|&#124;|  
  
## <a name="assignment-operators"></a>Operatori di assegnazione  
  
|Descrizione|Simbolo|  
|-----------------|------------|  
|[Assegnazione](../javascript/reference/assignment-operator-decrement-equal-javascript.md)|=|  
|[Assegnazione composta](../javascript/reference/compound-assignment-operators-javascript.md)|*OP*= (ad esempio += e &=)|  
  
## <a name="miscellaneous-operators"></a>Operatori vari  
  
|Descrizione|Simbolo|  
|-----------------|------------|  
|[delete](../javascript/reference/delete-operator-decrementjavascript.md)|delete|  
|[typeof](../javascript/reference/typeof-operator-decrementjavascript.md)|typeof|  
|[void](../javascript/reference/void-operator-decrementjavascript.md)|void|  
|[instanceof](../javascript/reference/instanceof-operator-decrementjavascript.md)|instanceof|  
|[new](../javascript/reference/new-operator-decrementjavascript.md)|new|  
|[in](../javascript/reference/in-operator-decrementjavascript.md)|in|  
  
## <a name="equality-and-strict-equality"></a>Uguaglianza e uguaglianza con vincoli  
 La differenza tra == (uguaglianza) e === (uguaglianza con vincoli) sta nel fatto che l'operatore di uguaglianza converte i valori di tipi diversi prima di verificare l'uguaglianza. Ad esempio, con l'operatore di uguaglianza il confronto tra la stringa "1" e il numero 1 risulta true. Con l'operatore di uguaglianza con vincoli invece i valori di tipi diversi non vengono convertiti, pertanto la stringa "1" non risulta uguale al numero 1.  
  
 Le stringhe primitive, i numeri e i valori booleani vengono confrontati in base al valore. Se hanno lo stesso valore, sono uguali. Gli oggetti (inclusi gli oggetti `Array`, `Function`, `String`, **Number**, `Boolean`, **Error** `Date` e `RegExp`) vengono confrontati in base al riferimento. Anche se due variabili di questi tipi hanno lo stesso valore, sono uguali solo se fanno riferimento esattamente allo stesso oggetto.  
  
 Ad esempio:  
  
```JavaScript  
// Two strings with the same value.  
var string1 = "Hello";  
var string2 = "Hello";  
  
// Two String objects with the same value.  
var StringObject1 = new String(string1);  
var StringObject2 = new String(string2);  
  
if (string1 == string2)  
    document.write("string1 is equal to string2 <br/>");  
  
if (StringObject1 != StringObject2)  
    document.write("StringObject1 is not equal to StringObject2 <br/>");  
  
// To compare the values of String objects, use the toString() or valueOf() methods.  
if (StringObject1.valueOf() == StringObject2.valueOf())  
    document.write("The value of StringObject1 is equal to the value of StringObject2");  
  
//Output:  
// string1 is equal to string2   
// StringObject1 is not equal to StringObject2   
// The value of StringObject1 is equal to the value of StringObject2  
  
```