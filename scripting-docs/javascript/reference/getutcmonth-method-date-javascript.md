---
title: Metodo getUTCMonth (Date) (JavaScript) | Documenti Microsoft
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
- getUTCMonth
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, UTC
- UTC dates, returning
- Month method
- getUTCMonth method
ms.assetid: eabae139-4da0-4e4a-a4cb-608e6375fc9e
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 07e7ecdc9a9ee8a49c12fc65e4b2ba1056bd377c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="getutcmonth-method-date-javascript"></a>Metodo getUTCMonth (Date) (JavaScript)
Ottiene il mese di un `Date` utilizzando l'ora UTC (Universal Coordinated Time).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
dateObj.getUTCMonth()   
```  
  
#### <a name="parameters"></a>Parametri  
 Il riferimento `dateObj` obbligatorio è un oggetto `Date` .  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un numero intero compreso tra 0 (gennaio) e 11 (dicembre).  
  
## <a name="remarks"></a>Note  
 Per ottenere il mese nell'ora locale, utilizzare il **getMonth** metodo.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come utilizzare il metodo `getUTCMonth`.  
  
```JavaScript  
var date = new Date("2/2/2002");  
document.write(date.getUTCMonth());  
  
// Output: 1  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Si applica a**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getMonth (Date)](../../javascript/reference/getmonth-method-date-javascript.md)   
 [Metodo setMonth (Date)](../../javascript/reference/setmonth-method-date-javascript.md)   
 [Metodo setUTCMonth (Date)](../../javascript/reference/setutcmonth-method-date-javascript.md)