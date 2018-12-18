---
title: Funzione Date.UTC (JavaScript) | Documenti Microsoft
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
- UTC
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- UTC function [JavaScript]
- UTC dates, returning
- Date.UTC function [JavaScript]
ms.assetid: c0d67ce1-a47e-4dfd-bbf4-21619c406a0f
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a6a7c5622b74699e3d718ceb65e96638bdb6c3c5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="dateutc-function-javascript"></a>Funzione Date.UTC (JavaScript)
Restituisce il numero di millisecondi tra la mezzanotte dell'1 gennaio 1970 ora UTC (Universal Coordinated Time) (o GMT) e la data specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Date.UTC(year, month, day[, hours[, minutes[, seconds[,ms]]]])   
```  
  
## <a name="parameters"></a>Parametri  
 `year`  
 Obbligatorio. La designazione di un anno completo è obbligatorio per le date tra secolo. Se `year` è compreso tra 0 e 99 viene usato, quindi `year` si presuppone che sia 1900 + `year`.  
  
 `month`  
 Obbligatorio. Il mese come numero intero compreso tra 0 e 11 (gennaio-dicembre).  
  
 `day`  
 Obbligatorio. La data come numero intero compreso tra 1 e 31.  
  
 `hours`  
 Parametro facoltativo. È necessario specificare se `minutes` viene fornito. Intero compreso tra 0 e 23 (da mezzanotte a 11 pm) che specifica l'ora.  
  
 `minutes`  
 Parametro facoltativo. È necessario specificare se `seconds` viene fornito. Intero compreso tra 0 e 59 che rappresenta i minuti.  
  
 `seconds`  
 Parametro facoltativo. È necessario specificare se `milliseconds` viene fornito. Intero compreso tra 0 e 59 che rappresenta i secondi.  
  
 `ms`  
 Parametro facoltativo. Intero compreso tra 0 e 999 che specifica il numero di millisecondi.  
  
## <a name="remarks"></a>Note  
 Il `Date.UTC` funzione restituisce il numero di millisecondi compresi tra la mezzanotte dell'1 gennaio 1970, UTC e la data specificata. Il valore restituito può essere utilizzato nel `setTime` (metodo) e il `Date` costruttore dell'oggetto. Se il valore di un argomento è maggiore dell'intervallo specificato o è un numero negativo, gli altri valori memorizzati verranno modificati di conseguenza. Ad esempio, se si specifica 150 secondi, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] ridefinisce il numero massimo di due minuti e 30 secondi.  
  
 La differenza tra il `Date.UTC` (funzione) e `Date` costruttore dell'oggetto che accetta una data è che il `Date.UTC` UTC, si presuppone di funzione e `Date` costruttore dell'oggetto presuppone l'ora locale.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente illustra l'uso della funzione `Date.UTC`.  
  
```JavaScript  
// Determine the milliseconds per day.  
 var MinMilli = 1000 * 60;  
var HrMilli = MinMilli * 60;  
var DyMilli = HrMilli * 24;  
  
var date = new Date("June 1, 1990");  
var year = date.getFullYear();  
var month = date.getMonth();  
var day = date.getDay();  
  
var newDay = new Date("January 16, 2020");  
var yeartoday = newDay.getUTCFullYear();  
var monthtoday = newDay.getUTCMonth();  
var dayofmonthtoday = newDay.getUTCDate();  
  
// Get the milliseconds since 1/1/1970 UTC.  
var t1 = Date.UTC(year, month - 1, day)  
var t2 = Date.UTC(yeartoday, monthtoday, dayofmonthtoday);  
  
// Determine the difference in days.  
var days = (t2 - t1) / DyMilli;  
  
document.write(days);  
// Output: 10848  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo setTime (Date)](../../javascript/reference/settime-method-date-javascript.md)