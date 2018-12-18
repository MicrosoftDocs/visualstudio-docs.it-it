---
title: Metodo setUTCHours (Date) (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: setUTCHours
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, UTC
- UTC times, setting
- setUTCHours method
ms.assetid: 257e36fd-fb06-4a4d-8634-d66a020a1511
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9fe83735028f86d38ef270beac6c44dfa4caae7f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="setutchours-method-date-javascript"></a>Metodo setUTCHours (Date) (JavaScript)
Imposta il valore delle ore di `Date` utilizzando l'ora UTC (Universal Coordinated Time).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
dateObj.setUTCHours(numHours[, numMin[, numSec[, numMilli]]])   
```  
  
## <a name="parameters"></a>Parametri  
 `dateObj`  
 Obbligatorio. Qualsiasi oggetto `Date`.  
  
 `numHours`  
 Obbligatorio. Valore numerico che rappresenta il valore delle ore.  
  
 `numMin`  
 Parametro facoltativo. Valore numerico che rappresenta il valore dei minuti. È necessario specificare se il valore `numSec` o `numMilli` vengono utilizzati.  
  
 `numSec`  
 Parametro facoltativo. Valore numerico che rappresenta il valore dei secondi. È necessario specificare se `numMilli` viene utilizzato l'argomento.  
  
 `numMilli`  
 Parametro facoltativo. Valore numerico che rappresenta il valore dei millisecondi.  
  
## <a name="remarks"></a>Note  
 Tutti **impostare** i metodi che gli argomenti facoltativi utilizzato il valore restituito dal corrispondente **ottenere** metodi, se non si specifica un argomento facoltativo. Ad esempio, se il `numMin` argomento non viene specificato, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] utilizza il valore restituito dal `getUTCMinutes` metodo.  
  
 Per impostare il valore delle ore utilizzando l'ora locale, utilizzare il `setHours` metodo.  
  
 Se il valore di un argomento è maggiore dell'intervallo specificato o è un numero negativo, gli altri valori memorizzati verranno modificati di conseguenza. Ad esempio, se la data memorizzata è "5 gennaio 1996 00.00.00.00", e **setUTCHours(30)** viene chiamato, la data viene modificata in "06:00:00.00 6 gennaio 1996".  
  
## <a name="example"></a>Esempio  
 Nell'esempio riportato di seguito viene illustrato l'utilizzo del metodo `setUTCHours`.  
  
```JavaScript  
function SetUTCHoursDemo(nhr, nmin, nsec){     
   var d, s;                        // Declare variables.  
   d = new Date();                  // Create Date object.  
   d.setUTCHours(nhr, nmin, nsec);  // Set UTC hours, minutes, seconds.  
   s = "Current setting is " + d.toUTCString()   
   return(s);                       // Return new setting.  
}  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Si applica a**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getHours (Date)](../../javascript/reference/gethours-method-date-javascript.md)   
 [Metodo getUTCHours (Date)](../../javascript/reference/getutchours-method-date-javascript.md)   
 [Metodo setHours (Date)](../../javascript/reference/sethours-method-date-javascript.md)