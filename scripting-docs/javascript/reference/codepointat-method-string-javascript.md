---
title: Metodo codePointAt (String) (JavaScript) | Documenti Microsoft
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
ms.assetid: 7979018f-1be3-4a13-9e8f-c84c7ed35288
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0dd5ef17db177dfb1d532bfb88d1d0d77cdb7304
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="codepointat-method-string-javascript"></a>Metodo codePointAt (String) (JavaScript)
Restituisce il punto di codice relativo a un carattere UTF-16 Unicode.  
  
## <a name="syntax"></a>Sintassi  
  
```  
stringObj.codePointAt(pos);  
```  
  
#### <a name="parameters"></a>Parametri  
 `stringObj`  
 Obbligatorio. Oggetto stringa.  
  
 `pos`  
 Obbligatorio. Posizione del carattere.  
  
## <a name="remarks"></a>Note  
 Questo metodo restituisce i valori dei punti di codice, tra cui i punti di codice "astrali" (punti di codice con più di quattro valori esadecimali), per tutti i caratteri UTF-16.  
  
 Se `pos` è minore di zero (0) o maggiore delle dimensioni della stringa, il valore restituito è `undefined`.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come utilizzare il metodo `codePointAt`.  
  
```JavaScript  
var cp1 = "𠮷".codePointAt(0);  
var cp2 = 'abc'.codePointAt(1);  
  
if(console && console.log) {  
    console.log(cp1);  
    console.log(cp2);}  
  
// Output:  
// 0x20BB7  
// 98   
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]
