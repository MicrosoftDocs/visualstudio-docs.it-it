---
title: Oggetti intrinseci (JavaScript) | Microsoft Docs
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
- built-in objects [JavaScript]
- intrinsic objects [JavaScript]
ms.assetid: 6520c634-a7d1-4a05-8c1b-2e79f449d2e4
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 242b572c2818f9968e6d5fc51e1272e3004c0f05
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="intrinsic-objects-javascript"></a>Oggetti intrinseci (JavaScript)
[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] fornisce oggetti intrinseci o "incorporati", ovvero gli oggetti `Array`, `Boolean`, `Date`, `Error`, `Function`, **Global**, **JSON**, **Math**, **Number**, `Object`, `RegExp` e `String`. Agli oggetti intrinseci sono associati metodi, funzioni, proprietà e costanti descritti in dettaglio nei [riferimenti al linguaggio](../javascript/reference/javascript-reference.md).  
  
## <a name="array-object"></a>Oggetto Array  
 Gli indici di una matrice possono essere considerati come proprietà di un oggetto a cui fa riferimento il relativo indice numerico. Si noti che le proprietà denominate aggiunte a una matrice non possono essere indicizzate in base al numero e sono separate dagli elementi della matrice.  
  
 Per creare una nuova matrice, usare l'operatore **new** e il [costruttore](../javascript/reference/constructor-property-object-javascript.md) **Array()**, come nell'esempio seguente.  
  
```JavaScript  
var theMonths = new Array(12);  
theMonths[0] = "Jan";  
theMonths[1] = "Feb";  
theMonths[2] = "Mar";  
theMonths[3] = "Apr";  
theMonths[4] = "May";  
theMonths[5] = "Jun";  
theMonths[6] = "Jul";  
theMonths[7] = "Aug";  
theMonths[8] = "Sep";  
theMonths[9] = "Oct";  
theMonths[10] = "Nov";  
theMonths[11] = "Dec";  
```  
  
 Quando si crea una matrice usando la parola chiave `Array`, [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] include una proprietà **length** in cui è registrato il numero di voci. Se non si specifica un numero, la lunghezza viene impostata su 0 e la matrice non contiene voci. Se invece si specifica un numero, la lunghezza verrà impostata in base a tale numero. Se si specifica più di un parametro, i parametri verranno usati come voci della matrice. Il numero di parametri viene inoltre assegnato alla proprietà length, come nell'esempio seguente, che equivale a quello precedente.  
  
```JavaScript  
var theMonths = new Array("Jan", "Feb", "Mar", "Apr", "May", "Jun",   
"Jul", "Aug", "Sep", "Oct", "Nov", "Dec");  
```  
  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] modifica automaticamente il valore di **length** quando si aggiungono elementi a una matrice creata con la parola chiave `Array`. In [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] gli indici di matrice iniziano sempre con 0 e non con 1, quindi la proprietà length è sempre maggiore di un'unità rispetto all'indice massimo della matrice.  
  
## <a name="string-object"></a>Oggetto String  
 In [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] è possibile considerare le stringhe (e i numeri) come se fossero oggetti. L'[oggetto string](../javascript/reference/string-object-javascript.md) include alcuni metodi incorporati, che possono essere usati con le stringhe. Uno di questi è il [metodo substring](../javascript/reference/substring-method-string-javascript.md), che restituisce parte della stringa. Accetta due numeri come argomenti.  
  
```JavaScript  
var aString = "0123456789";  
  
// This code sets aChunk to "456".  
var aChunk = aString.substring(4, 7);  
  
// This code sets anotherChunk to "456", using  
// the lower value index as the starting index.  
var anotherChunk = aString.substring(7, 4);  
  
// This code sets the firstLetter variable to "J"  
// by using the array in the preceding array creation example.  
firstLetter = theMonths[5].substring(0,1);  
```  
  
 Un'altra proprietà dell'oggetto `String` è la proprietà **length**. Questa proprietà contiene il numero di caratteri presenti nella stringa oppure 0 (zero) nel caso di una stringa vuota. Si tratta di un valore numerico che può essere usato direttamente nei calcoli.  
  
```JavaScript  
var howLong = "Hello World".length  // Sets the howLong variable to 11.  
```  
  
