---
title: Metodo indexOf (String) (JavaScript) | Documenti Microsoft
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
- indexOf
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- indexOf method, string
- string, indexOf method
ms.assetid: a17372fa-669b-471b-9240-46927a265152
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ecd96acb21f9d7711f9ee00dbf1c1bb70705c0d8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="indexof-method-string-javascript"></a>Metodo indexOf (String) (JavaScript)
Restituisce la posizione della prima occorrenza di una sottostringa.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
strObj. indexOf(subString[, startIndex])  
```  
  
## <a name="parameters"></a>Parametri  
 `strObj`  
 Obbligatorio. Oggetto `String` o valore letterale stringa.  
  
 `subString`  
 Obbligatorio. Sottostringa da cercare nella stringa  
  
 `startIndex`  
 Parametro facoltativo. Indice dal quale iniziare la ricerca dell'oggetto `String`. Se omesso, la ricerca verrà eseguita a partire dall'inizio della stringa.  
  
## <a name="remarks"></a>Note  
 Il **indexOf** il metodo restituisce l'inizio della sottostringa nel `String` oggetto. Se la ricerca ha esito negativo, verrà restituito -1.  
  
 Se `startindex` è negativo, `startindex` viene considerato pari a zero. Se è maggiore dell'indice più alto, viene considerato come l'indice più alto.  
  
 La ricerca viene eseguita da sinistra a destra. In caso contrario, questo metodo è identico a **lastIndexOf**.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del **indexOf** metodo.  
  
```JavaScript  
var str = "original equipment manufacturer";  
  
var s = "equip is at position " + str.indexOf("equip");  
s += "<br />";  
s += "abc is at position " + str.indexOf("abc");  
  
document.write(s);  
  
// Output:  
// equip is at position 9  
// abc is at position -1  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Si applica a**: [oggetto stringa](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo lastIndexOf (String)](../../javascript/reference/lastindexof-method-string-javascript.md)   
 [App di esempio di scorrimento, panoramica e zoom](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)