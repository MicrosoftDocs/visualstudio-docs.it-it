---
title: "Proprietà leftContext ($') (RegExp) (JavaScript) | Documenti Microsoft"
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
- $`
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- leftContext property ($`)
ms.assetid: 840e56c0-eb7c-461f-bb56-91acff9b5bcf
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b0234a547d2e26c6cf6b1d1a058a46135e577fdd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="leftcontext-property--regexp-javascript"></a>Proprietà leftContext ($`) (RegExp) (JavaScript)
Restituisce i caratteri dall'inizio di una stringa di ricerca fino alla posizione prima dell'inizio dell'ultima corrispondenza. Sola lettura.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
RegExp.leftContext  
```  
  
## <a name="remarks"></a>Note  
 L'oggetto associato a questa proprietà è sempre globale `RegExp` oggetto.  
  
 Il valore iniziale di `leftContext` proprietà è una stringa vuota. Il valore di `leftContext` proprietà cambia ogni volta che viene individuata una corrispondenza.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato l'uso della proprietà `leftContext`:  
  
```JavaScript  
// Create the regular expression pattern.  
var re = new RegExp("d(b+)(d)","ig");  
var str = "cdbBdbsbdbdz";  
  
// Perform the search.  
var arr = re.exec(str);  
  
// Print the output.  
var s = ""   
s += "$1: " + RegExp.$1 + "<br />";  
s += "$2: " + RegExp.$2 + "<br />";  
s += "$3: " + RegExp.$3 + "<br />";  
s += "input: " + RegExp.input + "<br />";  
s += "lastMatch: " + RegExp.lastMatch + "<br />";  
s += "leftContext: " + RegExp.leftContext + "<br />";  
s += "rightContext: " + RegExp.rightContext + "<br />";   
s += "lastParen: " + RegExp.lastParen + "<br />";  
  
document.write(s);  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Si applica a**: [RegExp (oggetto)](../../javascript/reference/regexp-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [$1, la proprietà $9 (RegExp)](../../javascript/reference/dollar-1-dot-dot-dot-dollar-9-properties-regexp-javascript.md)   
 [Proprietà Index (RegExp)](../../javascript/reference/index-property-regexp-javascript.md)   
 [Proprietà input ($_) (RegExp)](../../javascript/reference/input-property-dollar-regexp-javascript.md)   
 [Proprietà lastIndex (RegExp)](../../javascript/reference/lastindex-property-regexp-javascript.md)   
 [Proprietà lastMatch ($&) (RegExp)](../../javascript/reference/lastmatch-property-dollar-regexp-javascript.md)   
 [Proprietà lastParen ($ +) (RegExp)](../../javascript/reference/lastparen-property-dollar-regexp-javascript.md)   
 [Proprietà rightContext ($') (RegExp)](../../javascript/reference/rightcontext-property-dollar-regexp-javascript.md)