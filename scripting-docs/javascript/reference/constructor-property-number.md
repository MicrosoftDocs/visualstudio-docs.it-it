---
title: "Proprietà constructor (Number) | Documenti Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a348fe53-1b4a-42f5-964b-53d57342c906
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 72679f55aef9b0ac8dc01794c7460dbd8cf0bdf8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="constructor-property-number"></a>Proprietà constructor (Number)
Specifica la funzione che crea un numero.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
number.constructor  
```  
  
## <a name="remarks"></a>Note  
 Obbligatorio `number` è il nome di una stringa.  
  
 La proprietà `constructor` è un membro del prototipo di ogni oggetto per cui esiste un prototipo. Sono inclusi tutti gli intrinseci [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] oggetti ad eccezione di `Global` e `Math` oggetti. La proprietà `constructor` contiene un riferimento alla funzione che costruisce istanze di tale oggetto specifico.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo della proprietà di costruttore.  
  
```JavaScript  
var num = new Number();  
  
if (num.constructor == Number)  
    document.write("Object is a Number.");  
else  
    document.write("Object is not a Number.");  
  
// Output:  
// Object is a Number.  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]