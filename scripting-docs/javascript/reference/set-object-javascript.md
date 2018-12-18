---
title: Oggetto set (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Set
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 4a4dd749-2a76-44fb-9cb0-a3ef317f75fb
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5134ec09c9a8642499212af9dd5fd44de0068adc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="set-object-javascript"></a>Oggetto Set (JavaScript)
Raccolta di valori univoci che possono essere di qualsiasi tipo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
setObj = new Set()     
```  
  
## <a name="remarks"></a>Note  
 Se si tenta di aggiungere un valore non univoco per un `Set`, il nuovo valore non essere aggiunti alla raccolta.  
  
## <a name="properties"></a>Proprietà  
 Nella tabella seguente sono elencate le proprietà dell'oggetto `Set`.  
  
|Proprietà|Descrizione|  
|--------------|-----------------|  
|[costruttore](../../javascript/reference/constructor-property-set.md)|Specifica la funzione che crea un set.|  
|[prototipo](../../javascript/reference/prototype-property-set.md)|Restituisce un riferimento al prototipo per un set.|  
|[size](../../javascript/reference/size-property-set-javascript.md)|Restituisce il numero di elementi in un set.|  
  
## <a name="methods"></a>Metodi  
 Nella tabella seguente sono elencati i metodi dell'oggetto `Set`:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[add](../../javascript/reference/add-method-set-javascript.md)|Aggiunge un elemento a un set.|  
|[clear](../../javascript/reference/clear-method-set-javascript.md)|Rimuove tutti gli elementi da un set.|  
|[eliminare](../../javascript/reference/delete-method-set-javascript.md)|Rimuove un elemento specificato da un set.|  
|[forEach](../../javascript/reference/foreach-method-set-javascript.md)|Esegue l'azione specificata per ogni elemento in un set.|  
|[è](../../javascript/reference/has-method-set-javascript.md)|Restituisce `true` se il set contiene un elemento specificato.|  
|[toString](../../javascript/reference/tostring-method-set-javascript.md)|Restituisce una rappresentazione di stringa di un set.|  
|[valueOf](../../javascript/reference/valueof-method-set-javascript.md)|Restituisce il valore primitivo dell'opzione specificata.|  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come aggiungere membri a un oggetto Set e quindi recuperarli.  
  
```JavaScript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
  
s.forEach(function (item) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776, founding father,  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]