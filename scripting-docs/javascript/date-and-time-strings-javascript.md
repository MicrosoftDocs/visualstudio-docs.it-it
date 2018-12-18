---
title: Stringhe di data e ora (JavaScript) | Microsoft Docs
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
ms.assetid: ba0798c5-3574-4434-89f4-3d90be276001
caps.latest.revision: "47"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6218ba273b26243382d1e825b6da961d604917ab
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="date-and-time-strings-javascript"></a>Stringhe di data e ora (JavaScript)
Si possono utilizzare diverse tecniche per specificare e formattare le stringhe di data e ora di JavaScript.  
  
## <a name="formatting-dates-using-intldatetimeformat"></a>Formattazione di date mediante Intl.DateTimeFormat  
 In Internet Explorer 11 è stato introdotto il supporto dell'[Oggetto Intl.DateTimeFormat](../javascript/reference/intl-datetimeformat-object-javascript.md), che fa parte della [specifica dell'API di internazionalizzazione ECMAScript](http://www.ecma-international.org/ecma-402/1.0/). Per formattare le date è possibile usare direttamente l'oggetto oppure l'implementazione aggiornata del [Metodo toLocaleDateString (Date)](../javascript/reference/tolocaledatestring-method-date-javascript.md) e del [Metodo toLocaleTimeString (Date)](../javascript/reference/tolocaletimestring-method-date-javascript.md). Questi metodi di [Oggetto Date](../javascript/reference/date-object-javascript.md) usano `Intl.DateTimeFormat` internamente per supportare nuovi parametri facoltativi per le impostazioni locali e altre opzioni di formattazione.  
  
 Di seguito viene illustrato come utilizzare `toLocaleDateString` e `toLocaleTimeString` per formattare date e ore. Il primo parametro passato a questi metodi è un valore locale, ad esempio "it-it". Il secondo parametro, se presente, specifica le opzioni di formattazione, quali la forma estesa per il giorno della settimana.  
  
```JavaScript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = {  
    weekday: "long", year: "numeric", month: "short",  
    day: "numeric", hour: "2-digit", minute: "2-digit"  
};  
  
document.write(date.toLocaleDateString("en-US"));  
document.write(date.toLocaleTimeString("en-us", options));  
document.write(date.toLocaleDateString("ja-JP"));  
document.write(date.toLocaleTimeString("ja-JP", options));  
  
// Output:  
// ‎2‎/‎1‎/‎2013  
// ‎Friday‎, ‎Feb‎ ‎1‎, ‎2013‎ ‎06‎:‎00‎ ‎AM  
// ‎2013‎年‎2‎月‎1‎日‎  
// ‎2013‎年‎2‎月‎1‎日 ‎金曜日‎ ‎06‎:‎00  
```  
  
 Per un elenco completo di opzioni di formattazione, vedere [Oggetto Intl.DateTimeFormat](../javascript/reference/intl-datetimeformat-object-javascript.md).  
  
## <a name="formatting-dates"></a>Formattazione di date  
 Nelle versioni precedenti a Internet Explorer 11, JavaScript non dispone di metodi specifici per formattare date e ore. Per specificare la propria formattazione della data per le versioni di browser precedenti, usare i metodi [Metodo getDay (Date)](../javascript/reference/getday-method-date-javascript.md), [Metodo getDate (Date)](../javascript/reference/getdate-method-date-javascript.md), [Metodo getMonth (Date)](../javascript/reference/getmonth-method-date-javascript.md) e [Metodo getFullYear (Date)](../javascript/reference/getfullyear-method-date-javascript.md). (Il [Metodo getYear (Date)](../javascript/reference/getyear-method-date-javascript.md) è obsoleto e non deve essere usato).  
  
```JavaScript  
var myDate = new Date("February 3, 2001");  
var myDate = new Date("February 3 2001");  
document.write((myDate.getMonth() + 1) + "-" + myDate.getDate() + "-" + myDate.getFullYear());  
document.write("<br/>");  
document.write((myDate.getMonth() + 1) + "/" + myDate.getDate() + "/" + myDate.getFullYear());  
  
//Output:  
// 2-3-2001  
// 2/3/2001  
```  
  
 È possibile specificare la propria formattazione dell'ora usando i metodi [Metodo getHours (Date)](../javascript/reference/gethours-method-date-javascript.md), [Metodo getMinutes (Date)](../javascript/reference/getminutes-method-date-javascript.md), [Metodo getSeconds (Date)](../javascript/reference/getseconds-method-date-javascript.md) e [Metodo getMilliseconds (Date)](../javascript/reference/getmilliseconds-method-date-javascript.md).  
  
```JavaScript  
myDate = new Date();  
myDate.setHours(10, 30, 53, 400);  
  
document.write(myDate.getHours() + ":" + myDate.getMinutes() + ":" + myDate.getSeconds() +   
":" + myDate.getMilliseconds());  
  
// Output:   
// 10:30:53:400  
```  
  
## <a name="converting-strings-to-dates"></a>Conversione delle stringhe in date  
 Si possono specificare le stringhe per costruire oggetti `Date` con `Date(dateStr)` o `Date.parse(dateStr)`. JavaScript usa le seguenti regole per analizzare le stringhe di date:  
  
-   Prima di tutto, tenta di analizzare una stringa di data con il [Formato di data ISO](#ISO).  
  
    > [!NOTE]
    >  JavaScript usa una versione semplificata del formato esteso ISO 8601.  
  
-   Se la stringa di data non è in formato ISO, JavaScript tenta di analizzare la data con [Altri formati di data](#OtherDateFormats).  
  
<a name="ISO"></a>   
## <a name="iso-date-format"></a>Formato di data ISO  
 Il formato ISO è una semplificazione del formato esteso ISO 8601. Il formato è il seguente:  
  
 `YYYY-MM-DDTHH:mm:ss.sssZ`  
  
> [!IMPORTANT]
>  Il formato di data ISO non è supportato nella modalità standard e non standard di Internet Explorer 8.  
  
 Nella tabella che segue vengono descritte le parti di ciascun formato.  
  
|Simbolo|Descrizione|Valori|  
|------------|-----------------|------------|  
|`-`, `:`, `.`, `T`|Caratteri attualmente nella stringa. `T` specifica l’inizio di un'ora.||  
|`YYYY`|Anno. Un anno esteso può essere utilizzato al posto di un anno a 4 cifre. Per altre informazioni, vedere [Anni estesi](../javascript/date-and-time-strings-javascript.md#bkmk_extend) più avanti in questo argomento.||  
|`MM`|Mese|Da 01 a 12|  
|`DD`|Giorno del mese|Da 01 a 31|  
|`HH`|Ore|Da 00 a 24|  
|`mm`|Minuti|Da 00 a 59|  
|`ss`|Secondi. I secondi e i millisecondi sono facoltativi se si specifica un'ora.|Da 00 a 59|  
|`sss`|Milliseconds|Da 00 a 999|  
|`Z`|Il valore in questa posizione può essere uno dei seguenti. Se il valore viene omesso, viene utilizzata l'ora UTC.<br /><br /> -   `Z` indica l'ora UTC.<br />-   `+hh:mm` indica che l'ora di input è l'offset specificato dopo l'ora UTC.<br />-   `-hh:mm` indica che l'ora di input è il valore assoluto dell'offset specificato prima dell'ora UTC.||  
  
 La stringa può includere solo la data, come nei formati seguenti: `YYYY`, `YYYY-MM`, `YYYY-MM-DD`.  
  
 Il formato ISO non supporta i nomi dei fusi orari. È possibile utilizzare la posizione `Z` per specificare un offset rispetto all'ora UTC. Se non si include un valore nella posizione `Z`, viene utilizzata l'ora UTC.  
  
 È possibile specificare la mezzanotte utilizzando 00:00 o utilizzando le 24:00 del giorno precedente. Le seguenti due stringhe specificano la stessa ora: 2010-05-25T00:00 e 2010-05-24T24:00.  
  
 Per restituire una data nel formato ISO, è possibile usare il [Metodo toISOString (Date)](../javascript/reference/toisostring-method-date-javascript.md).  
  
<a name="bkmk_extend"></a>   
### <a name="extended-years"></a>Anni estesi  
 Un *anno esteso* ha 6 cifre anziché 4 ed è preceduto da un segno più o da un segno meno. Un esempio di anno esteso è `+002010`, che equivale a `2010`. È possibile utilizzare un anno esteso per rappresentare gli anni prima dell'anno 0 o dopo il 9999.  
  
 Se si utilizza il formato a 6 cifre, deve essere presente un segno più o un segno meno. Quando si utilizza il formato a 4 cifre, il segno deve essere assente. Pertanto, `0000` e `+000000` vengono accettati, mentre `000000` e `-0001` causano un errore. L'anno esteso 0 è considerato positivo e pertanto è preceduto da un segno più.  
  
 Il [Metodo toISOString (Date)](../javascript/reference/toisostring-method-date-javascript.md) usa sempre il formato di anno esteso per gli anni che sono precedenti a 0 oppure sono successivi a 9999.  
  
> [!NOTE]
>  [!INCLUDE[jsv9](../javascript/includes/jsv9-md.md)]  
  
<a name="OtherDateFormats"></a>   
## <a name="other-date-formats"></a>Altri formati di data  
 Se una stringa di data non è in formato ISO, [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] utilizza le seguenti regole per analizzarla.  
  
 Date brevi  
  
-   Il formato deve seguire l'ordine mese/giorno/anno, ad esempio "08/06/2010".  
  
-   Si può utilizzare "/" o "-" come separatore.  
  
 Date lunghe  
  
-   L'anno, il mese e il giorno possono essere in qualsiasi ordine. "Giugno 8 2010" e "2010 Giugno 8" sono entrambi validi.  
  
-   L'anno può avere due o quattro cifre. Se l'anno ha solo due cifre, deve essere almeno 70.  
  
-   I nomi di mesi e giorni devono avere almeno due caratteri. Se i due caratteri non consentono di identificare il nome in modo univoco, viene considerata valida l'ultima corrispondenza. Ad esempio, "Ju" specifica "July"(Luglio), e non "June"(Giugno).  
  
-   Un giorno della settimana viene ignorato se non è coerente con il resto della data specificata. Ad esempio, "Martedì 9 Novembre 1996" viene risolto con "Venerdì 9 Novembre 1996" perché venerdì è il giorno della settimana corretto per quella data.  
  
 Ore  
  
-   Le ore, i minuti e i secondi sono separati da due punti. Tuttavia, alcune parti possono essere omesse. Gli esempi seguenti sono validi: "10:", "10:11" e "10:11:12".  
  
-   Se viene specificato PM e l'ora specificata è almeno 13, viene restituito NaN. Ad esempio, "23:15 PM" restituisce NaN.  
  
 Generale  
  
-   Una stringa contenente una data non valida restituisce NaN. Ad esempio, una stringa contenente due anni o due mesi restituisce NaN.  
  
-   [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] supporta tutti i fusi orari standard, UTC (Universal Coordinated Time) e GMT (Greenwich Mean Time). Il formato ISO non supporta i fusi orari.  
  
-   Il testo racchiuso tra parentesi viene considerato come un commento. Le parentesi possono essere annidate.  
  
-   Le virgole e gli spazi vengono considerati come delimitatori. È possibile specificare più delimitatori.  
  
## <a name="example"></a>Esempio  
 Il codice seguente mostra il risultato dell'analisi di diverse stringhe di data e ora.  
  
```  
document.writeln((new Date("2010")).toUTCString());   
  
document.writeln((new Date("2010-06")).toUTCString());  
  
document.writeln((new Date("2010-06-09")).toUTCString());  
  
 // Specifies Z, which indicates UTC time.  
document.writeln((new Date("2010-06-09T15:20:00Z")).toUTCString());  
  
 // Specifies -07:00 offset, which is equivalent to Pacific Daylight time.  
document.writeln((new Date("2010-06-09T15:20:00-07:00")).toGMTString());  
  
// Specifies a non-ISO Long date.  
document.writeln((new Date("June 9, 2010")).toUTCString());  
  
// Specifies a non-ISO Long date.  
document.writeln((new Date("2010 June 9")).toUTCString());  
  
// Specifies a non-ISO Short date and time.  
document.writeln((new Date("6/9/2010 3:20 pm")).toUTCString());  
  
// Output:  
// Fri, 1 Jan 2010 00:00:00 UTC  
// Tue, 1 Jun 2010 00:00:00 UTC  
// Wed, 9 Jun 2010 00:00:00 UTC  
// Wed, 9 Jun 2010 15:20:00 UTC  
// Wed, 9 Jun 2010 22:20:00 UTC  
// Wed, 9 Jun 2010 07:00:00 UTC  
// Wed, 9 Jun 2010 07:00:00 UTC  
// Wed, 9 Jun 2010 22:20:00 UTC  
```  
  
 Dove le ore locali sono specificate, il risultato varierà a seconda del fuso orario.  
  
> [!IMPORTANT]
>  Il formato di data ISO non è supportato nella modalità standard e non standard di Internet Explorer 8.  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Date](../javascript/reference/date-object-javascript.md)   
 [Funzione Date.parse](../javascript/reference/date-parse-function-javascript.md)