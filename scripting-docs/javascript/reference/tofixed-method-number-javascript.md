---
title: Metodo toFixed (Number) (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: toFixed
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: toFixed method
ms.assetid: b5f03400-865e-4ab2-818c-f734c0f6d6f0
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dd51dd67632f4e6417fee72fd19575025423bbf1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="tofixed-method-number-javascript"></a>Metodo toFixed (Number) (JavaScript)
Rappresenta un numero in notazione a virgola fissa.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
numObj.toFixed([fractionDigits])  
```  
  
## <a name="parameters"></a>Parametri  
 `numObj`  
 Richiesto oggetto `Number` oggetto.  
  
 `fractionDigits`  
 Parametro facoltativo. Il numero di cifre dopo il separatore decimale. Deve essere compreso nell'intervallo 0 - 20, inclusivo.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce una rappresentazione di stringa di un numero in notazione a virgola fissa, contenente `fractionDigits` cifre dopo il separatore decimale.  
  
 Se `fractionDigits` viene omesso o **definito**, il valore predefinito è zero.  
  
## <a name="example"></a>Esempio  
 Il codice seguente viene illustrato come utilizzare `toFixed`.  
  
```JavaScript  
var num = new Number(123);  
var fix = num.toFixed();  
document.write(fix);  
document.write("<br/>");  
  
num = new Number(123.456);  
fix = num.toFixed(5);  
document.write(fix);  
  
// Output:  
// 123  
123.45600  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Si applica a**: [numero oggetto](../../javascript/reference/number-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo toExponential (Number)](../../javascript/reference/toexponential-method-number-javascript.md)   
 [Metodo toPrecision (Number)](../../javascript/reference/toprecision-method-number-javascript.md)