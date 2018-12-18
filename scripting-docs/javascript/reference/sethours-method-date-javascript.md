---
title: Metodo setHours (Date) (JavaScript) | Documenti Microsoft
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
- setHours
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- hours
- setHours method
- dates, setting
ms.assetid: 460f742d-f8d2-4874-9d07-2fb969fef066
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f9757f8416953eaf756dba96b91100527606cf9c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="sethours-method-date-javascript"></a>Metodo setHours (Date) (JavaScript)
Imposta il valore di ora il `Date` oggetto utilizzando l'ora locale.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
dateObj.setHours(numHours[, numMin[, numSec[, numMilli]]])   
```  
  
## <a name="parameters"></a>Parametri  
 `dateObj`  
 Obbligatorio. Qualsiasi oggetto `Date`.  
  
 `numHours`  
 Obbligatorio. Valore numerico che rappresenta il valore delle ore.  
  
 `numMin`  
 Parametro facoltativo. Valore numerico che rappresenta il valore dei minuti. È necessario specificare se uno degli argomenti seguenti viene utilizzato.  
  
 `numSec`  
 Parametro facoltativo. Valore numerico che rappresenta il valore dei secondi. È necessario specificare se l'argomento seguente viene utilizzato.  
  
 `numMilli`  
 Parametro facoltativo. Valore numerico che rappresenta il valore dei millisecondi.  
  
## <a name="remarks"></a>Note  
 Tutti **impostare** i metodi che gli argomenti facoltativi utilizzato il valore restituito dal corrispondente **ottenere** metodi, se non si specifica un argomento facoltativo. Ad esempio, se il `numMinutes` argomento non viene specificato, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] utilizza il valore restituito dal `getMinutes` metodo.  
  
 Per impostare il valore delle ore nell'ora UTC (Universal Coordinated Time), utilizzare il `setUTCHours` metodo.  
  
 Se il valore di un argomento è maggiore dell'intervallo specificato o è un numero negativo, gli altri valori memorizzati verranno modificati di conseguenza. Ad esempio, se la data memorizzata è "il 5 gennaio 1996 00:00:00", e **setHours(30)** viene chiamato, la data viene modificata in "6 gennaio 1996 06:00:00." I numeri negativi hanno un comportamento simile.  
  
## <a name="example"></a>Esempio  
 Nell'esempio riportato di seguito viene illustrato l'utilizzo del metodo `setHours`.  
  
```JavaScript  
function SetHoursDemo(nhr, nmin, nsec){  
   var d, s;                     //Declare variables.  
   d = new Date();               //Create Date object.  
   d.setHours(nhr, nmin, nsec);  //Set hours, minutes, & seconds.  
   s = "Current setting is " + d.toLocaleString()   
   return(s);                    //Return new date setting.  
}  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Si applica a**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getHours (Date)](../../javascript/reference/gethours-method-date-javascript.md)   
 [Metodo getUTCHours (Date)](../../javascript/reference/getutchours-method-date-javascript.md)   
 [Metodo setUTCHours (Date)](../../javascript/reference/setutchours-method-date-javascript.md)