---
title: Metodo setUTCFullYear (Date) (JavaScript) | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- setUTCFullYear
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, UTC
- setUTCFullYear method
- UTC dates, setting
ms.assetid: e6c51b49-0149-4f9a-aa74-c73c0306f98e
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2dda8b75dd8bc8dac87ea383546f392b064c1d63
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="setutcfullyear-method-date-javascript"></a>Metodo setUTCFullYear (Date) (JavaScript)
Imposta il valore dell'anno di `Date` utilizzando l'ora UTC (Universal Coordinated Time).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
dateObj.setUTCFullYear(numYear[, numMonth[, numDate]])   
```  
  
## <a name="parameters"></a>Parametri  
 `dateObj`  
 Obbligatorio. Qualsiasi oggetto `Date`.  
  
 `numYear`  
 Obbligatorio. Valore numerico che rappresenta l'anno.  
  
 `numMonth`  
 Parametro facoltativo. Un valore numerico che rappresenta il mese. Il valore di gennaio è 0 e altri valori di mese seguono consecutivamente. È necessario specificare se *numDate* fornito.  
  
 *numDate*  
 Parametro facoltativo. Valore numerico che rappresenta il giorno del mese.  
  
## <a name="remarks"></a>Note  
 Tutti **impostare** i metodi che gli argomenti facoltativi utilizzato il valore restituito dal corrispondente **ottenere** metodi, se non si specifica un argomento facoltativo. Ad esempio, se il `numMonth` argomento non viene specificato, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] utilizza il valore restituito dal `getUTCMonth` metodo.  
  
 Inoltre, se il valore di un argomento è maggiore che l'intervallo o è un numero, altre stored i valori negativi vengono modificati di conseguenza.  
  
 Per impostare l'anno utilizzando l'ora locale, utilizzare il `setFullYear` metodo.  
  
 L'intervallo di anni supportato il `Date` oggetto è di circa 285.616 anni da entrambi i lati del 1970.  
  
## <a name="example"></a>Esempio  
 Nell'esempio riportato di seguito viene illustrato l'utilizzo del metodo `setUTCFullYear`.  
  
```JavaScript  
var dtFirst = new Date();  
dtFirst.setUTCFullYear(2007);  
  
var dtSecond = new Date();  
// 10 is the value for November.   
dtSecond.setUTCFullYear(2008, 10, 3);   
  
document.write (dtFirst.toUTCString());  
document.write ("<br />");  
document.write (dtSecond.toUTCString());  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Si applica a**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getFullYear (Date)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [Metodo getUTCFullYear (Date)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [Metodo setFullYear (Date)](../../javascript/reference/setfullyear-method-date-javascript.md)