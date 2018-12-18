---
title: Metodo setUTCMonth (Date) (JavaScript) | Documenti Microsoft
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
- setUTCMonth
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, UTC
- setUTCMonth method
- Month method
- UTC dates, setting
ms.assetid: cdac5f64-c4fd-44cc-ba3a-9a8dd3dd3fad
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 02cb69026b66e3f307a8709ab3f5b23d9518643a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="setutcmonth-method-date-javascript"></a>Metodo setUTCMonth (Date) (JavaScript)
Imposta il valore del mese nel `Date` utilizzando l'ora UTC (Universal Coordinated Time).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
dateObj.setUTCMonth(numMonth[, dateVal])   
```  
  
## <a name="parameters"></a>Parametri  
 `dateObj`  
 Obbligatorio. Qualsiasi oggetto `Date`.  
  
 `numMonth`  
 Obbligatorio. Un valore numerico che rappresenta il mese. Il valore di gennaio è 0 e altri valori di mese seguono consecutivamente.  
  
 `dateVal`  
 Parametro facoltativo. Un valore numerico che rappresenta il giorno del mese. Se omesso, il valore da una chiamata al `getUTCDate` viene usato il metodo.  
  
## <a name="remarks"></a>Note  
 Per impostare il valore del mese utilizzando l'ora locale, utilizzare il `setMonth` metodo.  
  
 Se il valore di `numMonth` è maggiore di 11 (gennaio corrisponde a 0) o è un numero negativo, l'anno memorizzato viene incrementato o decrementato in modo appropriato. Ad esempio, se la data memorizzata è "5 gennaio 1996 00.00.00.00", e **setUTCMonth(14)** viene chiamato, la data viene modificata in "5 Mar 1997 00.00.00.00".  
  
 Il **setUTCFullYear** metodo può essere utilizzato per impostare l'anno, mese e giorno del mese.  
  
## <a name="example"></a>Esempio  
 Nell'esempio riportato di seguito viene illustrato l'utilizzo del metodo `setUTCMonth`.  
  
```JavaScript  
function SetUTCMonthDemo(newmonth){  
   var d, s;                       // Declare variables.  
   d = new Date();                 // Create Date object.  
   d.setUTCMonth(newmonth);        // Set UTC month.  
   s = "Current setting is ";  
   s += d.toUTCString();   
   return(s);                      // Return new setting.  
}  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Si applica a**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getMonth (Date)](../../javascript/reference/getmonth-method-date-javascript.md)   
 [Metodo getUTCMonth (Date)](../../javascript/reference/getutcmonth-method-date-javascript.md)   
 [Metodo setMonth (Date)](../../javascript/reference/setmonth-method-date-javascript.md)