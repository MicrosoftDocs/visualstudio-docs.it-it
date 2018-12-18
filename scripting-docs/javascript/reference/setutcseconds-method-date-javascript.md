---
title: Metodo setUTCSeconds (Date) (JavaScript) | Documenti Microsoft
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
- setUTCSeconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, UTC
- setUTCSeconds method
- UTC times, setting
- seconds method
ms.assetid: e035e282-b39d-4d1d-8771-c17542fd6493
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f3df010cd84332d8957f1c08c41c4543dec36e4a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="setutcseconds-method-date-javascript"></a>Metodo setUTCSeconds (Date) (JavaScript)
Imposta il valore secondi `Date` utilizzando l'ora UTC (Universal Coordinated Time).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
dateObj.setUTCSeconds(numSeconds[, numMilli])   
```  
  
## <a name="parameters"></a>Parametri  
 `dateObj`  
 Obbligatorio. Qualsiasi oggetto `Date`.  
  
 *numSeconds*  
 Obbligatorio. Valore numerico che rappresenta il valore dei secondi.  
  
 `numMilli`  
 Parametro facoltativo. Valore numerico che rappresenta il valore dei millisecondi.  
  
## <a name="remarks"></a>Note  
 Tutti **impostare** i metodi che gli argomenti facoltativi utilizzato il valore restituito dal corrispondente **ottenere** metodi, se non si specifica un argomento facoltativo. Ad esempio, se il `numMilli` argomento non viene specificato, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] utilizza il valore restituito dal `getUTCMilliseconds` metodo.  
  
 Per impostare il valore utilizzando l'ora locale, utilizzare il `setSeconds` metodo.  
  
 Se il valore di un argomento è maggiore dell'intervallo specificato o è un numero negativo, gli altri valori memorizzati verranno modificati di conseguenza. Ad esempio, se la data memorizzata è "5 gennaio 1996 00.00.00.00" e **setSeconds(150)** viene chiamato, la data viene modificata in "5 gennaio 1996 00.02.30.00".  
  
 Il **setUTCHours** metodo può essere utilizzato per impostare le ore, minuti, secondi e millisecondi.  
  
## <a name="example"></a>Esempio  
 Nell'esempio riportato di seguito viene illustrato l'utilizzo del metodo `setUTCSeconds`.  
  
```JavaScript  
function SetUTCSecondsDemo(nsec){  
// Create Date object.  
    var d = new Date();       
// Set UTC seconds.  
    d.setUTCSeconds(nsec);    
    var s = "Current setting is ";  
    s += d.toUTCString();  
// Return new setting.  
    return(s);                
}  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Si applica a**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getSeconds (Date)](../../javascript/reference/getseconds-method-date-javascript.md)   
 [Metodo getUTCSeconds (Date)](../../javascript/reference/getutcseconds-method-date-javascript.md)   
 [Metodo setSeconds (Date)](../../javascript/reference/setseconds-method-date-javascript.md)