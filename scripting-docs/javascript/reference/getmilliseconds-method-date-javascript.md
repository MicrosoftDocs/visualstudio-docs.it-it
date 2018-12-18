---
title: Metodo getMilliseconds (Date) (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getMilliseconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- milliseconds
- getMilliseconds method
ms.assetid: 1b512146-1e8a-44a4-89da-6cc5338d15cb
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 33e5fc54dffbe06e47f0978e6cef94b1f650c90f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="getmilliseconds-method-date-javascript"></a>Metodo getMilliseconds (Date) (JavaScript)
Ottiene il numero di millisecondi di una data, ora locale.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
dateObj.getMilliseconds()   
```  
  
#### <a name="parameters"></a>Parametri  
 Il riferimento `dateObj` obbligatorio è un oggetto `Date` .  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce il numero di millisecondi di una data. Il valore può essere compreso tra 0 e 999. Se una data è stata creata senza specificare il numero di millisecondi, il valore restituito è 0.  
  
## <a name="remarks"></a>Note  
 Per ottenere il numero di millisecondi in base al formato UTC (Coordinated Universal Time Coordinated), utilizzare il `getUTCMilliseconds` metodo.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come utilizzare il **getMilliseconds** metodo.  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getMilliseconds());  
document.write("<br/>");  
  
date.setMilliseconds(5);  
document.write(date.getMilliseconds());  
// Output:   
// 0  
// 5  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Si applica a**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getUTCMilliseconds (Date)](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)   
 [Metodo setMilliseconds (Date)](../../javascript/reference/setmilliseconds-method-date-javascript.md)   
 [Metodo setUTCMilliseconds (Date)](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)