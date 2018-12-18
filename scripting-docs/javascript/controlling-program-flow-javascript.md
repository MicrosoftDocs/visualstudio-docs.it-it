---
title: Controllo del flusso di programma (JavaScript) | Microsoft Docs
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
- Boolean values, program flow
- continue statement
- break statement
- control flow, about control flow
ms.assetid: 4ef58c82-e5d6-4b09-9458-cf0aa3b39bf5
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 20c256d26c6991067d7c25c0c835eda6e5e5aac6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="controlling-program-flow-javascript"></a>Controllo del flusso di programma (JavaScript)
In genere, le istruzioni in uno script di [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] vengono eseguite una dopo l'altra, nell'ordine di scrittura. Questo tipo di esecuzione viene definita sequenziale e rappresenta la direzione predefinita del flusso di programma.  
  
 Un'alternativa all'esecuzione sequenziale trasferisce il flusso di programma a un'altra parte dello script. In tal modo, invece della successiva istruzione della sequenza viene eseguita un'altra istruzione.  
  
 Per rendere utile uno script, il trasferimento del controllo deve essere eseguito in modo logico. Il trasferimento del controllo del programma si basa su una decisione il cui risultato è un'istruzione (che restituisce un valore booleano **true** o **false**). Una volta creata un'espressione, è possibile verificare se il risultato restituito è di tipo true. Esistono a tale scopo due tipi principali di strutture del programma.  
  
 Il primo tipo è la struttura di selezione utilizzata per specificare percorsi alternativi del flusso di programma, creando un collegamento nel programma stesso. In [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] sono disponibili quattro strutture di selezione:  
  
-   la struttura di selezione singola (**if**),  
  
-   la struttura di selezione doppia (**if/else**),  
  
-   l'operatore ternario in linea `?:`,  
  
-   la struttura di selezione multipla (`switch`).  
  
 Il secondo tipo di struttura di controllo del programma è la struttura di ripetizione utilizzata per specificare che un'azione deve essere ripetuta se alcune condizioni rimangono true. Quando infatti le condizioni dell'istruzione di controllo vengono soddisfatte, in genere dopo un numero specifico di iterazioni, il controllo passa all'istruzione successiva oltre la struttura di ripetizione. In [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] sono disponibili quattro strutture di ripetizione:  
  
-   l'espressione viene verificata all'inizio del ciclo (`while`),  
  
-   l'espressione viene verificata alla fine del ciclo (**do/while**),  
  
-   opera su ogni proprietà di un oggetto (**for/in**).  
  
-   la ripetizione è controllata da un contatore (**for**).  
  
 Si possono creare script piuttosto complessi annidando e sovrapponendo strutture di controllo di selezione e di ripetizione.  
  
 Una terza forma del flusso di programma strutturato è rappresentata dalla gestione delle eccezioni, non analizzata in questo documento.  
  
## <a name="using-conditional-statements"></a>Utilizzo di istruzioni condizionali  
 In [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] sono supportate le istruzioni condizionali **if** e [if...else](../javascript/reference/if-dot-dot-dot-else-statement-javascript.md). Nelle istruzioni **if** viene verificata una condizione e, se la condizione supera il test, viene eseguito il relativo codice [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]. Nell'istruzione `if...else` viene eseguito un codice diverso se la condizione non supera il test. Nella sua forma più semplice, un'istruzione **if** può essere inclusa in una sola riga di codice. Vengono tuttavia usate più spesso istruzioni **if** e `if...else` su più righe.  
  
 Negli esempi riportati di seguito viene illustrata la sintassi che è possibile usare per le istruzioni **if** e `if...else`. Il primo esempio illustra il tipo più semplice di test booleano. L'istruzione **if**, o il blocco di istruzioni che la segue, verrà eseguita solo se il valore dell'elemento tra parentesi è **true** o può essere assegnato forzatamente.  
  
```JavaScript  
function GetReaction(newShip, color, texture, dayOfWeek)  
{  
   // The test succeeds if the newShip Boolean value is true.  
   if (newShip)  
   {  
      return "Champagne Bottle";  
   }  
  
   // The test succeeds if both conditions are true.  
   if (color == "deep yellow" && texture == "large and small wrinkles")  
   {  
      return "Is it a crenshaw melon?";  
   }  
  
   // The test succeeds if either condition is true.  
   if ((dayOfWeek == "Saturday") || (dayOfWeek == "Sunday"))  
   {  
      return "I'm off to the beach!";  
   }  
   else  
   {  
      return "I'm going to work.";  
   }  
}  
  
var reaction = GetReaction(false, "deep yellow", "smooth", "Sunday");  
document.write(reaction);  
  
// Output: I'm off to the beach!  
```  
  
