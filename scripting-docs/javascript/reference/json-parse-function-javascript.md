---
title: Funzione JSON. Parse (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- JSON.parse
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- parse JSON method
- JSON.parse method
ms.assetid: 20f00d31-5ab5-4c3c-ab49-2534fc39a9b4
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 519fc733fd42a194fbd7335127ddf9bcf0bdc220
ms.sourcegitcommit: 11740fed01cc602252ef698aaa11c07987b00570
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/12/2018
---
# <a name="jsonparse-function-javascript"></a>Funzione JSON.parse (JavaScript)
Converte una stringa JSON (JavaScript Object Notation) in un oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
JSON.parse(text [, reviver])  
```  
  
## <a name="parameters"></a>Parametri  
 `text`  
 Obbligatorio. Stringa JSON valida.  
  
 `reviver`  
 Facoltativo. Funzione che trasforma i risultati. Questa funzione viene chiamata per ogni membro dell'oggetto. Se un membro contiene oggetti annidati, questi ultimi vengono trasformati prima dell'oggetto padre. Per ciascun membro, si verifica quanto segue:  
  
-   Se `reviver` restituisce un valore valido, il valore del membro viene sostituito con il valore trasformato.  
  
-   Se `reviver` restituisce lo stesso valore che ha ricevuto, il valore del membro non viene modificato.  
  
-   Se `reviver` restituisce `null` o `undefined`, il membro viene eliminato.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto o matrice.  
  
## <a name="exceptions"></a>Eccezioni  
 Se questa funzione provoca un errore del parser di [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] , ad esempio "SCRIPT1014: Carattere non valido", il testo di input non è conforme alla sintassi JSON. Per correggere l'errore, effettuare una delle operazioni seguenti:  
  
-   Modificare l'argomento `text` per conformarsi alla sintassi JSON. Per altre informazioni, vedere [Notazione della sintassi BNF](http://go.microsoft.com/fwlink/?LinkId=125203) degli oggetti JSON.  
  
     Se ad esempio la risposta è in formato JSONP anziché JSON pure, provare questo codice nell'oggetto della risposta:  
  
    ```JavaScript  
    var fixedResponse = response.responseText.replace(/\\'/g, "'");  
    var jsonObj = JSON.parse(fixedResponse);  
    ```  
  
-   Assicurarsi che l'argomento `text` sia stato serializzato da un'implementazione conforme a JSON come `JSON.stringify`.  
  
-   Eseguire il `text` argomento in un validator JSON come [JSLint](http://www.jslint.com/) o [JSON in formato CSV](https://json-csv.com) per identificare gli errori di sintassi.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente si utilizza `JSON.parse` per convertire una stringa JSON in un oggetto.  
  
```JavaScript  
var jsontext = '{"firstname":"Jesper","surname":"Aaberg","phone":["555-0100","555-0120"]}';  
var contact = JSON.parse(jsontext);  
document.write(contact.surname + ", " + contact.firstname);  
document.write(contact.phone[1]);  
// Output:  
// Aaberg, Jesper  
// 555-0100  
```  
  
## <a name="example"></a>Esempio  
 Di seguito viene illustrato come convertire una matrice in una stringa JSON utilizzando `JSON.stringify`e quindi come riconvertire la stringa in una matrice utilizzando `JSON.parse`.  
  
```JavaScript  
var arr = ["a", "b", "c"];  
var str = JSON.stringify(arr);  
document.write(str);  
document.write ("<br/>");  
  
var newArr = JSON.parse(str);  
  
while (newArr.length > 0) {  
    document.write(newArr.pop() + "<br/>");  
}  
  
// Output:  
// ["a","b","c"]  
// c  
// b  
// a  
```  
  
## <a name="example"></a>Esempio  
 La funzione `reviver` viene spesso usata per trasformare la rappresentazione JSON di stringhe di data ISO (International Organization for Standardization) in oggetti `Date` in formato UTC (Coordinated Universal Time). In questo esempio viene usato `JSON.parse` per deserializzare una stringa di data con formato ISO. La funzione `dateReviver` restituisce oggetti `Date` per i membri che sono formattati come le stringhe di date ISO.  
  
```JavaScript  
var jsontext = '{ "hiredate": "2008-01-01T12:00:00Z", "birthdate": "2008-12-25T12:00:00Z" }';  
var dates = JSON.parse(jsontext, dateReviver);  
document.write(dates.birthdate.toUTCString());  
  
function dateReviver(key, value) {  
    var a;  
    if (typeof value === 'string') {  
        a = /^(\d{4})-(\d{2})-(\d{2})T(\d{2}):(\d{2}):(\d{2}(?:\.\d*)?)Z$/.exec(value);  
        if (a) {  
            return new Date(Date.UTC(+a[1], +a[2] - 1, +a[3], +a[4],  
                            +a[5], +a[6]));  
        }  
    }  
    return value;  
};  
  
// Output:  
// Thu, 25 Dec 2008 12:00:00 UTC  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv58](../../javascript/reference/includes/jsv58-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione JSON. stringify](../../javascript/reference/json-stringify-function-javascript.md)   
 [Metodo toJSON (Date)](../../javascript/reference/tojson-method-date-javascript.md)   
 [App di esempio di modello hub (Windows Store)](http://code.msdn.microsoft.com/Hub-template-sample-with-4b70002d)