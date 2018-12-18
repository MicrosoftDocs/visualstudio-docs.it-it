---
title: "Proprietà lastIndex (RegExp) (JavaScript) | Documenti Microsoft"
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
- lastIndex
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- lastIndex property
ms.assetid: c8ae2a13-6dff-4cbe-b662-aca3d66c2a7f
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d5e24fe14d335e1494b13518543f56025625de0b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="lastindex-property-regexp-javascript"></a>Proprietà lastIndex (RegExp) (JavaScript)
Restituisce la posizione del carattere in cui inizia la corrispondenza successiva in una stringa di ricerca.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
RegExp.lastIndex  
```  
  
## <a name="remarks"></a>Note  
 L'oggetto associato a questa proprietà è sempre globale `RegExp` oggetto.  
  
 Il `lastIndex` proprietà in base zero, l'indice del primo carattere è zero. Il valore iniziale è -1. Il valore viene modificato ogni volta che viene individuata una corrispondenza.  
  
 Il `lastIndex` proprietà viene modificata tramite il `exec` e **test** metodi del `RegExp` oggetto e `match`, **sostituire**, e **dividere**metodi di `String` oggetto.  
  
 Le regole seguenti si applicano ai valori di `lastIndex`:  
  
-   Se è presente alcuna corrispondenza, `lastIndex` è impostato su -1.  
  
-   Se `lastIndex` è maggiore della lunghezza della stringa, **test** e `exec` esito negativo e `lastIndex` è impostato su -1.  
  
-   Se `lastIndex` è uguale alla lunghezza della stringa, le corrispondenze di espressione regolare, se il modello corrisponde a una stringa vuota. In caso contrario, la corrispondenza ha esito negativo e `lastIndex` viene reimpostato su -1.  
  
-   In caso contrario, `lastIndex` è impostata alla posizione successiva dopo la corrispondenza più recente.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del `lastIndex` proprietà. Questa funzione esegue l'iterazione di una stringa di ricerca e viene stampato il **indice** e `lastIndex` i valori per ogni parola nella stringa.  
  
```JavaScript  
function RegExpTest()  
{  
   var ver = Number(ScriptEngineMajorVersion() + "." + ScriptEngineMinorVersion())  
   if (ver < 5.5)  
   {  
      document.write("You need a newer version of JavaScript for this to work");  
      return;  
   }  
  
   var src = "The quick brown fox jumps over the lazy dog.";  
  
   // Create regular expression pattern with a global flag.  
   var re = /\w+/g;  
  
   // Get the next word, starting at the position of lastindex.  
   var arr;  
   while ((arr = re.exec(src)) != null)  
      {  
      // New line:  
      document.write ("<br />");    
      document.write (arr.index + "-" + re.lastIndex + " ");  
      document.write (arr);  
      }  
}  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Si applica a**: [RegExp (oggetto)](../../javascript/reference/regexp-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Sintassi di espressione regolare (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)