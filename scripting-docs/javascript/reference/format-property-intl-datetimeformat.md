---
title: "Proprietà (intl. DateTimeFormat) Format | Documenti Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 487930fe-a948-446f-902d-06bb0d7685d5
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2e94fcd797a63944d0162dceadf773cf9b15f943
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="format-property-intldatetimeformat"></a>Proprietà format (Intl.DateTimeFormat)
Restituisce una funzione che formatta una data specifica delle impostazioni locali utilizzando le impostazioni del formattatore di data e l'ora specificate.  
  
## <a name="syntax"></a>Sintassi  
  
```  
dateTimeFormatObj.format  
```  
  
#### <a name="parameters"></a>Parametri  
 `dateTimeFormatObj`  
 Obbligatorio. Il nome del `DateTimeFormat` oggetto da usare come un formattatore.  
  
## <a name="remarks"></a>Note  
 La funzione restituita dal `format` proprietà accetta un solo argomento, `date`e restituisce una stringa che rappresenta la data localizzata utilizzando le opzioni specificate nel `DateTimeFormat` oggetto. Il `date` parametro della funzione restituita deve essere un numero, stringa della data o un `Date` oggetto. Se `date` non viene fornito, viene utilizzata la funzione [Date.now](../../javascript/reference/date-now-function-javascript.md) come valore di input predefinito.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene utilizzato un `DateTimeFormat` per localizzare la data "1 dicembre 2007" in tedesco e riformattarlo.  
  
```JavaScript  
var dtFormat = new Intl.DateTimeFormat(["de"], {  
    year: "numeric",  
    month: "long",  
    day: "2-digit",  
    hour: "numeric"  
});  
  
if (console && console.log) {  
    console.log(dtFormat.format(new Date("Dec 1, 2007")));  
    // Returns 01. Dezember 2007 00:00  
}  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Intl.DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md)