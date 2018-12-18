---
title: Metodo getDay (Date) (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getDay
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- GetDay method
- Date object
- dates, returning day of the week
ms.assetid: 27be7168-3dce-41c9-ae69-6280b7984c2e
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1749eca5aceee76947a0162f22700f32525fdec0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="getday-method-date-javascript"></a>Metodo getDay (Date) (JavaScript)
Ottiene il giorno della settimana, utilizzando l'ora locale.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
dateObj. getDay()   
```  
  
#### <a name="parameters"></a>Parametri  
 Il riferimento `dateObj` obbligatorio è un oggetto `Date` .  
  
## <a name="return-value"></a>Valore restituito  
 Un numero intero compreso tra 0 e 6 che rappresenta il giorno della settimana (domenica è 0, sabato è 6).  
  
## <a name="remarks"></a>Note  
 Per ottenere il giorno utilizzando l'ora UTC (Universal Coordinated Time), utilizzare il `getUTCDay` metodo.  
  
 Nell'esempio seguente viene illustrato come utilizzare il metodo `getDay`.  
  
```JavaScript  
var date = new Date("Saturday, February 9, 2008");  
day = date.getDay();  
document.write(day);  
  
// Output: 6  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Si applica a**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getUTCDay (Date)](../../javascript/reference/getutcday-method-date-javascript.md)