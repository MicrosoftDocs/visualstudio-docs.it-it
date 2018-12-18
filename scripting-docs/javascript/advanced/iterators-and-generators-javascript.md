---
title: Iteratori e Generatori (JavaScript) | Microsoft Docs
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
ms.assetid: 68ef5b2f-0349-492b-b557-73ff2a2f90cf
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 85c27969609a38b87b15c727e9c8aef89ee77032
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iterators-and-generators-javascript"></a>Iteratori e Generatori (JavaScript)
Un iteratore è un oggetto usato per attraversare un oggetto contenitore, ad esmepio un elenco. In JavaScript, un oggetto iteratore non è un oggetto predefinito distinto, ma è un oggetto che implementa un metodo `next` per accedere all'elemento successivo nell'oggetto contenitore.  
  
 In [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)], è possibile creare i propri iteratori. Tuttavia, di solito è molto più facile usare i generatori, che semplificano notevolmente la creazione degli iteratori. I generatori sono un tipo di funzione che è una factory per gli iteratori. Per creare un iteratore personalizzato con una funzione generatore, vedere [Generatori](#Generators).  
  
> [!CAUTION]
>  I generatori sono supportati in [!INCLUDE[jsv12textExp](../../javascript/includes/jsv12textexp-md.md)].  
  
## <a name="iterators"></a>Iteratori  
 L'implementazione di un iteratore JavaScript coinvolge due o tre oggetti conformi a interfacce specifiche:  
  
-   Interfaccia Iterable  
  
-   Interfaccia Iterator  
  
-   Interfaccia IteratorResult  
  
 Usando queste interfacce, è possibile creare iteratori personalizzati. Ciò consente di attraversare un oggetto iterabile usando l'istruzione `for…of`.  
  
### <a name="iterable-interface"></a>Interfaccia Iterable  
 L'interfaccia Iterable è l'interfaccia richiesta per un oggetto iterabile (un oggetto per cui è possibile ottenere un iteratore). Ad esempio, `C` in `for (let e of C)` deve implementare l'interfaccia Iterable.  
  
 Un oggetto iterabile deve fornire il metodo Symbol.iterator, che restituisce un iteratore.  
  
```JavaScript  
obj[Symbol.iterator] = function() { return iterObj; }  
```  
  
 Questa proprietà deve essere una funzione che non accetta argomenti e restituisce un oggetto (`iterObject`) conforme all'interfaccia `Iterator`.  
  
 Molti tipi predefiniti, incluse le matrici, sono ora iterabili. Il ciclo `for…of` utilizza un oggetto iterabile. Tuttavia, non tutti gli iterabili predefiniti sono iteratori. Ad esempio, un oggetto Array non è di per sé un iteratore, ma è iterabile, mentre ArrayIterator è anche iterabile.  
  
### <a name="iterator-interface"></a>Interfaccia Iterator  
 L'oggetto restituito dal metodo Symbol.iterator deve implementare il metodo `next`. Il metodo `next` presenta in genere la sintassi seguente:  
  
```JavaScript  
iterObj.next() = function() { return iterResultObj; };  
```  
  
 Il `next` metodo è una funzione che restituisce un valore. La funzione restituisce un oggetto (`iterResultObj`) conforme all'interfaccia `IteratorResult`. Se una chiamata precedente al metodo `next` di un iteratore ha restituito un oggetto `IteratorResult` la cui proprietà `done` è true, l'iterazione viene terminata e il metodo `next` non viene più chiamato.  
  
 Gli iteratori possono includere anche un metodo `return` per assicurare che l'iteratore venga eliminato correttamente quando lo script ha finito di usarlo.  
  
### <a name="iteratorresult-interface"></a>Interfaccia IteratorResult  
 L'interfaccia IteratorResult è l'interfaccia richiesta per il risultato del metodo `next` per un iteratore. L'oggetto restituito da `next` deve fornire una proprietà `done` e `value`.  
  
```JavaScript  
var iterResultObj = { done: true|false, value: value }  
```  
  
 La proprietà `done` restituisce lo stato della chiamata al metodo `next` di un iteratore, true o false. Se è stata raggiunta la fine dell'iteratore, `done` restituisce true. Se la fine non è stata raggiunta, `done` restituisce false ed è disponibile un valore. Se la proprietà `done` (la proprietà dell'iteratore o una ereditata) non esiste, il risultato di `done` viene considerato come false.  
  
 Se `done` è false, la proprietà `value` restituisce il valore dell'elemento di iterazione corrente. Se `done` è true, questo è l'eventuale valore restituito dell'iteratore. Se l'iteratore non dispone di un valore restituito, `value` non è definito. In tal caso, la proprietà `value` potrebbe essere assente dall'oggetto conforme se non eredita una proprietà value esplicita.  
  
