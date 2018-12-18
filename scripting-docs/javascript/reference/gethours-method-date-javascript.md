---
title: Metodo getHours (Date) (JavaScript) | Documenti Microsoft
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
- getHours
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Date object
- GetHours method
- Hours method
ms.assetid: c3936496-a213-4d15-b308-d53926ed310c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 87170f96ee6ae6b4a825436717a94749cc336ee0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="gethours-method-date-javascript"></a>Metodo getHours (Date) (JavaScript)
Ottiene le ore in una data, ora locale.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
dateObj.getHours()   
```  
  
#### <a name="parameters"></a>Parametri  
 Il riferimento `dateObj` obbligatorio è un oggetto `Date` .  
  
## <a name="return-value"></a>Valore restituito  
 Un numero intero compreso tra 0 e 23, che indica il numero di ore da mezzanotte. Se l'ora prima 1:00:00 am, sarà restituito zero. Se un `Date` oggetto è stato creato senza specificare l'ora, per impostazione predefinita, l'ora è 0.  
  
## <a name="remarks"></a>Note  
 Per ottenere il valore delle ore nell'ora UTC (Universal Coordinated Time), utilizzare il `getUTCHours` metodo.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come utilizzare il metodo `getHours`.  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getHours());  
document.write("<br/>");  
  
date.setTime(50000000);  
document.write(date.getHours());  
  
// Output:  
// 0   
// 5  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Si applica a**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getUTCHours (Date)](../../javascript/reference/getutchours-method-date-javascript.md)   
 [Metodo setHours (Date)](../../javascript/reference/sethours-method-date-javascript.md)   
 [Metodo setUTCHours (Date)](../../javascript/reference/setutchours-method-date-javascript.md)