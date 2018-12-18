---
title: Metodo toExponential (Number) (JavaScript) | Documenti Microsoft
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
- toExponential
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toExponential method
ms.assetid: 7c4a6d84-3c1f-4cc4-a67d-7753e5d4ed66
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fff2f2bc0c443fa9308c8d01dcea42a3cec9ff04
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="toexponential-method-number-javascript"></a>Metodo toExponential (Number) (JavaScript)
Rappresenta un numero in notazione esponenziale.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
numObj. toExponential([fractionDigits])  
```  
  
## <a name="parameters"></a>Parametri  
 `numObj`  
 Obbligatorio. Oggetto **numero** oggetto.  
  
 `fractionDigits`  
 Parametro facoltativo. Il numero di cifre dopo il separatore decimale. Deve essere compreso nell'intervallo 0 - 20, inclusivo.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce una rappresentazione di stringa di un numero in notazione esponenziale. La stringa contiene una cifra prima del separatore decimale e può contenere `fractionDigits` dopo di esso.  
  
 Se `fractionDigits` non viene fornito il `toExponential` metodo restituisce il numero di cifre è necessario specificare in modo univoco il numero.  
  
## <a name="example"></a>Esempio  
  
```JavaScript  
var num = new Number(123);  
var exp = num.toExponential();  
document.write(exp);  
document.write("<br/>");  
  
num = new Number(123.456);  
exp = num.toExponential(5);  
document.write(exp);  
  
// Output:   
// 1.23e+2  
// 1.23456e+2  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Si applica a**: [numero oggetto](../../javascript/reference/number-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo toFixed (Number)](../../javascript/reference/tofixed-method-number-javascript.md)   
 [Metodo toPrecision (Number)](../../javascript/reference/toprecision-method-number-javascript.md)