---
title: Funzioni (JavaScript) | Microsoft Docs
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
helpviewer_keywords: intrinsic JavaScript functions
ms.assetid: e2a72b5a-3edd-43d8-95e8-91721b38c1c1
caps.latest.revision: "24"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7275985d07f9f564dac98ba39e5ec31618dcaac4
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/13/2018
---
# <a name="functions-javascript"></a>Funzioni (JavaScript)
Le funzioni [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] eseguono azioni; inoltre, possono restituire valori. In alcuni casi sono i risultati di calcoli o confronti. Le funzioni vengono chiamate anche "metodi globali".  
  
 Le funzioni combinano più operazioni con un solo nome. Ciò consente di semplificare il codice. È possibile scrivere una serie di istruzioni, denominarla e quindi eseguire l'intera serie chiamandola e passando le informazioni necessarie.  
  
 È possibile passare informazioni a una funzione racchiudendo le informazioni tra parentesi dopo il nome della funzione. I tipi di informazioni che vengono passati a una funzione sono denominati argomenti o parametri. Alcune funzioni non accettano alcun argomento mentre altri accettano uno o più argomenti. In alcune funzioni il numero di argomenti dipende da come si usa la funzione.  
  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] supporta due tipi di funzioni: quelle integrate nel linguaggio e quelle create dall'utente.  
  
## <a name="built-in-functions"></a>Funzioni integrate  
 Il linguaggio [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] include diverse funzioni integrate. Alcune consentono di gestire le espressioni e i caratteri speciali, mentre altre di convertire le stringhe in valori numerici.  
  
 Per informazioni su queste funzioni predefinite, vedere [Metodi JavaScript](../javascript/reference/javascript-methods.md).  
  
## <a name="creating-your-own-functions"></a>Creazione di funzioni personalizzate  
 È possibile creare funzioni personalizzate e usarle dove necessario. Una definizione di funzione è costituita da un'istruzione di funzione e da un blocco di istruzioni [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
 La funzione **checkTriplet** nell'esempio seguente usa le lunghezze dei lati di un triangolo come argomenti e calcola se il triangolo è un triangolo rettangolo controllando se tre numeri costituiscono una terna pitagorica (il quadrato della lunghezza dell'ipotenusa di un triangolo è uguale alla somma dei quadrati delle lunghezze delle due lati). La funzione checkTriplet chiama un'altra funzione per eseguire il test effettivo.  
  
 Si noti l'uso di un numero molto piccolo ("epsilon") come variabile di test nella versione a virgola mobile del test. Considerate le incertezze e gli errori di arrotondamento nei calcoli a virgola mobile, non è opportuno verificare direttamente se i tre numeri costituiscono una terna pitagorica a meno che tutti i tre valori in questione siano valori integer. Poiché un test diretto è più accurato, il codice in questo esempio determina se è appropriato e, in tal caso, lo usa.  
  
```JavaScript  
var epsilon = 0.00000000001; // Some very small number to test against.  
  
// The test function for integers.  
function integerCheck(a, b, c)   
{  
   // The test itself.  
   if ( (a*a) == ((b*b) + (c*c)) )     
      return true;  
  
   return false;  
} // End of the integer checking function.  
  
// The test function for floating-point numbers.  
function floatCheck(a, b, c)     
{  
   // Make the test number.  
   var delta = ((a*a) - ((b*b) + (c*c)))  
  
   // The test requires the absolute value  
   delta = Math.abs(delta);  
  
   // If the difference is less than epsilon, then it's pretty close.  
   if (delta < epsilon)     
      return true;  
  
   return false;  
} // End of the floating-poing check function.  
  
// The triplet checker.   
function checkTriplet(a, b, c)  
{   
   // Create a temporary variable for swapping values  
   var d = 0;   
  
   // First, move the longest side to position "a".  
  
   // Swap a and b if necessary  
   if (b > a)  
   {  
      d = a;  
      a = b;  
      b = d;  
   }  
  
   // Swap a and c if necessary  
   if (c > a)  
   {  
      d = a;  
      a = c;  
      c = d;  
   }  
  
   // Test all 3 values. Are they integers?  
   if (((a % 1) == 0) && ((b % 1) == 0) && ((c % 1) == 0))  
   {   
      // If so, use the precise check.  
      return integerCheck(a, b, c);   
   }  
   else  
   {  
      // If not, get as close as is reasonably possible.  
      return floatCheck(a, b, c);   
   }  
} // End of the triplet check function.  
  
// The next three statements assign sample values for testing purposes.  
var sideA = 5;  
var sideB = 5;  
var sideC = Math.sqrt(50.001);  
  
// Call the function. After the call, 'result' contains the result.  
var result = checkTriplet(sideA, sideB, sideC);  
```  
  
<a name="Arrow"></a>   
## <a name="arrow-functions"></a>Funzioni freccia  
 La sintassi della funzione freccia, `=>`, fornisce un metodo rapido per specificare una funzione anonima. Di seguito è riportata la sintassi della funzione freccia.  
  
```JavaScript  
([arg] [, arg]) => {  
    statements  
}  
```  
  
 I valori a sinistra della freccia, che possono essere racchiusi tra parentesi, specificano gli argomenti passati alla funzione. Un singolo argomento alla funzione non richiede parentesi. Le parentesi sono necessarie se non vengono passati argomenti. La definizione di funzione a destra della freccia può essere un'espressione, ad esempio `v + 1`, o un blocco di istruzioni racchiuse tra parentesi graffe ({}).  
  
