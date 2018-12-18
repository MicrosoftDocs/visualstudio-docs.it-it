---
title: Tipi di dati (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Boolean data type, supported data types
ms.assetid: c7a6bd3a-4b1c-4dbe-8505-106dbf483b41
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aa3a0e4cdbb25019758f89958afdf06c11f01a34
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="data-types-javascript"></a>Tipi di dati (JavaScript)
In [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] esistono tre tipi di dati primari, due tipi di dati compositi e due tipi di dati speciali.  
  
## <a name="primary-data-types"></a>Tipi di dati primari  
 I tipi di dati primari (primitivi) sono:  
  
-   String  
  
-   Number  
  
-   Booleano  
  
## <a name="composite-data-types"></a>Tipi di dati compositi  
 I tipi di dati compositi (riferimenti) sono:  
  
-   Oggetto  
  
-   Matrice  
  
## <a name="special-data-types"></a>Tipi di dati speciali  
 I tipi di dati speciali sono:  
  
-   Null  
  
-   Undefined  
  
## <a name="string-data-type"></a>Tipo di dati String  
 Un valore stringa è una catena di zero o più caratteri Unicode (lettere, cifre e segni di punteggiatura). Il tipo di dati String viene usato per rappresentare testo in [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]. I valori letterali stringa vengono inseriti negli script racchiudendoli tra virgolette singole o doppie. Le virgolette doppie possono essere inserite in stringhe racchiuse tra virgolette singole e le virgolette singole possono essere inserite in stringhe racchiuse tra virgolette doppie. Di seguito sono riportati alcuni esempi di stringhe:  
  
```JavaScript  
"Happy am I; from care I'm free!"  
'"Avast, ye lubbers!" roared the technician.'   
"45"  
'c'  
```  
  
 Si noti che [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] non include un tipo che consente di rappresentare un carattere singolo. Per rappresentare un carattere singolo in [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] è necessario creare una stringa costituita da un solo carattere. Una stringa che contiene zero caratteri ("") è una stringa vuota (a lunghezza zero).  
  
 In [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] sono disponibili sequenze di escape che possono essere incluse nelle stringhe per creare caratteri che non è possibile digitare direttamente. Ad esempio, `\t` specifica un carattere di tabulazione. Per altre informazioni, vedere [Caratteri speciali](../javascript/advanced/special-characters-javascript.md).  
  
## <a name="number-data-type"></a>Tipo di dati Number  
 In [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] non viene fatta distinzione tra valori interi e valori a virgola mobile; un numero [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] può essere di entrambi i tipi (internamente [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] rappresenta tutti i numeri come valori a virgola mobile).  
  
### <a name="integer-values"></a>Valori Integer  
 I valori interi possono essere numeri interi positivi, numeri interi negativi e 0. Possono essere rappresentati in base 10 (decimale), in base 16 (esadecimale) e in base 8 (ottale). La maggior parte dei numeri in [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] vengono scritti in formato decimale.  
  
 I numeri interi esadecimali ("hex") sono indicati dal prefisso iniziale "0x" (zero e x&#124;X). Possono contenere solo cifre da 0 a 9 e lettere da A a F (maiuscole o minuscole). Le lettere da A a F vengono usate per rappresentare, come cifre singole, i numeri da 10 a 15 in base 10. Ovvero, 0xF equivale a 15 e 0x10 equivale a 16.  
  
 I numeri interi ottali sono indicati da un prefisso con uno "0" (zero) iniziale. Possono contenere solo le cifre da 0 a 7. Un numero con uno "0" iniziale che contiene le cifre "8" e/o "9" viene interpretato come numero decimale.  
  
 Sia i numeri esadecimali che i numeri ottali possono essere negativi, ma non possono avere una parte decimale ed essere scritti in notazione scientifica (esponenziale).  
  
> [!NOTE]
>  A partire da [!INCLUDE[jsv9text](../javascript/includes/jsv9text-md.md)], la [funzione parseInt](../javascript/reference/parseint-function-javascript.md) non considera una stringa con prefisso "0" come ottale. Tuttavia, quando non viene usata la funzione `parseInt`, le stringhe con prefisso "0" possono ancora essere interpretate come ottali.  
  
### <a name="floating-point-values"></a>Valori a virgola mobile  
 I valori a virgola mobile possono essere numeri interi con una parte decimale. Inoltre, possono essere espressi in notazione scientifica. Ovvero, una "e" maiuscola o minuscola viene usata per rappresentare "10 elevato alla potenza di". [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] rappresenta i numeri usando lo standard a virgola mobile IEEE 754 a 8 byte per la rappresentazione numerica. Ciò significa che è possibile scrivere numeri fino a un massimo di 1.79769x10<sup>308</sup> e un minimo di 5x10<sup>-324</sup>. Un numero che contiene un separatore decimale e ha un singolo "0" prima del separatore decimale viene interpretato come numero decimale a virgola mobile.  
  
 Si noti che un numero che inizia con "0x" o "00" e contiene un separatore decimale genera un errore. Di seguito sono riportati alcuni esempi di numeri [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
|Number|Descrizione|Equivalente decimale|  
|------------|-----------------|------------------------|  
|.0001, 0.0001, 1e-4, 1.0e-4|Quattro numeri a virgola mobile equivalenti.|0.0001|  
|3.45e2|Numero a virgola mobile.|345|  
|45|Intero.|45|  
|0378|Intero. Sebbene sia simile a un numero ottale (inizia con zero), 8 non è una cifra ottale valida, pertanto il numero viene considerato come numero decimale.|378|  
|0377|Intero ottale. Si noti che sebbene sembri essere un'unità in meno rispetto al numero sopra, il valore effettivo è diverso.|255|  
|0.0001|Un numero a virgola mobile. Anche se inizia con zero, non è un numero ottale perché contiene un separatore decimale.|0.0001|  
|00.0001|Si tratta di un errore. I due zero iniziali indicano un numero ottale, ma per i numeri ottali non è consentito un componente decimale.|N/D (errore del compilatore)|  
|0Xff|Intero esadecimale.|255|  
|0x37CF|Intero esadecimale.|14287|  
|0x3e7|Intero esadecimale. Si noti che 'e' non è considerato come elevamento a potenza.|999|  
|0x3.45e2|Si tratta di un errore. I numeri esadecimali non possono contenere parti decimali.|N/D (errore del compilatore)|  
  
 Inoltre, [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] contiene numeri con valori speciali. Questi sono:  
  
-   NaN (non un numero). Viene usato quando viene eseguita un'operazione matematica su dati non appropriati, ad esempio stringhe o il valore non definito  
  
-   Infinito positivo. Viene usato quando un numero positivo è troppo grande per essere rappresentato in [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]  
  
-   Infinito negativo. Viene usato quando un numero negativo è troppo grande per essere rappresentato in [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]  
  
-   0 positivo e negativo. [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] riconosce la differenza tra zero positivo e negativo.  
  
## <a name="boolean-data-type"></a>Tipo di dati booleani  
 Mentre i tipi di dati String e Number possono avere potenzialmente un numero illimitato di valori diversi, il tipo di dati Boolean può avere solo due valori. Si tratta dei valori letterali `true` e `false`. Un valore booleano è un valore di verità: specifica se una condizione è vera o meno.  
  
 I confronti eseguiti negli script hanno sempre un risultato booleano. Si consideri la riga di codice [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] seguente.  
  
```JavaScript  
y = (x == 2000);  
```  
  
 In questo caso, il valore della variabile `x` viene confrontato con il numero 2000. Se il valore è uguale, il risultato del confronto è il valore booleano **true** che viene assegnato alla variabile `y`. Se `x` non è uguale a 2000, il risultato del confronto è il valore booleano `false`.  
  
 I valori booleani sono particolarmente utili nelle strutture di controllo. Il codice seguente esegue un confronto che crea un valore booleano direttamente con un'istruzione in cui viene usato. Si consideri l'esempio di codice [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] seguente.  
  
```JavaScript  
if (x == 2000) {  
    z = z + 1;  
}  
else {  
    x = x + 1;  
}  
```  
  
 L'istruzione `if/else` in [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] esegue un'azione se un valore booleano è `true` (`z = z + 1`), e un'altra azione se il valore booleano è `false` (`x = x + 1`).  
  
 È possibile usare qualsiasi espressione come espressione di confronto. Qualsiasi espressione che restituisce una stringa 0, Null, indefinita o vuota viene interpretata come `false`. Un'espressione che restituisce qualsiasi altro valore viene interpretata come `true`. Ad esempio, è possibile usare un'espressione come la seguente:  
  
```JavaScript  
// This may not do what you expect. See below!  
if (x = y + z)   
```  
  
 Si noti che la riga precedente non controlla se `x` è uguale a `y + z` poiché viene usato un solo segno di uguale (l'operatore di assegnazione). Il codice precedente, invece, assegna il valore di `y + z` alla variabile `x` e quindi controlla se il risultato dell'intera espressione (il valore di `x`) è uguale a zero. Per verificare se `x` è uguale a `y + z` è necessario usare il codice seguente.  
  
```JavaScript  
// This is different from the code above!  
if (x == y + z)   
```  
  
 Per altre informazioni sui confronti, vedere [Controllo del flusso di programma](../javascript/controlling-program-flow-javascript.md).  
  
## <a name="the-null-data-type"></a>Il tipo di dati NULL  
 Il tipo di dati `null` ha un solo valore in [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]: null. La parola chiave `null` non può essere usata come nome di una funzione o variabile.  
  
 Una variabile che contiene `null` non contiene alcun numero, stringa, valore booleano, matrice o oggetto valido. È possibile cancellare il contenuto di una variabile senza eliminare la variabile assegnando alla variabile il valore `null`.  
  
 Si noti che in [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] `null` non corrisponde 0, come avviene in C e C++. Si noti anche che l'operatore `typeof` in [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] riporta i valori `null` come valori di tipo `Object`, non di tipo `null`. Questo comportamento potenzialmente disorientante è finalizzato a garantire la compatibilità con le versioni precedenti.  
  
## <a name="the-undefined-data-type"></a>Il tipo di dati non definito  
 Il valore `undefined` viene restituito quando viene usata una proprietà oggetto non esistente o una variabile dichiarata ma a cui non è mai stato assegnato un valore.  
  
 È possibile verificare l'esistenza di una variabile confrontandola con `undefined`, sebbene sia possibile verificare se il tipo è `undefined` confrontando il tipo della variabile con la stringa "undefined". L'esempio seguente illustra come individuare se la variabile `x` è stata dichiarata:  
  
```JavaScript  
  
var x;  
  
// This method works.  
if (x == undefined) {  
    document.write("comparing x to undefined <br/>");  
}  
.  
// This method doesn't work - you must check for the string "undefined".  
if (typeof(x) == undefined) {  
    document.write("comparing the type of x to undefined <br/>");  
}  
// This method does work.   
if (typeof(x) == "undefined") {  
    document.write("comparing the type of x to the string 'undefined'");  
}  
  
// Output:   
// comparing x to undefined   
// comparing the type of x to the string 'undefined'  
  
```  
  
 È anche possibile confrontare il valore non definito con `null`. Il confronto restituisce `true` se la proprietà `someObject.prop` è `null` o se la proprietà `someObject.prop` non esiste.  
  
```JavaScript  
someObject.prop == null;  
```  
  
 Per verificare l'esistenza di una proprietà oggetto, è possibile usare l'operatore **in**:  
  
```JavaScript  
if ("prop" in someObject)  
    // someObject has the property 'prop'  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetti e matrici](../javascript/objects-and-arrays-javascript.md)   
 [Operatore typeof](../javascript/reference/typeof-operator-decrementjavascript.md)