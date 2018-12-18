---
title: Metodo setUTCMilliseconds (Date) (JavaScript) | Documenti Microsoft
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
- setUTCMilliseconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- milliseconds
- dates, UTC
- UTC times, setting
- setUTCMilliseconds method
ms.assetid: ed8e4486-d4b2-4b73-836b-dd1d3bb991a0
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 279d00b256b3b0763e2f15f549fdc6ee81c20254
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="setutcmilliseconds-method-date-javascript"></a>Metodo setUTCMilliseconds (Date) (JavaScript)
Imposta il valore dei millisecondi nel `Date` utilizzando l'ora UTC (Universal Coordinated Time).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
dateObj.setUTCMilliseconds(numMilli)   
```  
  
## <a name="parameters"></a>Parametri  
 `dateObj`  
 Obbligatorio. Qualsiasi oggetto `Date`.  
  
 `numMilli`  
 Obbligatorio. Valore numerico che rappresenta il valore dei millisecondi.  
  
## <a name="remarks"></a>Note  
 Per impostare il numero di millisecondi utilizzando l'ora locale, utilizzare il `setMilliseconds` metodo.  
  
 Se il valore di `numMilli` è maggiore di 999 o è un numero negativo, viene incrementato il numero di secondi (e minuti, ore e così via, se necessario) memorizzato una quantità appropriata.  
  
## <a name="example"></a>Esempio  
 Nell'esempio riportato di seguito viene illustrato l'utilizzo del metodo `setUTCMilliseconds`.  
  
```JavaScript  
function SetUTCMSecDemo(nmsec){     
// Create Date object.  
   var d = new Date();             
// Set UTC milliseconds.  
   d.setUTCMilliseconds(nmsec);    
  
   var s = "Current setting is ";  
   s += d.toUTCString();  
   s += " and " + d.getUTCMilliseconds();  
   s += " milliseconds"  
   return(s);  
}  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Si applica a**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getMilliseconds (Date)](../../javascript/reference/getmilliseconds-method-date-javascript.md)   
 [Metodo getUTCMilliseconds (Date)](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)   
 [Metodo setMilliseconds (Date)](../../javascript/reference/setmilliseconds-method-date-javascript.md)