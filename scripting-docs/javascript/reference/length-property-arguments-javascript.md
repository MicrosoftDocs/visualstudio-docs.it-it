---
title: "Proprietà length (arguments) (JavaScript) | Documenti Microsoft"
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
- length property (arguments)
- Length property
ms.assetid: 3cf36823-15bc-489b-a951-24c4923d9dba
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cede75a91244442f5f28ec9f71b7128814bed5d2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="length-property-arguments-javascript"></a>Proprietà length (arguments) (JavaScript)
Restituisce il numero effettivo di argomenti passati a una funzione dal chiamante.  
  
## <a name="syntax"></a>Sintassi  
  
```  
[function.]arguments.length  
```  
  
## <a name="remarks"></a>Note  
 Facoltativo *funzione* argomento è il nome di attualmente in esecuzione `Function` oggetto.  
  
 Il **lunghezza** proprietà del **argomenti** oggetto viene inizializzato dal motore di scripting per il numero effettivo di argomenti passati a un `Function` all'avvio dell'esecuzione di tale funzione dell'oggetto.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del **lunghezza** proprietà del **argomenti** oggetto. Per comprendere meglio l'esempio, passare più argomenti alla funzione di 2 argomenti previsti:  
  
```JavaScript  
function ArgTest(a, b){  
   var s = "";  
  
   s += "Expected Arguments: " + ArgTest.length;  
   s += "<br />";  
   s += "Passed Arguments: " + arguments.length;  
  
   document.write (s);  
}  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Si applica a**: [oggetto arguments](../../javascript/reference/arguments-object-javascript.md)&#124; [Funzione oggetto](../../javascript/reference/function-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà Arguments (Function)](../../javascript/reference/arguments-property-function-javascript.md)   
 [Proprietà length (Array)](../../javascript/reference/length-property-array-javascript.md)   
 [Proprietà length (String)](../../javascript/reference/length-property-string-javascript.md)