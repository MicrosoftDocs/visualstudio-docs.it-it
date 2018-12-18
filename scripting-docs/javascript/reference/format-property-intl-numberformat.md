---
title: "Proprietà (intl. NumberFormat) Format | Documenti Microsoft"
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
ms.assetid: 68c3223a-023c-4fa0-aa99-d049a7a0e26a
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: be40f8e94220ad7504dd3b9736e71b3416bb3d2a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="format-property-intlnumberformat"></a>Proprietà format (Intl.NumberFormat)
Restituisce una funzione che formatta un numero di specifiche delle impostazioni locali utilizzando le impostazioni di formattatore numero specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
numberFormatObj.format  
```  
  
#### <a name="parameters"></a>Parametri  
 `numberFormatObj`  
 Obbligatorio. Il nome del `NumberFormat` oggetto da usare come un formattatore.  
  
## <a name="remarks"></a>Note  
 La funzione restituita dal `format` proprietà accetta un solo argomento, `value`e restituisce una stringa che rappresenta il numero della localizzata utilizzando le opzioni specificate nel `NumberFormat` oggetto. Se `value` viene omesso, la funzione restituisce `NaN` (non un numero).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene utilizzato un `NumberFormat` oggetto per creare un numero localizzato.  
  
```JavaScript  
var nf = new Intl.NumberFormat(["en-US"], {  
    style: "currency",  
    currency: "CNY",  
    currencyDisplay: "symbol",  
    maximumFractionDigit: 1  
})  
  
if (console && console.log) {  
    console.log(nf.format(100)); // "¥100.00"  
}  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Intl.NumberFormat](../../javascript/reference/intl-numberformat-object-javascript.md)