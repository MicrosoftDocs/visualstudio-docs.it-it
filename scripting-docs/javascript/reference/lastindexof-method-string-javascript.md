---
title: Metodo lastIndexOf (String) (JavaScript) | Documenti Microsoft
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
- lastIndexOf
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- lastIndexOf method, string
- string, lastIndexOf method
ms.assetid: 1ed36ccd-0f0b-4f16-be45-0567207670af
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0fa0f35e970435a4d0296493c20afdeaac128cae
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="lastindexof-method-string-javascript"></a>Metodo lastIndexOf (String) (JavaScript)
Restituisce l'ultima occorrenza di una sottostringa nella stringa.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
strObj.lastIndexOf(substring[, startindex])  
```  
  
## <a name="parameters"></a>Parametri  
 `strObj`  
 Obbligatorio. Oggetto `String` o valore letterale stringa.  
  
 `substring`  
 Obbligatorio. La sottostringa da cercare.  
  
 `startindex`  
 Parametro facoltativo. Indice in corrispondenza del quale iniziare la ricerca. Se omesso, la ricerca inizia alla fine della stringa.  
  
## <a name="remarks"></a>Note  
 Il **lastIndexOf** il metodo restituisce un valore intero che indica l'inizio della sottostringa all'interno di `String` oggetto. Se la sottostringa non viene trovata, viene restituito -1.  
  
 Se `startindex` è negativo, `startindex` viene considerato pari a zero. Se è maggiore dell'indice di posizione di carattere maggiore, viene considerato l'indice più grande possibile.  
  
 La ricerca viene eseguita iniziando l'ultimo carattere nella stringa. In caso contrario, questo metodo è identico a **indexOf**.  
  
 Nell'esempio seguente viene illustrato l'utilizzo del **lastIndexOf** metodo.  
  
```JavaScript  
var str = "time, time";  
  
var s = "";  
s += "time is at position " + str.lastIndexOf("time");  
s += "<br />";  
s += "abc is at position " + str.lastIndexOf("abc");  
  
document.write(s);  
  
// Output:  
// time is at position 6  
// abc is at position -1  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Si applica a**: [oggetto stringa](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo indexOf (String)](../../javascript/reference/indexof-method-string-javascript.md)