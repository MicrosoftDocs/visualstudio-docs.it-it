---
title: Metodo getMonth (Date) (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getMonth
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Date object
- dates, month value
- Month method
- GetMonth method
ms.assetid: c20dd8ba-1d78-42f1-8717-ed3dfd2362dd
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eeffd7ffc7bee5fa63607e342a9a9dced7088d35
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="getmonth-method-date-javascript"></a>Metodo getMonth (Date) (JavaScript)
Ottiene il mese, utilizzando l'ora locale.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
dateObj.getMonth()   
```  
  
#### <a name="parameters"></a>Parametri  
 Il riferimento `dateObj` obbligatorio è un oggetto `Date` .  
  
## <a name="return-value"></a>Valore restituito  
 Il `getMonth` metodo restituisce un numero intero compreso tra 0 (gennaio) e 11 (dicembre). Per un `Date` costruito con "5 gennaio 1996", `getMonth` restituisce 0.  
  
## <a name="remarks"></a>Note  
 Per ottenere il valore del mese con l'ora UTC (Universal Coordinated Time), utilizzare il `getUTCMonth` metodo.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come utilizzare il metodo `getMonth`.  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getMonth());  
  
// Output: 0  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Si applica a**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getUTCMonth (Date)](../../javascript/reference/getutcmonth-method-date-javascript.md)   
 [Metodo setMonth (Date)](../../javascript/reference/setmonth-method-date-javascript.md)   
 [Metodo setUTCMonth (Date)](../../javascript/reference/setutcmonth-method-date-javascript.md)