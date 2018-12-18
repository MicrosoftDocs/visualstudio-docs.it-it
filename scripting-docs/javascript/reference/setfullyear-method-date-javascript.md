---
title: Metodo setFullYear (Date) (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: setFullYear
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Year method
- setFullYear method
- dates, setting
ms.assetid: 635e4f5a-0210-4c01-8152-b0da4146f6ff
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e5e20a8486d1aefeab9b244c5f1e9d1b1e60c3f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="setfullyear-method-date-javascript"></a>Metodo setFullYear (Date) (JavaScript)
Imposta l'anno del `Date` oggetto utilizzando l'ora locale.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
dateObj.setFullYear(numYear[, numMonth[, numDate]])   
```  
  
## <a name="parameters"></a>Parametri  
 `dateObj`  
 Obbligatorio. Qualsiasi oggetto `Date`.  
  
 `numYear`  
 Obbligatorio. Un valore numerico per l'anno.  
  
 `numMonth`  
 Parametro facoltativo. Un valore numerico in base zero per il mese (da 0 per gennaio, 11 per dicembre). Deve essere specificato se `numDate` è specificato.  
  
 `numDate`  
 Parametro facoltativo. Valore numerico per il giorno del mese.  
  
## <a name="remarks"></a>Note  
 Tutti **impostare** i metodi che gli argomenti facoltativi utilizzato il valore restituito dal corrispondente **ottenere** metodi, se non si specifica l'argomento facoltativo. Ad esempio, se il `numMonth` argomento è facoltativo, ma non viene specificato, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] utilizza il valore restituito dal **getMonth** metodo.  
  
 Inoltre, se il valore di un argomento è maggiore dell'intervallo di calendario o è negativo, la data esegue il rollup in avanti o indietro come appropriato.  
  
 Per impostare l'anno utilizzando l'ora UTC (Universal Coordinated Time), utilizzare il `setUTCFullYear` metodo.  
  
 L'intervallo di anni supportato nell'oggetto date è pari a circa 285.616 anni prima e dopo 1970.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del `setFullYear` metodo:  
  
```JavaScript  
var date1 = new Date("1/1/2001");  
date1.setFullYear(2007);  
  
var date2 = new Date("1/1/2001");  
date2.setFullYear(2008, 10, 3);   
  
document.write (date1.toLocaleString());  
document.write ("<br />");  
document.write (date2.toLocaleString());  
  
// Output:  
// Monday, January 01, 2007 12:00:00 AM  
// Monday, November 03, 2008 12:00:00 AM  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Si applica a**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getFullYear (Date)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [Metodo getUTCFullYear (Date)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [Metodo setUTCFullYear (Date)](../../javascript/reference/setutcfullyear-method-date-javascript.md)