---
title: Metodo setUTCDate (Date) (JavaScript) | Documenti Microsoft
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
- setUTCDate
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, UTC
- dates, setting
- UTC dates, setting
- setUTCDate method
ms.assetid: e6c3b876-70fe-4103-b197-6c84c078ce10
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5631a36c8b1c4f1ee50dcadb39f0f21ae5aa28e3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="setutcdate-method-date-javascript"></a>Metodo setUTCDate (Date) (JavaScript)
Imposta il valore numerico del giorno del mese nel `Date` utilizzando l'ora UTC (Universal Coordinated Time).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
dateObj.setUTCDate(numDate)   
```  
  
## <a name="parameters"></a>Parametri  
 `dateObj`  
 Obbligatorio. Qualsiasi oggetto `Date`.  
  
 *numDate*  
 Obbligatorio. Valore numerico che rappresenta il giorno del mese.  
  
## <a name="remarks"></a>Note  
 Per impostare il giorno del mese utilizzando l'ora locale, utilizzare il `setDate` metodo.  
  
 Se il valore di *numDate* è maggiore del numero di giorni del mese memorizzato nel **data** dell'oggetto o un numero negativo, la data è impostata su un valore uguale a *numDate* meno il numero di giorni del mese memorizzato. Ad esempio, se la data memorizzata è il 5 gennaio 1996 e **setUTCDate(32)** viene chiamato, le modifiche data 1 febbraio 1996. I numeri negativi hanno un comportamento simile.  
  
 Il **setUTCFullYear** metodo può essere utilizzato per impostare l'anno, mese e giorno del mese.  
  
## <a name="example"></a>Esempio  
 Nell'esempio riportato di seguito viene illustrato l'utilizzo del metodo `setUTCDate`.  
  
```JavaScript  
function SetUTCDateDemo(newdayofmonth){  
   var d = new Date();           // Create Date object.  
   d.setUTCDate(newdayofmonth);  // Set UTC day of month.  
   var s = "Current setting is ";  
   s += d.toUTCString();   
   return(s);                    // Return new setting.  
}  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Si applica a**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getDate (Date)](../../javascript/reference/getdate-method-date-javascript.md)   
 [Metodo getUTCDate (Date)](../../javascript/reference/getutcdate-method-date-javascript.md)   
 [Metodo setDate (Date)](../../javascript/reference/setdate-method-date-javascript.md)