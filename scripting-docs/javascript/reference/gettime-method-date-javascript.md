---
title: Metodo getTime (Date) (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getTime
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- GetTime method
- time method
ms.assetid: f0da1d4e-337c-497d-9205-093defbc6d3d
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a31e542445e89a0e2f3364d36ae44f8d2d4cf9bb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="gettime-method-date-javascript"></a>Metodo getTime (Date) (JavaScript)
Ottiene il valore di tempo in millisecondi.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
dateObj.getTime()   
```  
  
#### <a name="parameters"></a>Parametri  
 Il riferimento `dateObj` obbligatorio è un oggetto `Date` .  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce il numero di millisecondi tra la mezzanotte dell'1 gennaio 1970 e il valore di ora il `Date` oggetto. L'intervallo di date è circa 285.616 anni da entrambi i lati della mezzanotte dell'1 gennaio 1970. I numeri negativi indicano date precedenti al 1970.  
  
## <a name="remarks"></a>Note  
 Quando si esegue più calcoli di data e ora, si desidera definire variabili uguale al numero di millisecondi in un giorno, ore o minuti. Ad esempio:  
  
```JavaScript  
var minute = 1000 * 60;  
var hour = minute * 60;  
var day = hour * 24;  
```  
  
 Vedere [il calcolo di date e ore (JavaScript)](../../javascript/calculating-dates-and-times-javascript.md) per ulteriori informazioni sull'utilizzo di `getTime` metodo.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come utilizzare il metodo `getTime`.  
  
```JavaScript  
var minute = 1000 * 60;  
var hour = minute * 60;  
var day = hour * 24;  
  
date = new Date("1/1/2001");  
var time = date.getTime();  
  
document.write(Math.round(time / day) + " days from 1/1/1970 to 1/1/2001");  
  
// Output: 11323 days from 1/1/1970 to 1/1/2001  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Si applica a**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo setTime (Date)](../../javascript/reference/settime-method-date-javascript.md)