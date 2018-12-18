---
title: Funzione date. Parse (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: parse
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- parse function [JavaScript]
- Date.parse function [JavaScript]
ms.assetid: ed737e50-6398-4462-8779-2af3c03f8325
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0a73fda66ef24df17a5213a182c04667fc4dfabf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="dateparse-function-javascript"></a>Funzione Date.parse (JavaScript)
Analizza una stringa contenente una data e restituisce il numero di millisecondi tra la data e la mezzanotte dell'1 gennaio 1970.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Date.parse(dateVal)   
```  
  
## <a name="remarks"></a>Note  
 Obbligatorio `dateVal` argomento è una stringa che contiene una data o un valore VT_DATE recuperato da un oggetto ActiveX o un altro oggetto. Per informazioni sulla data stringhe il `Date.parse` funzione in grado di analizzare. vedere [stringhe data e ora](../../javascript/date-and-time-strings-javascript.md).  
  
 Il `Date.parse` funzione restituisce un valore intero che rappresenta il numero di millisecondi tra la mezzanotte dell'1 gennaio 1970 e la data specificata in `dateVal`.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente illustra l'uso della funzione `Date.parse`.  
  
```JavaScript  
var dateString = "November 1, 1997 10:15 AM";  
var mSec = Date.parse(dateString);  
document.write(mSec);  
// Output: 878404500000  
```  
  
## <a name="example"></a>Esempio  
 L'esempio seguente restituisce la differenza tra la data fornita e 1/1/1970.  
  
```JavaScript  
var minMilli = 1000 * 60;  
var hrMilli = minMilli * 60;  
var dyMilli = hrMilli * 24;  
  
var testDate = new Date("June 1, 1990");  
var ms = Date.parse(testDate);  
var days = Math.round(ms / dyMilli);  
  
var dateStr = "";  
dateStr += "There are " + days + " days ";  
dateStr += "between 01/01/1970 and " + testDate;  
document.write(dateStr);  
  
// Output: There are 7456 days between 01/01/1970 and Fri Jun 1 00:00:00 PDT 1990  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getDate (Date)](../../javascript/reference/getdate-method-date-javascript.md)