> [!IMPORTANT]
>  La sintassi della funzione freccia è supportata solo in [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)].  
  
 Non è possibile usare l'operatore `new` con una funzione freccia.  
  
 Gli esempi di codice seguente mostrano l'uso della funzione freccia con espressioni come le definizioni di funzione. Nel primo esempio, v viene passato come argomento all'espressione. Nel secondo esempio, v e i vengono passati come argomento all'espressione.  
  
```  
var evens = [2, 4, 6, 8];  
  
// Using standard syntax.  
var odds = evens.map(function(v) { return v + 1; });  
  
// Using arrow function syntax.  
// Add one to each value to produce output.  
var odds = evens.map(v => v + 1);  
  
// The following line of code adds the index value to the passed  
// in value to produce output.  
// Note: the second argument to the callback function in the map   
// method is the index value (i).  
var nums = evens.map((v, i) => v + i);  
  
console.log(odds);  
console.log(nums);  
  
// Output:  
// [object Array] [3, 5, 7, 9]  
// [object Array] [2, 5, 8, 11]  
```  
  
 Nell'esempio di codice seguente viene illustrato l'uso della funzione freccia con un blocco dell'istruzione.  
  
```JavaScript  
var fives = new Array();  
  
// Statement block, re-using nums array from previous example.  
// Note: The first argument to the callback function in forEach  
// is the value of the array element (v).  
nums.forEach(v => {  
  if (v % 5 === 0)  
    fives.push(v);  
});  
  
console.log(fives);  
  
// Output:  
// [object Array] [5]  
```  
  
 A differenza delle funzioni standard, le funzioni freccia condividono lo stesso oggetto lessicale `this` come il codice circostante che può essere usato per eliminare la necessità di soluzioni alternative come `var self = this;`.  
  
 L'esempio seguente mostra che il valore dell'oggetto `this` all'interno della funzione freccia è uguale a quello del codice circostante (fa ancora riferimento alla variabile `bob`).  
  
```JavaScript  
var bob = {  
  _name: "Bob",  
  _friends: ["Pete", "Joe", "Larry"],  
  printFriends() {  
    this._friends.forEach(f =>  
      console.log(this._name + " knows " + f));  
  }  
}  
  
// Output:  
// Bob knows Pete  
// Bob knows Joe  
// Bob knows Larry  
```  
  
 Le funzioni freccia condividono inoltre lo stesso oggetto lessicale `arguments` come codice circostante (analogamente all'oggetto `this`).  
  
<a name="Default"></a>   
## <a name="default-parameters"></a>Parametri predefiniti  
 È possibile specificare un valore predefinito per un parametro in una funzione assegnandolo a un valore iniziale. Il valore predefinito può essere un valore costante o un'espressione.  
  
> [!IMPORTANT]
>  Sono supportati solo i seguenti parametri predefiniti in [!INCLUDE[jsv12textExp](../javascript/includes/jsv12textexp-md.md)]:  
  
 Nell'esempio seguente il valore predefinito di y è 10 e il valore predefinito di z è 20. La funzione userà 10 come valore di y, a meno che il chiamante passi un valore distinto (o non definito) come secondo argomento. La funzione userà 20 come valore di z, a meno che il chiamante passi un valore distinto (o non definito) come terzo argomento.  
  
```JavaScript  
var val = 20;  
  
function f(x, y=10, z=val) {  
  return x + y + z;  
}  
  
console.log(f(3));  
console.log(f(3, 3));  
console.log(f(3, 3, 3));  
  
// Output:  
// 33  
// 26  
// 9  
```  
  
<a name="Rest"></a>   
## <a name="rest-parameters"></a>Parametri rest  
 I parametri rest, specificati dall'operatore spread `...`, consentono di convertire in una matrice gli argomenti consecutivi in una chiamata di funzione.  
  
 I parametri REST eliminano la necessità dell'oggetto `arguments`. Altri parametri sono diversi dall'oggetto `arguments` in diversi modi, ad esempio:  
  
-   Un parametro REST è un'istanza di matrice effettiva e pertanto supporta operazioni che possono essere eseguite su una matrice.  
  
-   Un parametro REST include solo gli argomenti consecutivi che non vengono passati come argomenti (denominati) separati (al contrario, l'oggetto `arguments` contiene tutti gli argomenti passati alla funzione).  
  
> [!IMPORTANT]
>  I parametri REST e l'operatore di diffusione sono supportati solo in [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)].  
  
 Nell'esempio di codice seguente "hello" e true vengono passati come valori della matrice e archiviati nel parametro y. Il parametro REST deve essere l'ultimo parametro della funzione.  
  
```JavaScript  
function f(x, ...y) {  
  // y is an array.  
  return x * y.length;  
}  
  
console.log(f(3, "hello", true));  
  
// Output:  
// 6  
  
```  
  
 Per altri usi dell'operatore spread, vedere [Operatore spread](../javascript/reference/spread-operator-decrement-dot-dot-dot-javascript.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti sul linguaggio JavaScript](../javascript/javascript-language-reference.md)