---
title: "Modalità strict (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT1038
- VS.WebClient.Help.SCRIPT1050
- VS.WebClient.Help.SCRIPT1042
- VS.WebClient.Help.SCRIPT1041
- VS.WebClient.Help.SCRIPT1046
- VS.WebClient.Help.SCRIPT1045
- VS.WebClient.Help.SCRIPT1037
- VS.WebClient.Help.SCRIPT1039
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- strict mode
- use strict
ms.assetid: 0f27022a-f41c-4504-965c-5a2701f342cd
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 77ee7d54dd265026b2bf4c9af52a71cccf9a7675
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="strict-mode-javascript"></a>Modalità strict (JavaScript)
La modalità strict consente di introdurre nel codice un migliore controllo degli errori. Quando si utilizza la modalità strict, non è possibile, ad esempio, utilizzare in modo implicito variabili dichiarate, assegnare un valore a una proprietà di sola lettura o aggiungere una proprietà a un oggetto non estendibile. Le restrizioni sono elencate nella sezione [Restrizioni sul codice in modalità strict](../../javascript/advanced/strict-mode-javascript.md#rest) più avanti in questo argomento. Per altre informazioni sulla modalità strict, vedere la [specifica del linguaggio ECMAScript, quinta edizione](http://www.ecma-international.org/publications/standards/Ecma-262.htm).  
  
> [!WARNING]
>  La modalità strict non è supportata nelle versioni di Internet Explorer precedenti alla 10.  
  
## <a name="declaring-strict-mode"></a>Dichiarazione della modalità strict  
 È possibile dichiarare la modalità strict aggiungendo `"use strict";` all'inizio di un file, di un programma o di una funzione. Questo tipo di dichiarazione è noto come *prologo della direttiva*. L'ambito di una dichiarazione della modalità strict dipende dal contesto. Se dichiarata in un contesto globale (al di fuori dell'ambito di una funzione), tutto il codice nel programma è in modalità strict. Se dichiarata in una funzione, tutto il codice presente nella funzione è in modalità strict. Nell'esempio seguente tutto il codice è in modalità strict e la dichiarazione di variabile all'esterno della funzione genera l'errore di sintassi "Variabile non definita in modalità strict".  
  
```JavaScript  
"use strict";  
function testFunction(){  
    var testvar = 4;  
    return testvar;  
}  
  
// This causes a syntax error.  
testvar = 5;  
  
```  
  
 Nell'esempio seguente, solo il codice all'interno di `testFunction` è in modalità strict. La dichiarazione di variabile all'esterno della funzione, a differenza di quella all'interno della funzione, non genera un errore di sintassi.  
  
```JavaScript  
function testFunction(){  
    "use strict";  
    // This causes a syntax error.  
    testvar = 4;  
    return testvar;  
}  
testvar = 5;  
  
```  
  
<a name="rest"></a>   
## <a name="restrictions-on-code-in-strict-mode"></a>Restrizioni relative al codice in modalità strict  
 Nella tabella seguente sono elencate le restrizioni più importanti valide in modalità strict.  
  
|||||  
|-|-|-|-|  
|**Elemento di linguaggio**|**Restrizione**|**Erroree**|**Esempio**|  
|Variabile|Utilizzo di una variabile senza la relativa dichiarazione.|SCRIPT5042: Variabile non definita in modalità strict.|`testvar = 4;`|  
|Proprietà di sola lettura.|Scrittura in una proprietà di sola lettura.|SCRIPT5045: Assegnazione a proprietà di sola lettura non consentita in modalità strict|`var testObj = Object.defineProperties({}, {     prop1: {         value: 10,         writable: false // by default     },     prop2: {         get: function () {         }     } }); testObj.prop1 = 20;  testObj.prop2 = 30;`|  
|Proprietà non estendibile|Aggiunta di una proprietà a un oggetto il cui attributo `extensible` è impostato su `false`.|SCRIPT5046: Impossibile creare la proprietà per un oggetto non estensibile|`var testObj = new Object();  Object.preventExtensions(testObj);  testObj.name = "Bob";`|  
|`delete`|Eliminazione di una variabile, una funzione o un argomento.<br /><br /> Eliminazione di una proprietà il cui attributo `configurable` è impostato su `false`.|SCRIPT1045: uso funzionalità di eliminazione in \<<expression> non consentito in modalità strict|`var testvar = 15; function testFunc() {}; delete testvar; delete testFunc;  Object.defineProperty(testObj, "testvar", {     value: 10,     configurable: false     }); delete testObj.testvar;`|  
|Duplicazione di una proprietà|Più definizioni di una proprietà in un valore letterale di oggetto.|SCRIPT1046: Più definizioni di una proprietà non consentite in modalità strict|`var testObj = {     prop1: 10,     prop2: 15,     prop1: 20 };`|  
|Duplicazione del nome di un parametro|Più utilizzi del nome di un parametro in una funzione.|SCRIPT1038: Nomi parametri formali duplicati non consentiti in modalità strict|`function testFunc(param1, param1) {     return 1; };`|  
|Parole chiave riservate future|Utilizzo di una parola chiave riservata futura come nome di una variabile o di una funzione.|SCRIPT1050: L'utilizzo di una parola riservata futura per un identificatore non è valido. Il nome dell'identificatore è riservato in modalità strict.|-                      `implements`<br /><br /> -                      `interface`<br /><br /> -                      `package`<br /><br /> -                      `private`<br /><br /> -                      `protected`<br /><br /> -                      `public`<br /><br /> -                      `static`<br /><br /> -                      `yield`|  
|Ottali|Assegnazione di un valore ottale a un valore letterale numerico o tentativo di utilizzo di un carattere di escape in un valore ottale.|SCRIPT1039: Letterali numerici ottali e caratteri escape non consentiti in modalità strict|`var testoctal = 010; var testescape = \010;`|  
|`this`|Il valore di `this` non viene convertito nell'oggetto globale quando è `null` o `undefined`.||`function testFunc() {     return this; } var testvar = testFunc();`<br /><br /> In modalità non strict il valore di `testvar` è l'oggetto globale, mentre in modalità strict il valore è `undefined`.|  
|`eval` come identificatore|La stringa "eval" non può essere utilizzata come identificatore (nome di variabile o di funzione, nome di parametro e così via).||`var eval = 10;`|  
|Funzione dichiarata in un'istruzione o in un blocco|Non è possibile dichiarare una funzione in un'istruzione o in un blocco.|SCRIPT1047: In modalità strict le dichiarazioni di funzioni non possono essere annidate in un'istruzione o un blocco. Possono essere visualizzate solo al livello superiore o direttamente in un corpo di funzione.|`var arr = [1, 2, 3, 4, 5]; var index = null; for (index in arr) {     function myFunc() {}; }`|  
|Variabile dichiarata in una funzione `eval`|Se una variabile viene dichiarata in una funzione `eval`, non può essere utilizzata all'esterno della funzione.|SCRIPT1041: Utilizzo non valido di 'eval' in modalità strict|`eval("var testvar = 10"); testvar = 15;`<br /><br /> La valutazione indiretta è possibile, ma non è possibile utilizzare una variabile dichiarata all'esterno della funzione `eval`.<br /><br /> `var indirectEval = eval; indirectEval("var testvar = 10;"); document.write(testVar);`<br /><br /> Questo codice causa un errore SCRIPT5009: 'testVar' non è definito.|  
|`Arguments` come identificatore|La stringa "arguments" non può essere utilizzata come identificatore (nome di variabile o di funzione, nome di parametro e così via).|SCRIPT1042: Uso non valido di 'arguments' in modalità strict|`var arguments = 10;`|  
|`arguments` in una funzione|Non è possibile modificare i valori dei membri dell'oggetto `arguments` locale.||`function testArgs(oneArg) {     arguments[0] = 20; }`<br /><br /> In modalità non strict si può modificare il valore del parametro `oneArg` modificando il valore di `arguments[0]`, in modo che il valore di `oneArg` e di `arguments[0]` sia 20. In modalità strict la modifica del valore di `arguments[0]` non influisce sul valore di `oneArg` perché l'oggetto `arguments` è una semplice copia locale.|  
|`arguments.callee`|Non consentito.||`function (testInt) {     if (testInt-- == 0)         return;     arguments.callee(testInt--); }`|  
|`with`|Non consentito.|SCRIPT1037: Le istruzioni 'with' non sono consentite in modalità strict|`with (Math){     x = cos(3);     y = tan(7); }`|