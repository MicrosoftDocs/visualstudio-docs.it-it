---
title: Metodo toPrecision (Number) (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: toPrecision
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: toPrecision method
ms.assetid: ac13c82f-1038-447a-823f-f755bba535ca
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eeab7642dcd88677d1b5a7102e3cf342d7ee1d29
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="toprecision-method-number-javascript"></a>Metodo toPrecision (Number) (JavaScript)
Rappresenta un numero in notazione esponenziale o a virgola fissa con un numero di cifre specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
numObj.toPrecision([precision])  
```  
  
## <a name="parameters"></a>Parametri  
 `numObj`  
 Obbligatorio. Oggetto `Number`.  
  
 `precision`  
 Parametro facoltativo. Il numero di cifre significative. Deve essere compreso nell'intervallo 1-21, inclusivo.  
  
## <a name="return-value"></a>Valore restituito  
 Per i numeri nella notazione esponenziale, `precision` - 1 vengono restituite le cifre dopo il separatore decimale. Per i numeri nella notazione fissa, `precision` vengono restituite le cifre significative.  
  
 Se `precision` viene omesso o è **definito**, **toString** viene invece chiamato il metodo.  
  
## <a name="example"></a>Esempio  
 Il codice seguente viene illustrato come utilizzare `toPrecision`.  
  
```JavaScript  
var num = new Number(123);  
var prec = num.toPrecision();  
document.write(prec);  
document.write("<br/>");  
  
num = new Number(123.456);  
prec = num.toPrecision(5);  
document.write(prec);  
  
// Output:  
// 123  
// 123.46  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Si applica a**: [numero oggetto](../../javascript/reference/number-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo toFixed (Number)](../../javascript/reference/tofixed-method-number-javascript.md)   
 [Metodo toExponential (Number)](../../javascript/reference/toexponential-method-number-javascript.md)