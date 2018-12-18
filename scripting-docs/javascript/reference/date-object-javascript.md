---
title: Data Object (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Date
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Date object
- dates, determining
ms.assetid: ce2202bb-7ec9-4f5a-bf48-3a04feff283e
caps.latest.revision: "29"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eb5d53f3bddfeb3a3ed1ab36e2b4be822964eba5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="date-object-javascript"></a>Oggetto Date (JavaScript)
Abilita l'archiviazione e il recupero di base di valori di data e ora.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
      dateObj = new Date()  
dateObj = new Date(dateVal)  
dateObj = new Date(year, month, date[, hours[, minutes[, seconds[,ms]]]])   
```  
  
## <a name="parameters"></a>Parametri  
 `dateObj`  
 Obbligatorio. Nome della variabile a cui l'oggetto `Date` è assegnato.  
  
 `dateVal`  
 Obbligatorio. Se un valore numerico, `dateVal` rappresenta il numero di millisecondi in Coordinated Universal Time tra la data specificata e la mezzanotte del 1 ° gennaio 1970. Se una stringa, `dateVal` viene analizzata sulla base delle regole in [stringhe data e ora](../../javascript/date-and-time-strings-javascript.md). Il `dateVal` argomento può anche essere un valore VT_DATE restituiti da alcuni oggetti ActiveX.  
  
 `year`  
 Obbligatorio. L'anno completo, ad esempio, 1976, (e non 76).  
  
 `month`  
 Obbligatorio. Il mese come numero intero compreso tra 0 e 11 (gennaio-dicembre).  
  
 `date`  
 Obbligatorio. La data come numero intero compreso tra 1 e 31.  
  
 `hours`  
 Parametro facoltativo. È necessario specificare se `minutes` viene fornito. Intero compreso tra 0 e 23 (da mezzanotte a 11 pm) che specifica l'ora.  
  
 minuti  
 Parametro facoltativo. È necessario specificare se `seconds` viene fornito. Intero compreso tra 0 e 59 che rappresenta i minuti.  
  
 `seconds`  
 Parametro facoltativo. È necessario specificare se `milliseconds` viene fornito. Intero compreso tra 0 e 59 che rappresenta i secondi.  
  
 `ms`  
 Parametro facoltativo. Intero compreso tra 0 e 999 che specifica il numero di millisecondi.  
  
## <a name="remarks"></a>Note  
 Oggetto `Date` oggetto contiene un numero che rappresenta un istante specifico nel tempo all'interno di un millisecondo. Se il valore di un argomento è maggiore dell'intervallo specificato o è un numero negativo, gli altri valori memorizzati verranno modificati di conseguenza. Ad esempio, se si specifica 150 secondi, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] ridefinisce il numero massimo di due minuti e 30 secondi.  
  
 Se il numero è `NaN`, l'oggetto non rappresenta un istante di tempo specifico. Se viene passato alcun parametro per il `Date` dell'oggetto, viene inizializzato all'ora corrente (UTC). Un valore deve essere specificato per l'oggetto prima che sia possibile utilizzarlo.  
  
 L'intervallo di date che può essere rappresentato in un `Date` oggetto è pari a circa 285.616 anni entrambi i lati del 1 gennaio 1970.  
  
 Vedere [il calcolo di date e ore (JavaScript)](../../javascript/calculating-dates-and-times-javascript.md) per ulteriori informazioni sull'utilizzo di `Date` oggetto e i relativi metodi.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo dell'oggetto `Date`.  
  
```JavaScript  
var dateString = "Today's date is: ";  
  
var newDate = new Date();  
  
// Get the month, day, and year.  
dateString += (newDate.getMonth() + 1) + "/";  
dateString += newDate.getDate() + "/";  
dateString += newDate.getFullYear();  
  
document.write(dateString);  
  
// Output: Today's date is: <date>  
```  
  
## <a name="requirements"></a>Requisiti  
 `Date object` è stato introdotto in [!INCLUDE[jsv1text](../../javascript/reference/includes/jsv1text-md.md)]. Alcuni membri dell'elenco seguente sono stati introdotti nelle versioni successive. Per ulteriori informazioni, vedere [informazioni sulla versione](../../javascript/reference/javascript-version-information.md) o la documentazione per i singoli membri.  
  
## <a name="properties"></a>Proprietà  
 La tabella seguente elenca le proprietà dell'oggetto `Date Object`.  
  
|Proprietà|Descrizione|  
|--------------|-----------------|  
|[Proprietà constructor](../../javascript/reference/constructor-property-date.md)|Specifica la funzione che crea un oggetto.|  
|[Proprietà prototype](../../javascript/reference/prototype-property-date.md)|Restituisce un riferimento al prototipo per una classe di oggetti.|  
  
## <a name="functions"></a>Funzioni  
 La tabella seguente elenca le funzioni dell'oggetto `Date Object`.  
  
|Funzioni|Descrizione|  
|---------------|-----------------|  
|[Funzione Date.now](../../javascript/reference/date-now-function-javascript.md)|Restituisce il numero di millisecondi compresi tra 1 gennaio 1970 e la data e ora correnti.|  
|[Funzione Date.parse](../../javascript/reference/date-parse-function-javascript.md)|Analizza una stringa contenente una data e restituisce il numero di millisecondi tra la data e la mezzanotte dell'1 gennaio 1970.|  
|[Funzione Date.UTC](../../javascript/reference/date-utc-function-javascript.md)|Restituisce il numero di millisecondi tra la mezzanotte dell'1 gennaio 1970 ora UTC (Universal Coordinated Time) (o GMT) e la data specificata.|  
  
<a name="js56jsobjdatemeth"></a>   
## <a name="methods"></a>Metodi  
 La tabella seguente elenca i metodi dell'oggetto `Date Object`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Metodo getDate](../../javascript/reference/getdate-method-date-javascript.md)|Restituisce il valore del giorno del mese utilizzando l'ora locale.|  
|[Metodo getDay](../../javascript/reference/getday-method-date-javascript.md)|Restituisce il valore del giorno della settimana utilizzando l'ora locale.|  
|[Metodo getFullYear](../../javascript/reference/getfullyear-method-date-javascript.md)|Restituisce il valore dell'anno utilizzando l'ora locale.|  
|[Metodo getHours](../../javascript/reference/gethours-method-date-javascript.md)|Restituisce il valore delle ore utilizzando l'ora locale.|  
|[Metodo getMilliseconds](../../javascript/reference/getmilliseconds-method-date-javascript.md)|Restituisce il valore dei millisecondi utilizzando l'ora locale.|  
|[Metodo getMinutes](../../javascript/reference/getminutes-method-date-javascript.md)|Restituisce il valore dei minuti utilizzando l'ora locale.|  
|[Metodo getMonth](../../javascript/reference/getmonth-method-date-javascript.md)|Restituisce il valore del mese utilizzando l'ora locale.|  
|[Metodo getSeconds](../../javascript/reference/getseconds-method-date-javascript.md)|Restituisce il valore dei secondi utilizzando l'ora locale.|  
|[Metodo getTime](../../javascript/reference/gettime-method-date-javascript.md)|Restituisce il valore di tempo in un `Date` oggetto come il numero di millisecondi trascorsi dalla mezzanotte del 1 ° gennaio 1970.|  
|[Metodo getTimezoneOffset](../../javascript/reference/gettimezoneoffset-method-date-javascript.md)|Restituisce la differenza in minuti tra l'ora del computer host e l'ora UTC (Universal Coordinated Time).|  
|[Metodo getUTCDate](../../javascript/reference/getutcdate-method-date-javascript.md)|Restituisce il valore del giorno del mese con l'ora UTC.|  
|[Metodo getUTCDay](../../javascript/reference/getutcday-method-date-javascript.md)|Restituisce il valore del giorno della settimana utilizzando l'ora UTC.|  
|[Metodo getUTCFullYear](../../javascript/reference/getutcfullyear-method-date-javascript.md)|Restituisce il valore di anno formato UTC.|  
|[Metodo getUTCHours](../../javascript/reference/getutchours-method-date-javascript.md)|Restituisce il valore delle ore UTC.|  
|[Metodo getUTCMilliseconds](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)|Restituisce il valore dei millisecondi in UTC.|  
|[Metodo getUTCMinutes](../../javascript/reference/getutcminutes-method-date-javascript.md)|Restituisce il valore UTC.|  
|[Metodo getUTCMonth](../../javascript/reference/getutcmonth-method-date-javascript.md)|Restituisce il valore del mese con l'ora UTC.|  
|[Metodo getUTCSeconds](../../javascript/reference/getutcseconds-method-date-javascript.md)|Restituisce i secondi come valore utilizzando l'ora UTC.|  
|[Metodo getVarDate](../../javascript/reference/getvardate-method-date-javascript.md)|Restituisce il valore VT_DATE in un `Date` oggetto.|  
|[Metodo getYear](../../javascript/reference/getyear-method-date-javascript.md)|Restituisce il valore dell'anno.|  
|[Metodo hasOwnProperty](../../javascript/reference/hasownproperty-method-object-javascript.md)|Restituisce un valore booleano che indica se per un oggetto è disponibile una proprietà con il nome specificato.|  
|[Metodo isPrototypeOf](../../javascript/reference/isprototypeof-method-object-javascript.md)|Restituisce un valore booleano che indica se un oggetto esiste nella catena di prototipi di un altro oggetto.|  
|[Metodo propertyIsEnumerable](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|Restituisce un valore booleano che indica se una proprietà specificata è parte di un oggetto e se è enumerabile.|  
|[Metodo setDate](../../javascript/reference/setdate-method-date-javascript.md)|Imposta il giorno numerico del mese utilizzando l'ora locale.|  
|[Metodo setFullYear](../../javascript/reference/setfullyear-method-date-javascript.md)|Imposta il valore di anno utilizzando l'ora locale.|  
|[Metodo setHours](../../javascript/reference/sethours-method-date-javascript.md)|Imposta il valore delle ore utilizzando l'ora locale.|  
|[Metodo setMilliseconds](../../javascript/reference/setmilliseconds-method-date-javascript.md)|Imposta il valore dei millisecondi utilizzando l'ora locale.|  
|[Metodo setMinutes](../../javascript/reference/setminutes-method-date-javascript.md)|Imposta il valore dei minuti utilizzando l'ora locale.|  
|[Metodo setMonth](../../javascript/reference/setmonth-method-date-javascript.md)|Imposta il valore del mese utilizzando l'ora locale.|  
|[Metodo setSeconds](../../javascript/reference/setseconds-method-date-javascript.md)|Imposta il valore secondi utilizzando l'ora locale.|  
|[Metodo setTime](../../javascript/reference/settime-method-date-javascript.md)|Imposta il valore di data e ora nel `Date` oggetto.|  
|[Metodo setUTCDate](../../javascript/reference/setutcdate-method-date-javascript.md)|Imposta il giorno numerico del mese con l'ora UTC.|  
|[Metodo setUTCFullYear](../../javascript/reference/setutcfullyear-method-date-javascript.md)|Imposta il valore di anno formato UTC.|  
|[Metodo setUTCHours](../../javascript/reference/setutchours-method-date-javascript.md)|Imposta il valore delle ore UTC.|  
|[Metodo setUTCMilliseconds](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)|Imposta il valore dei millisecondi in UTC.|  
|[Metodo setUTCMinutes](../../javascript/reference/setutcminutes-method-date-javascript.md)|Imposta il valore UTC.|  
|[Metodo setUTCMonth](../../javascript/reference/setutcmonth-method-date-javascript.md)|Imposta valore del mese in formato UTC.|  
|[Metodo setUTCSeconds](../../javascript/reference/setutcseconds-method-date-javascript.md)|Imposta il valore secondi formato UTC.|  
|[Metodo setYear](../../javascript/reference/setyear-method-date-javascript.md)|Imposta il valore di anno utilizzando l'ora locale.|  
|[Metodo toDateString](../../javascript/reference/todatestring-method-date-javascript.md)|Restituisce una data come valore stringa.|  
|[Metodo toGMTString](../../javascript/reference/togmtstring-method-date-javascript.md)|Restituisce una data convertita in una stringa con ora di Greenwich (GMT).|  
|[Metodo toISOString](../../javascript/reference/toisostring-method-date-javascript.md)|Restituisce una data come valore stringa in formato ISO.|  
|[Metodo toJSON](../../javascript/reference/tojson-method-date-javascript.md)|Utilizzato per trasformare i dati di un tipo di oggetto prima della serializzazione JSON.|  
|[Metodo toLocaleDateString](../../javascript/reference/tolocaledatestring-method-date-javascript.md)|Restituisce una data come valore di stringa appropriato alle impostazioni locali correnti dell'ambiente host.|  
|[Metodo toLocaleString](../../javascript/reference/tolocalestring-date.md)|Restituisce un oggetto convertito in una stringa utilizzando le impostazioni locali correnti.|  
|[Metodo toLocaleTimeString](../../javascript/reference/tolocaletimestring-method-date-javascript.md)|Restituisce un'ora come valore di stringa appropriato alle impostazioni locali correnti dell'ambiente host.|  
|[Metodo toString](../../javascript/reference/tostring-method-date.md)|Restituisce la rappresentazione in formato stringa di un oggetto.|  
|[Metodo toTimeString](../../javascript/reference/totimestring-method-date-javascript.md)|Restituisce un'ora come valore stringa.|  
|[Metodo toUTCString](../../javascript/reference/toutcstring-method-date-javascript.md)|Restituisce una data convertita in una stringa di formato UTC.|  
|[Metodo valueOf](../../javascript/reference/valueof-method-date.md)|Restituisce il valore primitivo dell'opzione specificata.|  
  
## <a name="see-also"></a>Vedere anche  
 [Calcolo di date e ore (JavaScript)](../../javascript/calculating-dates-and-times-javascript.md)   
 [Stringhe di data e ora](../../javascript/date-and-time-strings-javascript.md)