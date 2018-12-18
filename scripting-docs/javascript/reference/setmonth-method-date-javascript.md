---
title: Metodo setMonth (Date) (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: setMonth
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Month method
- setMonth method
ms.assetid: 4f5be295-d536-46c0-b3a4-ad06457efe82
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0f2672abebd327af8b0da58d46ebc183b8159711
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="setmonth-method-date-javascript"></a>Metodo setMonth (Date) (JavaScript)
Imposta il valore del mese di `Date` oggetto utilizzando l'ora locale.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
dateObj. setMonth(numMonth[, dateVal])   
```  
  
## <a name="parameters"></a>Parametri  
 `dateObj`  
 Obbligatorio. Qualsiasi oggetto `Date`.  
  
 `numMonth`  
 Obbligatorio. Un valore numerico che rappresenta il mese. Il valore di gennaio è 0 e altri valori di mese seguono consecutivamente.  
  
 `dateVal`  
 Parametro facoltativo. Un valore numerico che rappresenta il giorno del mese. Se questo valore non viene specificato, il valore da una chiamata al `getDate` viene usato il metodo.  
  
## <a name="remarks"></a>Note  
 Per impostare il valore del mese con l'ora UTC (Universal Coordinated Time), utilizzare il `setUTCMonth` metodo.  
  
 Se il valore di `numMonth` è maggiore di 11 (gennaio corrisponde a 0) o è un numero negativo, l'anno memorizzato verrà modificato di conseguenza. Ad esempio, se la data memorizzata è "5 gennaio 1996" e **setMonth(14)** viene chiamato, la data viene modificata in "5 Mar 1997".  
  
 Il **setFullYear** metodo può essere utilizzato per impostare l'anno, mese e giorno del mese.  
  
## <a name="example"></a>Esempio  
 Nell'esempio riportato di seguito viene illustrato l'utilizzo del metodo `setMonth`.  
  
```JavaScript  
date = new Date('1/1/1990');  
date.setMonth(14);  
document.write(date);  
  
// Output: Fri Mar 1 00:00:00 PST 1991  
// Note that the time zone corresponds to the time zone on the local computer.  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Si applica a**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getMonth (Date)](../../javascript/reference/getmonth-method-date-javascript.md)   
 [Metodo getUTCMonth (Date)](../../javascript/reference/getutcmonth-method-date-javascript.md)   
 [Metodo setUTCMonth (Date)](../../javascript/reference/setutcmonth-method-date-javascript.md)