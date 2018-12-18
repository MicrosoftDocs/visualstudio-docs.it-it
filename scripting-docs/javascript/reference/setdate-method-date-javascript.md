---
title: Metodo setDate (Date) (JavaScript) | Documenti Microsoft
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
- setDate
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- setDate method
- dates, setting
ms.assetid: a84b9b01-a6d0-489f-8a13-e7af9e9630b2
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8d74340287b3a7348419d302f79775eb610c6983
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="setdate-method-date-javascript"></a>Metodo setDate (Date) (JavaScript)
Imposta il valore numerico giorno del mese del `Date` oggetto utilizzando l'ora locale.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
dateObj.setDate(numDate)   
```  
  
## <a name="parameters"></a>Parametri  
 `dateObj`  
 Obbligatorio. Qualsiasi oggetto `Date`.  
  
 `numDate`  
 Obbligatorio. Valore numerico che rappresenta il giorno del mese.  
  
## <a name="remarks"></a>Note  
 Per impostare il valore del giorno del mese con l'ora UTC (Universal Coordinated Time), utilizzare il `setUTCDate` metodo.  
  
 Se il valore di `numDate` è maggiore del numero di giorni del mese, esegue il rollback data in a una versione successiva mese e/o anno. Ad esempio, se la data memorizzata è 5 gennaio 1996 e `setDate(32)` viene chiamato, le modifiche data 1 febbraio 1996. Se `numDate` è un numero negativo, il Data esegue il rollback un precedente mese e/o anno. Ad esempio, se la data memorizzata è 5 gennaio 1996 e `setDate(-32)` viene chiamato, le modifiche data 29 novembre 1995.  
  
 Il [metodo setFullYear (Date)](../../javascript/reference/setfullyear-method-date-javascript.md) può essere utilizzato per impostare l'anno, mese e giorno del mese.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come utilizzare il metodo `setDate`.  
  
```JavaScript  
var date = new Date("12/15/1990");  
date.setDate(30);  
document.write(date);  
  
// Output (for the PST time zone): Sun Dec 30 00:00:00 PST 1990  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Si applica a**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getDate (Date)](../../javascript/reference/getdate-method-date-javascript.md)   
 [Metodo setFullYear (Date)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [Metodo setMonth (Date)](../../javascript/reference/setmonth-method-date-javascript.md)   
 [Metodo setUTCDate (Date)](../../javascript/reference/setutcdate-method-date-javascript.md)