---
title: Metodo toUTCString (Date) (JavaScript) | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- toUTCString
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- UTC dates, converting to strings
- toUTCString method
ms.assetid: eb0983ed-7884-42fa-a2cc-de92b3111207
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0bd5efc43152c1af2dd467b73dce235e8fe52f29
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="toutcstring-method-date-javascript"></a>Metodo toUTCString (Date) (JavaScript)
Restituisce una data convertita in una stringa utilizzando l'ora UTC (Universal Coordinated Time).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
dateObj.toUTCString()   
```  
  
## <a name="remarks"></a>Note  
 Obbligatorio `dateObj` si intende qualsiasi riferimento `Date` oggetto.  
  
 Il `toUTCString` metodo restituisce un `String` oggetto che contiene la data formattata utilizzando la convenzione UTC in un formato di agevole lettura.  
  
## <a name="example"></a>Esempio  
 Nell'esempio riportato di seguito viene illustrato l'utilizzo del metodo `toUTCString`.  
  
```JavaScript  
function toUTCStrDemo(){  
   var d, s;                   //Declare variables.  
   d = new Date();             //Create Date object.  
   s = "Current setting is ";  
   s += d.toUTCString();       //Convert to UTC string.  
   return(s);                  //Return UTC string.  
}  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Si applica a**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo toGMTString (Date)](../../javascript/reference/togmtstring-method-date-javascript.md)