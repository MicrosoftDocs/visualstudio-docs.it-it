---
title: Metodo concat (String) (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: concat
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- concat method (String)
- Concat method
ms.assetid: 5d28ebb2-d534-4179-9297-a4c821ee9f24
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1b6419cc6404e06fc780802a30a3b4add8320881
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="concat-method-string-javascript"></a>Metodo concat (String) (JavaScript)
Restituisce una stringa che contiene la concatenazione di due o più stringhe.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
string1. concat([string2[, string3[, . . . [, stringN]]]])  
```  
  
## <a name="parameters"></a>Parametri  
 `string1`  
 Obbligatorio. Il `String` o valore letterale stringa a cui tutti gli altri specificato stringhe vengono concatenate.  
  
 `string2,. . ., stringN`  
 Parametro facoltativo. Le stringhe da aggiungere alla fine di `string1`.  
  
## <a name="remarks"></a>Note  
 Il risultato di `concat` metodo è equivalente a: `result`  =  `string1`  +  `string2`  +  `string3`  +  `stringN`. Modifica del valore nella stringa di origine o di risultato non influirà sul valore di altra stringa. Se uno degli argomenti non sono stringhe, vengono innanzitutto convertiti in stringhe prima di essere concatenato a `string1`.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del `concat` metodo con una stringa:  
  
```JavaScript  
var str1 = "ABCD"  
var str2 = "EFGH";  
var str3 = "1234";  
var str4 = "5678";  
document.write(str1.concat(str2, str3, str4));  
  
// Output: "ABCDEFGH12345678"  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Si applica a**: [oggetto stringa](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Operatore addizione (+)](../../javascript/reference/addition-operator-decrement-javascript.md)