## <a name="conditional-operator"></a>Operatore condizionale  
 In [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] viene inoltre supportata una forma condizionale implicita. Essa usa un punto interrogativo dopo la condizione da verificare, invece della parola **if** prima della condizione. Specifica inoltre due alternative, una da utilizzare se la condizione viene soddisfatta e una in caso contrario. I due punti devono separare queste alternative.  
  
```JavaScript  
var AMorPM = (theHour >= 12) ? "PM" : "AM";  
```  
  
 Se è necessario verificare più condizioni contemporaneamente e si sa che una di queste ha maggiori possibilità rispetto alle altre di essere vera o falsa, è possibile utilizzare una funzione definita "valutazione in corto circuito" per velocizzare l'esecuzione dello script. Durante una valutazione di un'espressione logica in [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] viene considerato solo il numero di sottoespressioni necessario per ottenere un risultato.  
  
 Ad esempio, se è disponibile un'espressione AND come ((x == 123) && (y == 6)), [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] controlla innanzitutto se x corrisponde a 123. Se non corrisponde, l'intera espressione non può essere true, anche se y è uguale a 6. Di conseguenza, y non verrà valutato e in [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] verrà restituito il valore **false**.  
  
 Analogamente, se solo una delle varie condizioni deve essere **true** (tramite l'operatore &#124;&#124;), il test si arresta non appena una qualsiasi condizione supera il test. Ciò è efficace se le condizioni da verificare implicano l'esecuzione di chiamate di funzione o di altre espressioni complesse. A tal fine, quando si scrivono espressioni Or, inserire per prime le condizioni il cui valore è con maggiore probabilità **true**. Quando si scrivono espressioni And, inserire per prime le condizioni il cui valore è con maggiore probabilità **false**.  
  
 Un vantaggio connesso a questo tipo di progettazione di script consiste nel fatto che **runsecond()** non verrà eseguito se **runfirst()** restituisce 0.  
  
```JavaScript  
if ((runfirst() == 0) || (runsecond() == 0)) {  
    // some code  
}  
```  
  
## <a name="using-loops"></a>Utilizzo di cicli  
 Sono disponibili metodi diversi per eseguire più volte un'istruzione o un blocco di istruzioni. In generale, l'esecuzione ripetuta viene definita *ciclo* o *iterazione*. Un'iterazione è semplicemente un'unica esecuzione di un ciclo. Viene in genere controllata da un test di una variabile, il cui valore viene modificato ogni volta che si esegue il ciclo. In [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] sono supportati quattro tipi di cicli: [for](../javascript/reference/for-statement-javascript.md), [for...in](../javascript/reference/for-dot-dot-dot-in-statement-javascript.md), [while](../javascript/reference/while-statement-javascript.md) e [do...while](../javascript/reference/do-dot-dot-dot-while-statement-javascript.md).  
  
## <a name="using-for-loops"></a>Utilizzo di cicli for  
 L'istruzione **for** specifica una variabile contatore, una condizione di test e un'operazione per l'aggiornamento del contatore. La condizione viene verificata prima di ciascuna iterazione del ciclo. Se il test ha esito positivo, il codice presente nel ciclo verrà eseguito. In caso di esito negativo, il codice presente nel ciclo non verrà eseguito e il programma continuerà dalla prima riga di codice successiva al ciclo. La variabile contatore viene aggiornata dopo ciascuna iterazione, prima che inizi l'iterazione successiva.  
  
 Se la condizione del ciclo risulta sempre falsa, il ciclo non verrà mai eseguito. Se invece risulta sempre vera, verrà eseguito un ciclo infinito. Mentre il primo caso può a volte risultare utile, si consiglia di evitare la creazione di cicli infiniti. A tale scopo, durante la scrittura di condizioni di ciclo è necessario prestare la massima attenzione.  
  
```JavaScript  
// The update expression ("icount++" in the following examples)  
// is executed at the end of the loop, after the block of  
// statements that forms the body of the loop is executed, and  
// before the condition is tested.  
  
// Set a limit of 10 on the loop.  
var howFar = 10;  
  
// Create an array called sum with 10 members, 0 through 9.  
var sum = new Array(howFar);  
sum[0] = 0;  
  
// Iterate from 0 through 9.  
var theSum = 0;  
for(var icount = 0; icount < howFar; icount++)  
{  
   theSum += icount;  
   sum[icount] = theSum;  
}  
  
// This code is not executed at all, because icount is not greater than howFar.  
var newSum = 0;  
for(var icount = 0; icount > howFar; icount++)  
{  
   newSum += icount;  
}  
  
// This is an infinite loop.  
var sum = 0;  
for(var icount = 0; icount >= 0; icount++)  
{  
   sum += icount;  
}  
```  
  
## <a name="using-forin-loops"></a>Utilizzo di cicli for...in  
 In [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] è disponibile un tipo speciale di ciclo per scorrere tutte le proprietà di un [oggetto](../javascript/objects-and-arrays-javascript.md) definite dall'utente o tutti gli elementi di una matrice. Il contatore di un ciclo `for...in` è una stringa e non un numero. Contiene il nome della proprietà corrente o l'indice dell'elemento della matrice corrente.  
  
```JavaScript  
// Create an object with some properties  
var myObject = new Object();  
myObject.name = "James";  
myObject.age = "22";  
myObject.phone = "555 1234";  
  
// Enumerate (loop through)_all the properties in the object  
for (var prop in myObject)  
{  
    // This displays "The property 'name' is James", etc.  
    document.write("The property '" + prop + "' is " + myObject[prop]);  
    // New line.  
    document.write("<br />");    
}  
```  
  
 Nonostante i cicli `for...in` siano simili ai cicli `For Each...Next` di VBScript, non funzionano in modo analogo. Il **ciclo for...in** di [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] scorre le proprietà di oggetti [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]. Il ciclo **For Each...Next** di VBScript scorre gli elementi in una raccolta. Per eseguire un ciclo nelle raccolte in [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], è necessario usare l'[oggetto Enumerator](../javascript/reference/enumerator-object-javascript.md) o, se presente, il metodo `forEach` dell'oggetto raccolta. Sebbene alcuni oggetti, ad esempio quelli in Internet Explorer, supportino sia il ciclo **For Each...Next** di VBScript sia il ciclo **for...in** di [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], la maggior parte degli oggetti non li supportano.  
  
## <a name="using-while-loops"></a>Utilizzo di cicli while  
 Un ciclo `while` è simile a un ciclo **for**. La differenza è data dal fatto che un ciclo `while` non include una variabile contatore predefinita o un'espressione di aggiornamento. Per controllare l'esecuzione ripetuta di un'istruzione o di un blocco di istruzioni con una regola più complessa della semplice esecuzione del codice per un numero specificato di volte, utilizzare un ciclo `while`. Nell'esempio seguente viene utilizzato il modello a oggetti di Internet Explorer e un ciclo `while` per porre all'utente una semplice domanda.  
  
```JavaScript  
var x = 0;  
while ((x != 5) && (x != null))  
{  
    x = window.prompt("What is my favorite number?", x);  
}  
  
if (x == null)  
    window.alert("You gave up!");  
else  
    window.alert("Correct answer!");  
```  
  
> [!NOTE]
>  I cicli `while`, non includendo variabili contatore predefinite esplicite, possono generare cicli infiniti con maggiore probabilità rispetto agli altri tipi di cicli. Poiché inoltre non è sempre possibile identificare in modo rapido la posizione e il momento in cui la condizione del ciclo verrà aggiornata, può facilmente accadere di scrivere inavvertitamente cicli `while` in cui la condizione non viene mai aggiornata. Durante la scrittura di cicli `while` è pertanto necessario prestare particolare cautela.  
  
 Come notato in precedenza, in [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] esiste anche un ciclo **do...while** simile al ciclo while, con l'eccezione che viene sempre eseguito almeno una volta, poiché la condizione viene verificata alla fine del ciclo, anziché all'inizio. È possibile, ad esempio, riscrivere il ciclo sopra riportato come segue:  
  
```JavaScript  
var x = 0;  
do  
{  
    x = window.prompt("What is my favorite number?", x);  
} while ((x != 5) && (x != null));  
  
if (x == null)  
    window.alert("You gave up!");  
else  
    window.alert("Correct answer!");  
```  
  
## <a name="using-break-and-continue-statements"></a>Utilizzo delle istruzioni break e continue  
 In [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] l'istruzione [break](../javascript/reference/break-statement-javascript.md) viene usata per arrestare l'esecuzione di un ciclo quando viene soddisfatta una determinata condizione. Si noti che l'istruzione **break** viene usata anche per la chiusura di un blocco `switch`. L'istruzione [continue](../javascript/reference/continue-statement-javascript.md) consente di passare immediatamente all'iterazione successiva, ignorando il resto del blocco di codice e aggiornando la variabile contatore nel caso di cicli **for** o `for...in`.  
  
 L'esempio seguente si basa sull'esempio precedente per l'uso delle istruzioni **break** e **continue** per controllare il ciclo.  
  
```JavaScript  
var x = 0;  
do  
{  
    x = window.prompt("What is my favorite number?", x);  
  
    // Did the user cancel? If so, break out of the loop  
    if (x == null)  
        break;  
  
    // Did they enter a number?  
    // If so, no need to ask them to enter a number.  
    if (Number(x) == x)  
        continue;  
  
    // Ask user to only enter in numbers  
    window.alert("Please only enter in numbers!");  
  
} while (x != 5)  
  
if (x != 5)  
    window.alert("You gave up!");  
else  
    window.alert("Correct answer!");  
```