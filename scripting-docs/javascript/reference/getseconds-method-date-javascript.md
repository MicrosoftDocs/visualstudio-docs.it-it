---
title: Metodo getSeconds (Date) (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getSeconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- seconds method
- GetSeconds method
ms.assetid: 97b10674-af0b-4681-a846-38f972196501
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 151d720b92fb9d7068c320983a25b965078f1b2e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="getseconds-method-date-javascript"></a>Metodo getSeconds (Date) (JavaScript)
Ottiene i secondi di un `Date` dell'oggetto, utilizzando l'ora locale.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
dateObj.getSeconds()   
```  
  
#### <a name="parameters"></a>Parametri  
 Il riferimento `dateObj` obbligatorio è un oggetto `Date` .  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un numero intero compreso tra 0 e 59. Quando il tempo è minore di un secondo il minuto corrente, viene restituito zero. Se un `Date` oggetto è stato creato senza specificare l'ora, per impostazione predefinita, il valore dei secondi è 0.  
  
## <a name="remarks"></a>Note  
 Per ottenere i secondi come valore utilizzando l'ora UTC (Universal Coordinated Time), utilizzare il `getUTCSeconds` metodo.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come utilizzare il metodo `getSeconds`.  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getSeconds());  
document.write("<br/>");  
  
date.setSeconds(5);  
document.write(date.getSeconds());  
  
// Output:  
// 0  
// 5  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Si applica a**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getUTCSeconds (Date)](../../javascript/reference/getutcseconds-method-date-javascript.md)   
 [Metodo setSeconds (Date)](../../javascript/reference/setseconds-method-date-javascript.md)   
 [Metodo setUTCSeconds (Date)](../../javascript/reference/setutcseconds-method-date-javascript.md)