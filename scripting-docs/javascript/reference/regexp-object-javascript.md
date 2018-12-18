---
title: Oggetto RegExp (JavaScript) | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- RegExp
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- RegExp object, overview
- RegExp object
ms.assetid: 7f6b1073-8cbb-49ed-94b6-56833ba663c5
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b7319e4556721bcfd397061ce525acfb3278c6b9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="regexp-object-javascript"></a>Oggetto RegExp (JavaScript)
Corrisponde a un oggetto globale intrinseco che archivia le informazioni sui risultati di ricerca di espressioni regolari.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
RegExp.property   
```  
  
## <a name="remarks"></a>Note  
 Obbligatorio *proprietà* argomento può essere uno qualsiasi del `RegExp` proprietà dell'oggetto.  
  
 Il `RegExp` oggetto non è possibile creare direttamente, ma è sempre disponibile per l'utilizzo. Fino a quando non è stata completata una ricerca di espressioni regolari ha esito positivo, i valori iniziali delle varie proprietà del `RegExp` oggetto sono le seguenti:  
  
|Proprietà|Sintassi abbreviata|Valore iniziale|  
|--------------|---------------|-------------------|  
|indice||-1|  
|input|$_|Stringa vuota.|  
|lastIndex||-1|  
|lastMatch|$&|Stringa vuota.|  
|lastParen|$+|Stringa vuota.|  
|leftContext|$`|Stringa vuota.|  
|rightContext|$'|Stringa vuota.|  
|$1 - $9|$1 - $9|Stringa vuota.|  
  
 Le proprietà hanno non definiti come relativo valore fino a quando non è stata completata una ricerca di espressioni regolari ha esito positivo.  
  
 Globale `RegExp` oggetto non deve essere confuso con il **espressione regolare** oggetto. Anche se sembrano come la stessa operazione, sono distinti e separati. Le proprietà dell'oggetto globale `RegExp` contengono informazioni continuamente aggiornate su ogni corrispondenza quando si verifica, mentre le proprietà del **espressione regolare** contengono solo informazioni sulle corrispondenze che si verificano con questa istanza del **espressione regolare**.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente esegue una ricerca di espressioni regolari. Visualizza le corrispondenze e submatches da globale `RegExp` oggetto e dalla matrice restituita dal `exec` metodo.  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
<a name="js56jsobjregexpprop"></a>   
## <a name="properties"></a>Proprietà  
 [$1... $9 proprietà](../../javascript/reference/dollar-1-dot-dot-dot-dollar-9-properties-regexp-javascript.md) &#124; [proprietà index](../../javascript/reference/index-property-regexp-javascript.md) &#124; [proprietà input](../../javascript/reference/input-property-dollar-regexp-javascript.md) &#124; [proprietà lastIndex](../../javascript/reference/lastindex-property-regexp-javascript.md) &#124; [proprietà lastMatch](../../javascript/reference/lastmatch-property-dollar-regexp-javascript.md) &#124; [proprietà lastParen](../../javascript/reference/lastparen-property-dollar-regexp-javascript.md) &#124; [proprietà leftContext](../../javascript/reference/leftcontext-property-dollar-grave-regexp-javascript.md) &#124; [proprietà rightContext](../../javascript/reference/rightcontext-property-dollar-regexp-javascript.md)  
  
## <a name="methods"></a>Metodi  
 Il `RegExp` oggetto non ha metodi.  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto di espressione regolare](../../javascript/reference/regular-expression-object-javascript.md)   
 [Sintassi di espressione regolare (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [Oggetto String](../../javascript/reference/string-object-javascript.md)