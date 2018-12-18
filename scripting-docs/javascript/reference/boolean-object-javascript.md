---
title: Oggetto Boolean (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: boolean_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Boolean object
- Boolean data type, Boolean object
ms.assetid: d67748f2-7bf5-4889-8269-e777616cc5f0
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 20695376e4935cf6ddc34f30e373df19575ece3f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="boolean-object-javascript"></a>Oggetto Boolean (JavaScript)
Crea un nuovo valore booleano.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
boolObj = new Boolean([boolValue])  
```  
  
## <a name="parameters"></a>Parametri  
 `boolObj`  
 Obbligatorio. Nome della variabile a cui l'oggetto `Boolean` è assegnato.  
  
 `boolValue`  
 Parametro facoltativo. Valore booleano iniziale per il nuovo oggetto. Se `boolvalue` viene omesso oppure è `false`, 0, `null`, `NaN`, o una stringa vuota, il valore iniziale dell'oggetto Boolean è `false`. In caso contrario, il valore iniziale è `true`.  
  
## <a name="remarks"></a>Note  
 Il `Boolean` oggetto è un wrapper per il tipo di dati Boolean. [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]utilizza in modo implicito il `Boolean` oggetto ogni volta che un tipo di dati booleano viene convertito in un `Boolean` oggetto.  
  
 Si crea un'istanza raramente la `Boolean` dell'oggetto in modo esplicito.  
  
## <a name="properties"></a>Proprietà  
 Nella tabella seguente sono elencate le proprietà dell'oggetto `Boolean`.  
  
|Proprietà|Descrizione|  
|--------------|-----------------|  
|[Proprietà constructor](../../javascript/reference/constructor-property-boolean.md)|Specifica la funzione che crea un valore booleano.|  
|[Proprietà prototype](../../javascript/reference/prototype-property-boolean.md)|Restituisce un riferimento al prototipo per un valore booleano.|  
  
<a name="js56jsobjarraymeth"></a>   
## <a name="methods"></a>Metodi  
 Nella tabella seguente sono elencati i metodi dell'oggetto `Boolean`:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Metodo toString](../../javascript/reference/tostring-method-boolean-1.md)|Restituisce una rappresentazione di stringa di un valore booleano.|  
|[Metodo valueOf](../../javascript/reference/valueof-method-boolean.md)|Ottiene un riferimento al valore booleano.|  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]