---
title: Metodo setSeconds (Date) (JavaScript) | Documenti Microsoft
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
- setSeconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- setSeconds method
- seconds method
ms.assetid: 986ffa54-1db6-4af2-ab8b-8353f64f0b57
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b8d545307f6aac3506310c868a2860a6159a106
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="setseconds-method-date-javascript"></a>Metodo setSeconds (Date) (JavaScript)
Imposta il valore secondi `Date` oggetto utilizzando l'ora locale.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
dateObj  
.setSeconds(  
numSeconds[, numMilli])   
```  
  
## <a name="parameters"></a>Parametri  
 `dateObj`  
 Obbligatorio. Qualsiasi oggetto `Date`.  
  
 *numSeconds*  
 Obbligatorio. Valore numerico che rappresenta il valore dei secondi.  
  
 `numMilli`  
 Parametro facoltativo. Valore numerico che rappresenta il valore dei millisecondi.  
  
## <a name="remarks"></a>Note  
 Tutti **impostare** i metodi che gli argomenti facoltativi utilizzato il valore restituito dal corrispondente **ottenere** metodi, se non si specifica un argomento facoltativo. Ad esempio, se il `numMilli` argomento non viene specificato, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] utilizza il valore restituito dal **getMilliseconds** metodo.  
  
 Per impostare il valore utilizzando l'ora UTC (Universal Coordinated Time), utilizzare il `setUTCSeconds` metodo.  
  
 Se il valore di un argomento è maggiore dell'intervallo specificato o è un numero negativo, gli altri valori memorizzati verranno modificati di conseguenza. Ad esempio, se la data memorizzata è "il 5 gennaio 1996 00:00:00" e **setSeconds(150)** viene chiamato, la data viene modificata in "5 gennaio 1996 02:00:30."  
  
 Il `setHours` metodo può essere utilizzato per impostare le ore, minuti, secondi e millisecondi.  
  
## <a name="example"></a>Esempio  
 Nell'esempio riportato di seguito viene illustrato l'utilizzo del metodo `setSeconds`.  
  
```JavaScript  
function SetSecondsDemo(nsec){  
   var d = new Date();         //Create Date object.  
   d.setSeconds(nsec);         //Set seconds.  
   var s = "Current setting is ";  
   s += d.toLocaleString();  
   return(s);                  //Return new setting.  
}  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Si applica a**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getSeconds (Date)](../../javascript/reference/getseconds-method-date-javascript.md)   
 [Metodo getUTCSeconds (Date)](../../javascript/reference/getutcseconds-method-date-javascript.md)   
 [Metodo setUTCSeconds (Date)](../../javascript/reference/setutcseconds-method-date-javascript.md)