---
title: Metodo getUTCSeconds (Date) (JavaScript) | Documenti Microsoft
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
- getUTCSeconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- UTC times, returning
- seconds method
- getUTCSeconds method
ms.assetid: 2d8ea7dc-79f8-4a9b-b2ab-732db2bcd5fd
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4f398145f8e31ed633bf3215de7d5a5ef669b7ef
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="getutcseconds-method-date-javascript"></a>Metodo getUTCSeconds (Date) (JavaScript)
Ottiene i secondi di un `Date` utilizzando l'ora UTC (Universal Coordinated Time).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
dateObj.getUTCSeconds()   
```  
  
#### <a name="parameters"></a>Parametri  
 Il riferimento `dateObj` obbligatorio è un oggetto `Date` .  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un numero intero compreso tra 0 e 59. Quando il tempo è minore di un secondo il minuto corrente, viene restituito zero. Se un `Date` oggetto è stato creato senza specificare l'ora, per impostazione predefinita, l'ora UTC, il valore dei secondi è 0.  
  
## <a name="remarks"></a>Note  
 Per ottenere il numero di secondi nell'ora locale, utilizzare il `getSeconds` metodo.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come utilizzare il metodo `getUTCSeconds`.  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date. getUTCSeconds());  
  
// Output: 0  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Si applica a**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getSeconds (Date)](../../javascript/reference/getseconds-method-date-javascript.md)   
 [Metodo setSeconds (Date)](../../javascript/reference/setseconds-method-date-javascript.md)   
 [Metodo setUTCSeconds (Date)](../../javascript/reference/setutcseconds-method-date-javascript.md)