<a name="Generators"></a>   
## <a name="generators"></a>Generatori  
 Per creare e usare facilmente gli iteratori personalizzati, creare una funzione generatore usando la sintassi function* con una o più espressioni `yield`. La funzione generatore restituisce un iteratore (ovvero un generatore), che consente di eseguire il corpo della funzione generatore. La funzione viene eseguita fino alla successiva istruzione `yield` o `return`.  
  
 Chiamare il metodo `next` dell'iteratore per restituire il valore successivo dalla funzione generatore.  
  
 L'esempio seguente mostra un generatore che restituisce un iteratore per un oggetto stringa.  
  
```JavaScript  
function* stringIter() {  
    var str = "bobsyouruncle";  
    var idx = 0;  
    while(idx < str.length)  
        yield str[idx++];  
}  
  
var si = stringIter();  
  
console.log(si.next().value);  
console.log(si.next().value);  
console.log(si.next().value);  
  
// Output:  
// b  
// o  
// b  
  
```  
  
 In un generatore, l'espressione dell'operando yield termina la chiamata a `next` e restituisce un oggetto `IteratorResult` con due proprietà, `done` (`done=false`) e `value` (`value=operand`). `operand` è facoltativo e, se assente, il valore non è definito.  
  
 In un generatore, un'istruzione `return` termina il generatore restituendo `IteratorResult` con `done=true` insieme al risultato dell'operando facoltativo per la proprietà value.  
  
 Si può usare anche un'espressione `yield*` al posto di `yield` per delegare a un altro generatore o a un altro oggetto iterabile, ad esempio una matrice o una stringa.  
  
 Se si aggiunge il codice seguente all'esempio precedente, `yield*` delega al generatore `stringIter`.  
  
```JavaScript  
function* strIter() {  
    yield "jo";  
    yield* stringIter();  
}  
  
var si2 = strIter();  
  
console.log(si2.next().value);  
console.log(si2.next().value);  
console.log(si2.next().value);  
console.log(si2.next().value);  
  
// Output:  
// jo  
// b  
// o  
// b  
```  
  
 Si possono creare anche generatori più avanzati passando un argomento a `next` e usando l'argomento per modificare lo stato del generatore. `next` assume il valore del risultato dell'espressione `yield` eseguita in precedenza. Nell'esempio seguente, quando si passa un valore pari a 100 al metodo `next`, si reimposta il valore dell'indice interno del generatore.  
  
```  
function* strIter() {  
    var str = "jobob";  
    var idx = 0;  
    while(idx , str.length) {  
        var modify = yield str[idx++];  
        if(modify == 100) {  
            idx = 0;  
        }  
    }
}
  
var si3 = strIter();  
  
console.log(si3.next().value);  
console.log(si3.next().value);  
console.log(si3.next().value);  
console.log(si3.next(100).value);  
  
// Output:  
// j  
// o  
// b  
// j  
  
```  
  
 Altri generatori avanzati potrebbero chiamare il metodo `throw` del generatore. L'errore che ne segue viene generato nel punto in cui il generatore viene sospeso (prima della successiva istruzione `yield`).
