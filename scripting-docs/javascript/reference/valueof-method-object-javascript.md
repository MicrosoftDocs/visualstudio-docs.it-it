---
title: Metodo valueOf (Object) (JavaScript) | Documenti Microsoft
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
- valueOf
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- valueOf method
ms.assetid: c555e38b-f451-4341-8fcd-4c8b02906a2c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 677b56fd6fc142ce175b130d2f83291c1ac9535f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="valueof-method-object-javascript"></a>Metodo valueOf (Object) (JavaScript)
Restituisce il valore primitivo dell'opzione specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
object.valueOf( )  
```  
  
## <a name="remarks"></a>Note  
 Obbligatorio `object` riferimento è qualsiasi intrinseco [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] oggetto.  
  
 Il `valueOf` metodo definito in modo diverso per ogni funzione intrinseca [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] oggetto.  
  
|Oggetto|Valore restituito|  
|------------|------------------|  
|Matrice|Restituisce l'istanza di matrice.|  
|Booleano|Valore booleano.|  
|Data|Il valore di ora stored in millisecondi trascorsi dalla mezzanotte del 1 gennaio 1970 ora UTC.|  
|Funzione|La funzione stessa.|  
|Number|Il valore numerico.|  
|Oggetto|L'oggetto stesso. Questa è l'impostazione predefinita.|  
|String|Valore stringa.|  
  
 Il **matematiche** e `Error` oggetti non hanno un `valueOf` metodo.  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
 **Si applica a**: [oggetto matrice](../../javascript/reference/array-object-javascript.md)&#124; [Oggetto Boolean](../../javascript/reference/boolean-object-javascript.md)&#124; [Data oggetto](../../javascript/reference/date-object-javascript.md)&#124; [Funzione oggetto](../../javascript/reference/function-object-javascript.md)&#124; [Numero oggetto](../../javascript/reference/number-object-javascript.md)&#124; [Oggetto](../../javascript/reference/object-object-javascript.md)&#124; [Oggetto stringa](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo toString (Object)](../../javascript/reference/tostring-method-object-javascript.md)