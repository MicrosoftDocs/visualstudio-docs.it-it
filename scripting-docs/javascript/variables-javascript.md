---
title: Variabili, JavaScript | Microsoft Docs
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
- coercion
- case sensitivity, JavaScript variable name
ms.assetid: 12a450e5-4818-4a09-9878-cd7c6cd2a248
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f30946899ad35286dfb1e786cf903d58f5c98cb6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="variables-javascript"></a>Variabili (JavaScript)
In [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], una variabile contiene un valore, ad esempio "hello" o 5. Quando si usa la variabile, si fa riferimento ai dati che rappresenta, ad esempio `NumberOfDaysLeft = EndDate - TodaysDate`.  
  
 Si usano le variabili per archiviare, recuperare e modificare i valori visualizzati nel codice. Tentare di assegnare alle variabili dei nomi significativi per semplificare agli altri utenti la comprensione del funzionamento del codice.  
  
## <a name="declaring-variables"></a>Dichiarazione di variabili  
 La prima volta che una variabile viene visualizzata nello script è in occasione della sua dichiarazione. La prima indicazione della variabile la configura nella memoria, pertanto è possibile farvi riferimento in un secondo momento nello script. È necessario dichiarare le variabili prima di usarle. Eseguire questa operazione usando la parola chiave `var`.  
  
```JavaScript  
// A single declaration.  
var count;    
// Multiple declarations with a single var keyword.  
var count, amount, level;      
// Variable declaration and initialization in one statement.  
var count = 0, amount = 100;   
```  
  
 Se non si inizializza la variabile nell'istruzione `var`,prende automaticamente il valore `undefined`.  
  
## <a name="naming-variables"></a>Denominazione delle variabili  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] effettua la distinzione tra maiuscole e minuscole. Ciò significa che un nome della variabile, come ad esempio **myCounter** è diverso dal nome della variabile **MYCounter**. I nomi delle variabili possono essere di qualsiasi lunghezza. Le regole per la creazione di nomi delle variabili validi sono riportate di seguito:  
  
-   Il primo carattere deve essere una lettera ASCII (maiuscolo o minuscola), oppure un carattere di sottolineatura (_). Si noti che non è possibile usare un numero come primo carattere.  
  
-   I caratteri successivi devono essere lettere, numeri o caratteri di sottolineatura (_).  
  
-   Il nome della variabile non deve essere una [parola riservata](../javascript/reference/javascript-reserved-words.md).  
  
 Ecco alcuni esempi di nomi di variabile validi:  
  
```  
_pagecount   
Part9   
Number_Items   
```  
  
 Ecco alcuni esempi di nomi di variabile non validi:  
  
```JavaScript  
// Cannot begin with a number.   
99Balloons     
// The ampersand (&) character is not a valid character for variable names.   
Alpha&Beta   
```  
  
 Quando si desidera dichiarare una variabile e inizializzarla, ma non si desidera assegnare un valore particolare, assegnare il valore `null`. Di seguito è riportato un esempio.  
  
```JavaScript  
var bestAge = null;  
var muchTooOld = 3 * bestAge; // muchTooOld has the value 0.  
```  
  
 Se si dichiara una variabile senza assegnarle un valore, ha il valore `undefined`. Di seguito è riportato un esempio.  
  
```JavaScript  
var currentCount;  
// finalCount has the value NaN because currentCount is undefined.  
var finalCount = 1 * currentCount;   
```  
  
 Il valore `null` si comporta come il numero 0, mentre `undefined` si comporta come il valore speciale `NaN` (non un numero). Se si confronta un valore `null` e un valore `undefined`, essi risultano essere uguali.  
  
 È possibile dichiarare una variabile senza usare la parola chiave `var` nella dichiarazione, e assegnarle un valore. Questa è una dichiarazione esplicita.  
  
```JavaScript  
// The variable noStringAtAll is declared implicitly.  
noStringAtAll = "";   
```  
  
 Non e possibile usare una variabile che non è mai stata dichiarata.  
  
```JavaScript  
// Error. Length and width do not yet exist.  
var area = length * width;   
```  
  
## <a name="coercion"></a>Coercizione  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] è un linguaggio debolmente tipizzato, in opposizione a linguaggi fortemente tipizzati come C++. Ciò significa che le variabili di JavaScript non dispongono di alcun tipo predeterminato. Al contrario, il tipo di una variabile è il tipo del suo valore. Questo comportamento consente di trattare un valore come se fosse di tipo diverso.  
  
 In [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], è possibile eseguire operazioni su valori di diversi tipi senza generare un'eccezione. L'interprete [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] converte in modo implicito, o *assegna*, uno dei tipi di dati a quello degli altri, quindi esegue l'operazione. Le regole per l'assegnazione forzata della stringa, del numero e dei valori booleani sono i seguenti:  
  
-   Se si aggiunge un numero e una stringa, il numero viene assegnato a una stringa.  
  
-   Se si aggiunge un booleano e una stringa, il booleano viene assegnato a una stringa.  
  
-   Se si aggiunge un numero e un booleano, il booleano viene assegnato a un numero.  
  
 Nell'esempio seguente, un numero aggiunto a una stringa produce una stringa.  
  
```JavaScript  
var x = 2000;  
var y = "Hello";  
// The number is coerced to a string.  
x = x + y;  
document.write(x);   
  
// Output:  
// 2000Hello  
```  
  
 Le stringhe vengono automaticamente convertite in numeri equivalenti per il confronto. Per convertire esplicitamente una stringa in un intero, usare la [funzione parseInt](../javascript/reference/parseint-function-javascript.md). Per convertire esplicitamente una stringa in un numero, usare la [funzione parseFloat](../javascript/reference/parsefloat-function-javascript.md).