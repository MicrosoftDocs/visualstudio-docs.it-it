---
title: Metodo setTime (Date) (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: setTime
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- SetTime method
- time method
ms.assetid: 86584748-7219-495b-bf56-e27f5782778c
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e66b1fbf5d668330eb727e8bfc50ee9d11a28be3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="settime-method-date-javascript"></a>Metodo setTime (Date) (JavaScript)
Imposta il valore di data e ora nel `Date` oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
dateObj.setTime(milliseconds)   
```  
  
## <a name="parameters"></a>Parametri  
 `dateObj`  
 Obbligatorio. Qualsiasi oggetto `Date`.  
  
 *millisecondi*  
 Obbligatorio. Un valore numerico che rappresenta il numero di millisecondi trascorsi dalla mezzanotte del 1 ° gennaio 1970 GMT.  
  
## <a name="remarks"></a>Note  
 Se *millisecondi* è negativo, viene indicata una data precedente al 1970. L'intervallo di date disponibili è circa 285.616 anni da entrambi i lati del 1970.  
  
 Impostazione della data e ora con il `setTime` metodo è indipendente del fuso orario.  
  
## <a name="example"></a>Esempio  
 Nell'esempio riportato di seguito viene illustrato l'utilizzo del metodo `setTime`.  
  
```JavaScript  
function SetTimeTest(newtime){  
   var d, s;                  //Declare variables.  
   d = new Date();            //Create Date object.  
   d.setTime(newtime);        //Set time.  
   s = "Current setting is ";  
   s += d.toUTCString();  
   return(s);                 //Return new setting.  
}  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Si applica a**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getTime (Date)](../../javascript/reference/gettime-method-date-javascript.md)