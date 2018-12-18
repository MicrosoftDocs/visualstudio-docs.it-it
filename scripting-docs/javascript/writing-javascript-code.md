---
title: Scrittura di codice JavaScript | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.htmldesigner.html
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- code, JavaScript syntax
- comments, JavaScript code
- JavaScript code
ms.assetid: dde28266-0d0f-4460-a819-f931cf0911ad
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e50bc25f818724b59d9adda51f97d76ae14de2b4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="writing-javascript-code"></a>Scrittura di codice JavaScript
Come molti altri linguaggi di programmazione, [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] è organizzato in istruzioni, blocchi costituiti da set di istruzioni correlate e commenti. All'interno di un'istruzione è possibile usare variabili, stringhe, numeri ed espressioni.  
  
## <a name="statements"></a>Istruzioni  
 Un programma [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] è una raccolta di istruzioni. Le istruzioni [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] combinano espressioni in modo da portare a termine un'attività completa.  
  
 Un'istruzione è costituita da una o più espressioni, parole chiave o operatori (simboli). In genere un'istruzione viene scritta su una riga singola, ma può essere scritta su due o più righe. È anche possibile scrivere due o più istruzioni sulla stessa riga, separandole con punti e virgola. In genere ogni nuova riga indica l'inizio di una nuova istruzione. È consigliabile terminare le istruzioni in modo esplicito. Per fare ciò si usa il punto e virgola (;), il carattere di terminazione istruzione di [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
 Di seguito sono riportati due esempi di istruzioni [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]. Le frasi dopo i caratteri // sono *commenti*, osservazioni esplicative della funzionalità del programma.  
  
```JavaScript  
var aBird = "Robin"; // Assign the text "Robin" to the variable aBird.  
var today = new Date(); // Assign today's date to the variable today.  
```  
  
 Un gruppo di istruzioni [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] racchiuse tra parentesi graffe ({}) è detto *blocco*. In genere le istruzioni raggruppate in un blocco possono essere considerate come un'unica istruzione. Ciò significa che è possibile usare i blocchi nella maggior parte dei punti in cui [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] prevede l'uso una singola istruzione. Le eccezioni degne di nota includono le intestazioni dei cicli **for** e `while`. Si noti che le singole istruzioni all'interno di un blocco terminano con un punto e virgola, ma non così il blocco stesso.  
  
 In genere i blocchi vengono usati in funzioni e istruzioni condizionali. Si noti che a differenza di C++ e di altri linguaggi, in [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] un blocco non viene considerato come un nuovo ambito; solo le funzioni creano un nuovo ambito.  
  
 Nell'esempio seguente la clausola `else` contiene un blocco di due istruzioni delimitato da parentesi graffe. Il blocco viene considerato come un'istruzione singola. La funzione stessa è costituita da un blocco di istruzioni racchiuse tra parentesi graffe. Le istruzioni sotto la funzione si trovano all'esterno del blocco e pertanto non appartengono alla definizione della funzione.  
  
```JavaScript  
function inchestometers(inches)  
   {  
   if (inches < 0)  
      return -1;  
   else  
      {  
      var meters = inches / 39.37;  
      return meters;  
      }  
   }  
  
var inches = 12;  
var meters = inchestometers(inches);  
document.write("the value in meters is " + meters);  
```  
  
## <a name="comments"></a>Commenti  
 Un commento [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] a riga singola inizia con una coppia di caratteri barra (//). Di seguito è riportato un esempio di commento a riga singola.  
  
```JavaScript  
var aGoodIdea = "Comment your code thoroughly."; // This is a single-line comment.  
```  
  
 Un commento [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] su più righe inizia con una barra e un asterisco (/*) e termina con gli stessi caratteri nell'ordine inverso (\*/).  
  
```JavaScript  
/*  
This is a multiline comment that explains the preceding code statement.  
  
The statement assigns a value to the aGoodIdea variable. The value,   
which is contained between the quote marks, is called a literal. A   
literal explicitly and directly contains information; it does not   
refer to the information indirectly. The quote marks are not part   
of the literal.  
*/  
```  
  
> [!NOTE]
>  Se si prova a incorporare un commento su più righe in un altro, [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] interpreta il commento risultante in modo imprevisto. La sequenza */ che indica la fine del commento su più righe incorporato viene interpretata come la fine dell'intero commento su più righe. Di conseguenza il testo che segue il commento su più righe incorporato non viene impostato come commento, ma interpretato come codice [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] e genera errori di sintassi.  
  
 È consigliabile scrivere tutti i commenti come blocchi di commenti a riga singola. In questo modo, successivamente sarà possibile impostare come commento segmenti di codice di grandi dimensioni con la notazione del commento su più righe.  
  
```JavaScript  
// This is another multiline comment, written as a series of single-line comments.  
// After the statement is executed, you can refer to the content of the   
// aGoodIdea variable by using its name.  
var extendedIdea = aGoodIdea + " You never know when you'll have to figure out what it does.";  
```  
  
## <a name="assignments-and-equality"></a>Assegnazioni e uguaglianza  
 Il segno di uguale (=) viene usato nelle istruzioni [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] per assegnare valori alle variabili: è l'operatore di assegnazione. L'operando a sinistra dell'operatore = è sempre un lvalue. Sono esempi di lvalue:  
  
-   le variabili,  
  
-   gli elementi di matrice,  
  
-   le proprietà oggetto.  
  
 L'operando a destra dell'operatore = è sempre un rvalue. I valori rvalue possono essere valori arbitrari di qualsiasi tipo, incluso il valore di un'espressione. Di seguito è riportato un esempio di istruzione di assegnazione [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
```JavaScript  
var anInteger = 3;  
```  
  
 Il compilatore [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] interpreta questa istruzione come "Assegna il valore 3 alla variabile **anInteger**" oppure come "**anInteger** accetta il valore 3".  
  
 Si noti la differenza tra l'operatore = (assegnazione) e l'operatore == (uguaglianza). Se si vuole confrontare due valori per sapere se sono uguali, usare due segni di uguale (==). Questo argomento è illustrato in dettaglio in [Controllo del flusso di programma](../javascript/controlling-program-flow-javascript.md).  
  
## <a name="expressions"></a>Espressioni  
 Il valore di un'espressione [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] può essere di qualsiasi tipo [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] valido: un numero, una stringa, un oggetto e così via. Le espressioni più semplici sono valori letterali. Di seguito sono riportati alcuni esempi di espressioni letterali [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
```JavaScript  
3.9                       // numeric literal  
"Hello!"                  // string literal  
false                     // boolean literal  
null                      // literal null value  
{x:1, y:2}                // Object literal  
[1,2,3]                   // Array literal  
function(x){return x*x;}  // function literal  
```  
  
 Le espressioni più complesse possono contenere variabili, chiamate di funzione e altre espressioni. È possibile combinare le espressioni e creare espressioni complesse usando gli operatori. Sono esempi di operatori: `+` (addizione), `-` (sottrazione), `*` (moltiplicazione) e `/` (divisione).  
  
 Di seguito sono riportati alcuni esempi di espressioni complesse [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
```JavaScript  
var anExpression = 3 * (4 / 5) + 6;  
var aSecondExpression = Math.PI * radius * radius;  
var aThirdExpression = aSecondExpression + "%" + anExpression;  
var aFourthExpression = "(" + aSecondExpression + ") % (" + anExpression + ")";  
```