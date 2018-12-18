---
title: Metodo getDate (Date) (JavaScript) | Documenti Microsoft
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
- getDate
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Date object
- dates, returning day of the month
- getDate method
ms.assetid: 67e7f07c-dd46-4b42-82d6-e53e4bd33703
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bfb3a8ad3ba433dc776f0831d1eac4787b8aea90
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="getdate-method-date-javascript"></a>Metodo getDate (Date) (JavaScript)
Ottiene il giorno-di-mese, utilizzando l'ora locale.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
dateObj.getDate()   
```  
  
#### <a name="parameters"></a>Parametri  
 Il riferimento `dateObj` obbligatorio è un oggetto `Date` .  
  
## <a name="return-value"></a>Valore restituito  
 Valore intero compreso tra 1 e 31 che rappresenta il giorno-di-mese.  
  
## <a name="remarks"></a>Note  
 Per ottenere il giorno-di-mese utilizzando Universal Coordinated Time (UTC), utilizzare il `getUTCDate` metodo.  
  
## <a name="example"></a>Esempio  
 Nell'esempio riportato di seguito viene illustrato l'utilizzo del metodo `getDate`.  
  
```JavaScript  
var date = new Date("Jan 01, 2001");  
var str = "Today's date is: ";  
   str += (date.getMonth() + 1) + "/";  
   str += date.getDate() + "/";  
   str += date.getFullYear();  
document.write(str);  
  
// Output: Today's date is: 1/1/2001  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Si applica a**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getUTCDate (Date)](../../javascript/reference/getutcdate-method-date-javascript.md)   
 [Metodo setDate (Date)](../../javascript/reference/setdate-method-date-javascript.md)   
 [Metodo setUTCDate (Date)](../../javascript/reference/setutcdate-method-date-javascript.md)