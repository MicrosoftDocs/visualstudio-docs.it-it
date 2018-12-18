---
title: Metodo getUTCMilliseconds (Date) (JavaScript) | Documenti Microsoft
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
- getUTCMilliseconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- milliseconds
- UTC times, returning
- getUTCMilliseconds method
ms.assetid: 7491d387-7b6a-40df-89e5-55c64795ef70
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3fb7cf202c8511bec00c10dc5b8c23bd198d8700
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="getutcmilliseconds-method-date-javascript"></a>Metodo getUTCMilliseconds (Date) (JavaScript)
Ottiene il numero di millisecondi di un `Date` utilizzando l'ora UTC (Universal Coordinated Time).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
dateObj.getUTCMilliseconds()   
```  
  
#### <a name="parameters"></a>Parametri  
 Il riferimento `dateObj` obbligatorio è un oggetto `Date` .  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un valore in millisecondi che può essere compreso tra 0 e 999.  
  
## <a name="remarks"></a>Note  
 Per ottenere il numero di millisecondi nell'ora locale, utilizzare il `getMilliseconds` metodo.  
  
## <a name="example"></a>Esempio  
 Nell'esempio riportato di seguito viene illustrato l'utilizzo del metodo `getUTCMilliseconds`.  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getUTCMilliseconds());  
document.write("<br/>");  
  
date.setMilliseconds(34);  
document.writedate.getUTCMilliseconds());  
  
// Output:  
// 0   
// 34   
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Si applica a**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getMilliseconds (Date)](../../javascript/reference/getmilliseconds-method-date-javascript.md)   
 [Metodo setMilliseconds (Date)](../../javascript/reference/setmilliseconds-method-date-javascript.md)   
 [Metodo setUTCMilliseconds (Date)](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)