---
title: "Proprietà length (String) (JavaScript) | Documenti Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: length Property
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- strings [Visual Studio], length
- Length property
- length property (String)
ms.assetid: 7dbd4a0e-c24e-4561-9b5b-e75e649a10a4
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 706a7f6986086f95613e09b9a8355eb5bc2702a7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="length-property-string-javascript"></a>Proprietà length (String) (JavaScript)
Restituisce la lunghezza di un oggetto `String`.  
  
> [!WARNING]
>  Stringhe JavaScript non sono modificabili, pertanto non può essere modificata la lunghezza di una stringa.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
      strVariable.length  
"String Literal".length   
```  
  
## <a name="remarks"></a>Note  
 Il `length` proprietà contiene un numero intero che indica il numero di caratteri di `String` oggetto. L'ultimo carattere di `String` oggetto dispone di un indice si`length` - 1.  
  
## <a name="example"></a>Esempio  
 Il codice seguente viene illustrato come utilizzare `length`. Le stringhe di JavaScript non sono modificabili e non possono essere modificate sul posto. Tuttavia, è possibile scrivere una stringa invertita in una matrice e quindi chiamare `join` con il carattere vuoto, che produce una stringa senza caratteri separatore.  
  
```JavaScript  
var str = "every good boy does fine";  
        var start = 0;  
        var end = str.length - 1;  
        var tmp = "";  
        var arr = new Array(end);  
  
        while (end >= 0) {  
            arr[start++] = str.charAt(end--);  
        }  
  
// Join the elements of the array with a   
        var str2 = arr.join('');  
        document.write(str2);  
  
// Output: enif seod yob doog yreve  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]