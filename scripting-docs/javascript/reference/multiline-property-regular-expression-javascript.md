---
title: "Proprietà Multiline (Regular Expression) (JavaScript) | Documenti Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: multiline
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: multiline property
ms.assetid: ca7b276a-1fe2-4189-ac27-f089ab3e9974
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 289cb8d8e103d8c4ac1b1ef06714105d21cba743
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="multiline-property-regular-expression-javascript"></a>Proprietà multiline (Regular Expression) (JavaScript)
Restituisce un valore booleano che indica lo stato del flag multiline (**m**) utilizzato con un'espressione regolare. Valore predefinito è **false**. Sola lettura.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
rgExp.multiline  
```  
  
## <a name="remarks"></a>Note  
 Obbligatorio `rgExp` argomento è un'istanza di `RegExp` oggetto  
  
 Il **multiriga** restituisce proprietà **true** se per un'espressione regolare è impostato il flag su più righe e restituisce **false** in caso contrario. Il **multiriga** proprietà **true** se è stato creato l'oggetto di espressione regolare con la **m** flag.  
  
 Se **multiriga** è **false**, "^" corrisponde alla posizione all'inizio di una stringa e "$" alla posizione in corrispondenza della fine di una stringa. Se **multiriga** è **true**, "^" corrisponde alla posizione all'inizio di una stringa e a quella che segue un "\n" o "\r" e "$" corrisponde alla posizione alla fine di una stringa e la posizione che precede "\n "o"\r".  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato il comportamento del **multiriga** proprietà. Se "m" viene passato alla funzione illustrata di seguito, la parola "while" viene sostituita con la parola "e". Questo avviene perché è impostato con il flag su più righe e la parola "while" si verifica all'inizio della riga dopo un carattere di nuova riga. Il flag su più righe consente la ricerca da eseguire sulle stringhe su più righe.  
  
```JavaScript  
function RegExpMultilineDemo(flag){  
   // The flag parameter is a string that contains  
   // g, i, or m.  The flags can be combined.  
  
   // Check flags for validity.  
   if (flag.match(/[^gim]/))  
      {  
      return ("Flag specified is not valid");  
      }  
  
   // Create the string on which to perform the replacement.  
   var ss = "The man hit the ball with the bat ";  
   ss += "\nwhile the fielder caught the ball with the glove.";  
  
   // Replace "while" with "and".  
   var re = new RegExp("^while", flag);  
   var r = ss.replace(re, "and");          
  
   // Output the multiline flag and the resulting string.  
   var s = "";  
   s += "Result for multiline = " + re.multiline.toString();  
   s += ": " + r;  
  
   return(s);  
  
}  
  
sa = RegExpMultilineDemo("m");  
sb = RegExpMultilineDemo("");  
document.write (sa + "<br />" + sb);  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Si applica a**: [oggetto di espressione regolare](../../javascript/reference/regular-expression-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà Global (Regular Expression)](../../javascript/reference/global-property-regular-expression-javascript.md)   
 [Proprietà ignoreCase (Regular Expression)](../../javascript/reference/ignorecase-property-regular-expression-javascript.md)   
 [Sintassi di espressione regolare (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)