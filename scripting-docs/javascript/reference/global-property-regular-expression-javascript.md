---
title: "Proprietà Global (Regular Expression) (JavaScript) | Documenti Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Global
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: global property
ms.assetid: 76a0f115-0d89-4aca-86d5-932895c6d649
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7e2b0256fea60b7ab998c504e79565fc7028cd98
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="global-property-regular-expression-javascript"></a>Proprietà global (Regular Expression) (JavaScript)
Restituisce un valore booleano che indica lo stato del flag globale (**g**) utilizzato con un'espressione regolare. Valore predefinito è **false**. Sola lettura.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
rgExp.global  
```  
  
## <a name="remarks"></a>Note  
 Obbligatorio `rgExp` riferimento è un'istanza di un **espressione regolare** oggetto.  
  
 Il `global` restituisce proprietà **true** se il flag globale è impostato per un'espressione regolare e restituisce **false** in caso contrario.  
  
 Il flag globale, se utilizzato, indica che una ricerca devono essere individuate tutte le occorrenze del criterio all'interno della stringa di ricerca, non solo il primo. È anche noto come corrispondenza globale.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del `global` proprietà. Se si passa **g** "nella funzione illustrata di seguito, tutte le istanze della parola the" verranno sostituite con la parola "a". Si noti che la "The" all'inizio della stringa non viene sostituita in quanto il **si** (Ignora maiuscole / minuscole) flag non è stato passato alla funzione.  
  
 Questa funzione consente di visualizzare la condizione delle proprietà associate ai flag dell'espressione regolare consentiti, ovvero **g**, **si**, e **m**. La funzione Visualizza anche la stringa con tutte le sostituzioni apportate.  
  
```JavaScript  
function RegExpPropDemo(flag){  
   // The flag parameter is a string that contains  
   // g, i, or m.  The flags can be combined.  
  
   // Check flags for validity.  
   if (flag.match(/[^gim]/))  
      {  
      return ("Flag specified is not valid");  
      }  
  
   // Create the string on which to perform the replacement.  
   var ss = "The batter hit the ball with the bat ";  
   ss += "and the fielder caught the ball with the glove.";  
  
   //Replace "the" with "a".  
   var re = new RegExp("the", flag);  
   var r = ss.replace(re, "a");          
  
   // Output the resulting string and the flags.  
   var s = "";  
   s += "global: " + re.global.toString();  
   s += "<br />";  
   s += "ignoreCase: " + re.ignoreCase.toString();  
   s += "<br />";  
   s += "multiline: " + re.multiline.toString();  
   s += "<br />";  
   s += "Resulting String: " + r;  
  
   return (s);  
}  
  
document.write(RegExpPropDemo("g"));  
```  
  
## <a name="example"></a>Esempio  
 Di seguito è l'output risultante.  
  
```JavaScript  
global: true  
ignoreCase: false  
multiline: false  
Resulting String: The batter hit a ball with a bat and a fielder caught a ball with a glove.  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Si applica a**: [oggetto di espressione regolare](../../javascript/reference/regular-expression-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà ignoreCase (Regular Expression)](../../javascript/reference/ignorecase-property-regular-expression-javascript.md)   
 [Proprietà Multiline (Regular Expression)](../../javascript/reference/multiline-property-regular-expression-javascript.md)   
 [Sintassi di espressione regolare (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)