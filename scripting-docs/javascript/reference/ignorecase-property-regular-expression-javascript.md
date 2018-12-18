---
title: "Proprietà ignoreCase (Regular Expression) (JavaScript) | Documenti Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ignoreCase
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: IgnoreCase property
ms.assetid: 816f0df5-5a82-44a5-a4ab-dbc91fa76e61
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ae9fee8e6303fb944f59c11c173f9e8b7f7cc75a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="ignorecase-property-regular-expression-javascript"></a>Proprietà ignoreCase (Regular Expression) (JavaScript)
Restituisce un valore booleano che indica lo stato del flag ignoreCase (**si**) utilizzato con un'espressione regolare. Valore predefinito è **false**. Sola lettura.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
rgExp.ignoreCase  
```  
  
## <a name="remarks"></a>Note  
 Obbligatorio `rgExp` riferimento è un'istanza di `RegExp` oggetto.  
  
 Il **ignoreCase** restituisce proprietà **true** se il contrassegno ignoreCase è impostato per un'espressione regolare e restituisce **false** in caso contrario.  
  
 Il contrassegno ignoreCase, quando utilizzato, indica che una ricerca deve ignorare maiuscole e minuscole quando corrispondenti al criterio all'interno della stringa di ricerca.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del **ignoreCase** proprietà. Se "gi" viene passato alla funzione illustrata di seguito, tutte le istanze della parola "cui" vengono sostituite con la parola "a", tra cui iniziale "The". Questo avviene perché con il set di flag ignoreCase, la ricerca ignora qualsiasi distinzione maiuscole/minuscole. Pertanto, "T" equivale "t" ai fini della corrispondenza.  
  
 Questa funzione restituisce i valori booleani che indicano lo stato dei flag di espressione regolare consentita, sono **g**, **si**, e **m**. Inoltre, la funzione restituisce la stringa con tutte le sostituzioni apportate.  
  
```JavaScript  
function RegExpPropDemo(flag){  
    // The flag parameter is a string that contains  
    // g, i, or m. The flags can be combined.  
  
    // Check flags for validity.  
    if (flag.match(/[^gim]/))  
        {  
        return ("Flag specified is not valid");  
        }  
  
    // Create the string on which to perform the replacement.  
    var orig = "The batter hit the ball with the bat ";  
    orig += "and the fielder caught the ball with the glove.";  
  
    // Replace "the" with "a".  
    var re = new RegExp("the", flag);  
    var r = orig.replace(re, "a");          
  
    // Output the resulting string and the values of the flags.  
    var s = "";  
    s += "global: " + re.global.toString();  
    s += "<br />";  
    s += "ignoreCase: " + re.ignoreCase.toString();  
    s += "<br />";  
    s += "multiline: " + re.multiline.toString();  
    s += "<br />";  
    s += "Resulting String: " + r;  
    s += "<br />";  
    s += "<br />";  
    return (s);  
}  
  
document.write(RegExpPropDemo("gi"));  
document.write(RegExpPropDemo("g"));  
```  
  
## <a name="example"></a>Esempio  
 Di seguito è l'output risultante.  
  
```JavaScript  
global: true  
ignoreCase: true  
multiline: false  
Resulting String: a batter hit a ball with a bat and a fielder caught a ball with a glove.  
  
global: true  
ignoreCase: false  
multiline: false  
Resulting String: The batter hit a ball with a bat and a fielder caught a ball with a glove.  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Si applica a**: [oggetto di espressione regolare](../../javascript/reference/regular-expression-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà Global (Regular Expression)](../../javascript/reference/global-property-regular-expression-javascript.md)   
 [Proprietà Multiline (Regular Expression)](../../javascript/reference/multiline-property-regular-expression-javascript.md)   
 [Sintassi di espressione regolare (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)