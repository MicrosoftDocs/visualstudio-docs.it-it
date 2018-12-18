---
title: Metodo Split (String) (JavaScript) | Documenti Microsoft
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
- split
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- split method
ms.assetid: 7f093336-c887-4efb-b91f-819b6d18a181
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eea90dda2e8e4d52451af247d139eeee44f83917
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="split-method-string-javascript"></a>Metodo split (String) (JavaScript)
Suddivide una stringa in sottostringhe utilizzando il separatore specificato e le restituisce come matrice.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
stringObj.split([separator[, limit]])  
```  
  
## <a name="parameters"></a>Parametri  
 `stringObj`  
 Obbligatorio. Oggetto `String` o valore letterale stringa da suddividere. Questo oggetto non è stato modificato dal **dividere** metodo.  
  
 `separator`  
 Parametro facoltativo. Una stringa o una **espressione regolare** oggetto che identifica uno o più caratteri da utilizzare nella separazione della stringa. Se omesso, verrà restituita una matrice a elemento singolo contenente l'intera stringa.  
  
 `limit`  
 Parametro facoltativo. Valore utilizzato per limitare il numero di elementi restituiti nella matrice.  
  
## <a name="return-value"></a>Valore restituito  
 Il risultato del **dividere** metodo è una matrice di stringhe suddivise in ciascun punto in cui `separator` si verifica `stringObj`. `separator` non verrà restituito come parte di alcun elemento della matrice.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del **dividere** metodo.  
  
```JavaScript  
var s = "The quick brown fox jumps over the lazy dog.";  
var ss = s.split(" ");  
for (var i in ss) {  
    document.write(ss[i]);  
    document.write("<br/>");  
}  
  
// Output:   
// The  
// quick  
// brown  
// fox  
// jumps  
// over  
// the  
// lazy  
// dog.  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Si applica a**: [oggetto stringa](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo concat (String)](../../javascript/reference/concat-method-string-javascript.md)   
 [RegExp (oggetto)](../../javascript/reference/regexp-object-javascript.md)   
 [Oggetto di espressione regolare](../../javascript/reference/regular-expression-object-javascript.md)   
 [Sintassi di espressione regolare (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [App di esempio di scorrimento, panoramica e zoom](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)