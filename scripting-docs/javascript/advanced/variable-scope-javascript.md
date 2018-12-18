---
title: Ambito della variabile (JavaScript) | Microsoft Docs
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
helpviewer_keywords:
- scope, JavaScript
- variable scope [JavaScript]
- variables, scope [JavaScript]
ms.assetid: a811a9a6-856f-46e9-8be3-f2d22a0c245f
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5afc99bf3d1006b68e1d6c4c8d5bbcfc90eb776f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="variable-scope-javascript"></a>Ambito della variabile (JavaScript)
[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] contiene due ambiti: globale e locale. Una variabile dichiarata all'esterno di una definizione di funzione è globale e il relativo valore è accessibile e modificabile nell'intero programma. Una variabile dichiarata all'interno di una definizione di funzione è locale. Essa viene creata ed eliminata a ogni esecuzione della funzione. L'accesso alla variabile locale è consentito soltanto da codice all'esterno della funzione. Il codice JavaScript non supporta l'ambito blocco (in cui un set di parentesi graffe `{. . .}` definisce un nuovo ambito), tranne nel caso speciale delle variabili con ambito blocco.  
  
## <a name="scope-in-javascript"></a>Ambito in JavaScript  
 Il nome di una variabile locale può corrispondere a quello di una variabile globale. Tuttavia le variabili rimangono completamente separate. La modifica del valore di una variabile non ha alcun effetto sull'altra. Solo la versione locale assume significato all'interno della funzione in cui viene dichiarata.  
  
```JavaScript  
// Global definition of aCentaur.  
var aCentaur = "a horse with rider,";  
  
// A local aCentaur variable is declared in this function.  
function antiquities(){  
  
   var aCentaur = "A centaur is probably a mounted Scythian warrior";  
}  
  
antiquities();  
aCentaur += " as seen from a distance by a naive innocent.";  
  
document.write(aCentaur);  
  
// Output: "a horse with rider, as seen from a distance by a naive innocent."  
```  
  
 In JavaScript le variabili vengono valutate come se fossero dichiarate all'inizio di qualsiasi ambito in cui esistono. A volte ciò comporta risultati imprevisti, come illustrato qui.  
  
```JavaScript  
var aNumber = 100;  
tweak();  
  
function tweak(){  
  
    // This prints "undefined", because aNumber is also defined locally below.  
    document.write(aNumber);  
  
    if (false)  
    {  
        var aNumber = 123;    
    }  
}  
```  
  
 Quando [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] esegue una funzione, cerca innanzitutto tutte le dichiarazioni delle variabili, ad esempio `var someVariable;`, e crea le variabili con un valore iniziale `undefined`. Se una variabile è dichiarata con un valore, ad esempio `var someVariable = "something";`, inizialmente presenta ancora il valore `undefined` e assumerà il valore dichiarato solo quando la riga contenente la dichiarazione viene eseguita.  
  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] elabora tutte le dichiarazioni delle variabili prima dell'esecuzione del codice, indipendentemente dal fatto che le dichiarazioni si trovino all'interno di un blocco condizionale o di un altro costrutto. Una volta trovate tutte le variabili in [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], viene eseguito il codice nella funzione. Se una variabile viene dichiarata in modo implicito all'interno di una funzione, ovvero se viene visualizzata a sinistra di un'espressione di assegnazione ma non è stata dichiarata con `var`, viene creata come variabile globale.  
  
 In JavaScript, una funzione (annidata) interna archivia i riferimenti nelle variabili locali presenti nello stesso ambito della funzione stessa, anche dopo che la funzione è stata eseguita. Questo set di riferimenti viene chiamato chiusura. Nell'esempio seguente, la seconda chiamata alla funzione interna restituisce lo stesso messaggio ("Hello Bill") della prima chiamata, perché il parametro di input per la funzione esterna, `name`, è una variabile locale archiviata nella chiusura della funzione interna.  
  
```JavaScript  
function send(name) {  
    // Local variable 'name' is stored in the closure  
    // for the inner function.  
    return function () {  
        sendHi(name);  
    }  
}  
  
function sendHi(msg) {  
    console.log('Hello ' + msg);  
}  
  
var func = send('Bill');  
func();  
// Output:  
// Hello Bill  
sendHi('Pete');  
// Output:  
// Hello Pete  
func();  
// Output:  
// Hello Bill  
```  
  
## <a name="block-scoped-variables"></a>Variabili con ambito blocco  
 In Internet Explorer 11 è stato introdotto il supporto di [let](../../javascript/reference/let-statement-javascript.md) e [const](../../javascript/reference/const-statement-javascript.md), che sono variabili con ambito blocco. Per queste variabili, le parentesi graffe `{. . .}` definiscono un nuovo ambito. Quando si imposta una di queste variabili su un valore specifico, il valore viene applicato solo all'ambito in cui è impostato.  
  
 Nell'esempio seguente viene illustrato l'utilizzo di `let` e dell'ambito blocco.  
  
> [!NOTE]
>  Il codice seguente è supportato nella modalità standard di Internet Explorer 11 e versioni successive.  
  
```JavaScript  
let x = 10;  
var y = 10;  
{  
    let x = 5;  
    var y = 5;  
    {  
        let x = 2;  
        var y = 2;  
        document.write("x: " + x + "<br/>");  
        document.write("y: " + y + "<br/>");  
        // Output:  
        // x: 2  
        // y: 2  
    }  
    document.write("x: " + x + "<br/>");  
    document.write("y: " + y + "<br/>");  
    // Output:  
    // x: 5  
    // y: 2  
}  
  
document.write("x: " + x + "<br/>");  
document.write("y: " + y + "<br/>");  
// Output:  
// x: 10  
// y: 2  
```