## <a name="math-object"></a>Oggetto Math  
 Per l'oggetto **Math** sono disponibili diverse costanti e funzioni predefinite. Le costanti sono costituite da numeri specifici, uno dei quali è il valore pi greco, circa 3,14159. Si tratta della costante **Math.PI** illustrata nell'esempio seguente.  
  
```JavaScript  
var radius = 5;  
var circleArea = Math.PI * radius * radius;  
```  
  
 Una delle funzioni predefinite dell'oggetto **Math** è l'elevazione a potenza o `Math.pow`, che consente di elevare un numero a una potenza specificata. L'esempio seguente usa sia il pi greco che l'elevazione a potenza per calcolare il volume di una sfera.  
  
```JavaScript  
var volume = (4/3)*(Math.PI*Math.pow(radius,3));  
```  
  
## <a name="date-object"></a>Oggetto Date  
 L'oggetto `Date` può essere usato per rappresentare date e orari arbitrari, ottenere la data di sistema corrente e calcolare le differenze tra date. Ha numerose proprietà e metodi, tutti predefiniti. In generale, l'oggetto `Date` fornisce il giorno della settimana, il mese, il giorno e l'anno e l'orario espresso in ore, minuti e secondi. Queste informazioni si basano sul numero di millisecondi a partire dall'1 gennaio 1970, alle 00.00.00.000 GMT, ovvero l'ora di Greenwich. Il termine preferito è UTC (Universal Coordinated Time, Tempo universale coordinato) che fa riferimento ai segnali generati dallo standard di tempo universale. [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] può gestire date comprese nell'intervallo approssimativo dal 250.000 a.C al 255.000 d.C.  
  
 Per creare un nuovo oggetto `Date` usare l'operatore **new**, come indicato nell'esempio seguente.  
  
```JavaScript  
var toDay = new Date();    
var thisYear = toDay.getFullYear();  
var thisMonth = theMonths[toDay.getMonth()];  
var thisDay = thisMonth  + " " + toDay.getDate() + ", " + thisYear;  
```  
  
## <a name="number-object"></a>Oggetto Number  
 Oltre alle costanti numeriche speciali (ad esempio `PI`) disponibili nell'oggetto **Math**, in [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] sono disponibili molte altre costanti tramite l'oggetto **Number**.  
  
|Costante|Descrizione|  
|--------------|-----------------|  
|Number.MAX_VALUE|Numero massimo consentito, pari a circa 1,79E+308. Può essere positivo o negativo. Il valore varia leggermente a seconda del sistema. |  
|Number.MIN_VALUE|Numero minimo consentito, pari a circa 5,00E+324. Può essere positivo o negativo. Il valore varia leggermente a seconda del sistema. |  
|Number.NaN|Valore speciale non numerico (Not a Number).|  
|Number.POSITIVE_INFINITY|Qualsiasi valore positivo maggiore del numero positivo massimo (Number.MAX_VALUE) viene automaticamente convertito in questo valore. Rappresentato come infinito.|  
|Number.NEGATIVE_INFINITY|Qualsiasi valore più negativo del numero negativo massimo (-Number.MAX_VALUE) viene automaticamente convertito in questo valore. Rappresentato come -infinito.|  
  
 **Number.NaN** è una costante speciale definita come "non numerica". Un tentativo di analizzare una stringa che non può essere analizzata come numero restituisce **Number.NaN**. `NaN` viene considerata come diversa da qualsiasi numero e da se stessa. Per verificare un risultato `NaN`, anziché confrontarlo con la funzione **Number.NaN** usare la funzione **isNaN()**.  
  
## <a name="json-object"></a>Oggetto JSON  
 JSON è un formato di interscambio dei dati leggero basato su un sottoinsieme della notazione del valore letterale di oggetto del linguaggio JavaScript.  
  
 L'oggetto JSON fornisce due funzioni per la conversione nel formato testo JSON e da tale formato. La funzione [JSON.stringify](../javascript/reference/json-stringify-function-javascript.md) serializza gli oggetti e le matrici nel testo JSON. La funzione [JSON.parse](../javascript/reference/json-parse-function-javascript.md) deserializza il testo JSON per produrre oggetti in memoria. Per altre informazioni, vedere [An Introduction to JavaScript Object Notation (JSON) in JavaScript and .NET](http://go.microsoft.com/fwlink/?LinkId=124098) (Introduzione a JavaScript Object Notation (JSON) in JavaScript e .NET).  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetti JavaScript](../javascript/reference/javascript-objects.md)