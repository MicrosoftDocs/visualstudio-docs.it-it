---
title: Funzione JSON. stringify (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- stringify method
ms.assetid: 0fafaf3b-c29b-46dc-b65b-ca223064a1d0
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3539bb003ed20a3ff7586e42466bf7c47165b83f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="jsonstringify-function-javascript"></a>Funzione JSON.stringify (JavaScript)
Converte un valore [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] in una stringa JSON (JavaScript Object Notation).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
JSON.stringify(  
value [, replacer] [, space])  
```  
  
## <a name="parameters"></a>Parametri  
 `value`  
 Obbligatorio. Valore [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], in genere un oggetto o una matrice, da convertire.  
  
 `replacer`  
 Facoltativo. Funzione o matrice che trasforma i risultati.  
  
 Se `replacer` è una funzione, `JSON.stringify` chiama la funzione passando la chiave e il valore di ciascun membro. Il valore restituito viene utilizzato invece del valore originale. Se la funzione restituisce `undefined`, il membro viene escluso. La chiave per l'oggetto radice è una stringa vuota: "".  
  
 Se `replacer` è una matrice, verranno convertiti solo i membri con i valori della chiave nella matrice. I membri vengono convertiti in base all'ordine delle chiavi nella matrice. La matrice `replacer` viene ignorata se anche l'argomento `value` è una matrice.  
  
 `space`  
 Facoltativo. Aggiunge rientri, spazi vuoti e caratteri di interruzione di riga al testo JSON del valore restituito per semplificare la lettura.  
  
 Se `space` viene omesso, il testo del valore restituito viene generato senza alcuno spazio vuoto aggiuntivo.  
  
 Se `space` è un numero, al testo del valore restituito viene applicato un rientro del numero specificato di spazi vuoti in ogni livello. Se `space` è maggiore di 10, al testo viene applicato un rientro di 10 spazi.  
  
 Se `space` è una stringa non vuota, ad esempio '\t', al testo del valore restituito viene applicato un rientro dei caratteri presenti nella stringa in ogni livello.  
  
 Se `space` è una stringa di lunghezza superiore a 10 caratteri, vengono utilizzati i primi 10.  
  
## <a name="return-value"></a>Valore restituito  
 Stringa contenente il testo JSON.  
  
## <a name="exceptions"></a>Eccezioni  
  
|Eccezione|Condizione|  
|---------------|---------------|  
|[Argomento Replacer non valido](../../javascript/misc/invalid-replacer-argument.md)|L'argomento `replacer` non è una funzione o una matrice.|  
|[Riferimento circolare nell'argomento Value non supportato](../../javascript/misc/circular-reference-in-value-argument-not-supported.md)|L'argomento `value` contiene un riferimento circolare.|  
  
## <a name="remarks"></a>Note  
 Se per `value` è disponibile un metodo `toJSON`, la funzione `JSON.stringify` utilizza il valore restituito del metodo. Se il valore restituito del metodo `toJSON` è `undefined`, il membro non viene convertito. Ciò consente a un oggetto di determinare la propria rappresentazione JSON.  
  
 I valori senza rappresentazioni JSON, come `undefined`, non verranno convertiti. Negli oggetti verranno eliminati, mentre nelle matrici verranno sostituiti con null.  
  
 I valori stringa iniziano e terminano con le virgolette. Tutti i caratteri Unicode possono essere racchiusi tra virgolette eccetto i caratteri che devono essere preceduti da una barra rovesciata come carattere di escape. I seguenti caratteri devono essere preceduti da una barra rovesciata:  
  
-   Virgolette doppie (")  
  
-   Barra rovesciata (\\)  
  
-   Backspace (b)  
  
-   Avanzamento carta (f)  
  
-   Nuova riga (n)  
  
-   Ritorno a capo (r)  
  
-   Tabulazione orizzontale (t)  
  
-   Quattro cifre esadecimali (uhhhh)  
  
## <a name="order-of-execution"></a>Ordine di esecuzione  
 Durante il processo di serializzazione, se un metodo `toJSON` esiste per l'argomento `value`, `JSON.stringify` chiama innanzitutto il metodo `toJSON`. Se non esiste, si utilizza il valore originale. Successivamente, se viene fornito un argomento `replacer`, il valore (valore originale o valore restituito `toJSON`) viene sostituito con il valore restituito dell'argomento `replacer`. Infine, al valore vengono aggiunti spazi vuoti in base all'argomento `space` facoltativo per generare il testo JSON finale.  
  
## <a name="example"></a>Esempio  
 In questo esempio viene utilizzato `JSON.stringify` per convertire l'oggetto `contact` in testo JSON. La matrice `memberfilter` viene definita in modo da convertire solo i membri `surname` e `phone`. Il membro `firstname` viene omesso.  
  
```JavaScript  
var contact = new Object();  
contact.firstname = "Jesper";  
contact.surname = "Aaberg";  
contact.phone = ["555-0100", "555-0120"];  
  
var memberfilter = new Array();  
memberfilter[0] = "surname";  
memberfilter[1] = "phone";  
var jsonText = JSON.stringify(contact, memberfilter, "\t");  
document.write(jsonText);  
// Output:   
// { "surname": "Aaberg", "phone": [ "555-0100", "555-0120" ] }  
```  
  
## <a name="example"></a>Esempio  
 In questo esempio viene utilizzato `JSON.stringify` con una matrice. La funzione `replaceToUpper` converte ogni stringa della matrice in maiuscolo.  
  
```JavaScript  
var continents = new Array();  
continents[0] = "Europe";  
continents[1] = "Asia";  
continents[2] = "Australia";  
continents[3] = "Antarctica";  
continents[4] = "North America";  
continents[5] = "South America";  
continents[6] = "Africa";  
  
var jsonText = JSON.stringify(continents, replaceToUpper);  
  
function replaceToUpper(key, value) {  
    return value.toString().toUpperCase();  
}  
  
//Output:  
// "EUROPE,ASIA,AUSTRALIA,ANTARCTICA,NORTH AMERICA,SOUTH AMERICA,AFRICA"  
  
```  
  
## <a name="example"></a>Esempio  
 In questo esempio viene utilizzato il metodo `toJSON` per convertire valori stringa in maiuscolo.  
  
```JavaScript  
var contact = new Object();   
contact.firstname = "Jesper";  
contact.surname = "Aaberg";  
contact.phone = ["555-0100", "555-0120"];  
  
contact.toJSON = function(key)  
 {  
    var replacement = new Object();  
    for (var val in this)  
    {  
        if (typeof (this[val]) === 'string')  
            replacement[val] = this[val].toUpperCase();  
        else  
            replacement[val] = this[val]  
    }  
    return replacement;  
};  
  
var jsonText = JSON.stringify(contact);  
document.write(jsonText);  
  
// Output:  
{"firstname":"JESPER","surname":"AABERG","phone":["555-0100","555-0120"]}  
  
'{"firstname":"JESPER","surname":"AABERG","phone":["555-0100","555-0120"]}'  
*/  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv58](../../javascript/reference/includes/jsv58-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione JSON. Parse](../../javascript/reference/json-parse-function-javascript.md)   
 [Metodo toJSON (Date)](../../javascript/reference/tojson-method-date-javascript.md)   
 [Lettore di feed app di esempio (Windows Store)](http://code.msdn.microsoft.com/Feed-reader-sample-99d68cf8)