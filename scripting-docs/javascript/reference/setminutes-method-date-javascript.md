---
title: Metodo setMinutes (Date) (JavaScript) | Documenti Microsoft
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
- setMinutes
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- minutes
- setMinutes method
ms.assetid: 34c959cd-cd29-4cee-8e04-9061cf6d42f3
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1ce40cb3ebf769cdd8f668e246e272833780434d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="setminutes-method-date-javascript"></a>Metodo setMinutes (Date) (JavaScript)
Imposta il valore dei minuti il **data** oggetto utilizzando l'ora locale.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
dateObj.setMinutes(numMinutes[, numSeconds[, numMilli]])   
```  
  
## <a name="parameters"></a>Parametri  
 `dateObj`  
 Obbligatorio. Qualsiasi oggetto `Date`.  
  
 `numMinutes`  
 Obbligatorio. Valore numerico che rappresenta il valore dei minuti. È necessario specificare se uno degli argomenti seguenti viene utilizzato.  
  
 *numSeconds*  
 Parametro facoltativo. Valore numerico che rappresenta il valore dei secondi. È necessario specificare se il `numMilli` viene utilizzato l'argomento.  
  
 `numMilli`  
 Parametro facoltativo. Valore numerico che rappresenta il valore dei millisecondi.  
  
## <a name="remarks"></a>Note  
 Tutti **impostare** i metodi che gli argomenti facoltativi utilizzato il valore restituito dal corrispondente **ottenere** metodi, se non si specifica un argomento facoltativo. Ad esempio, se il *numSeconds* argomento non specificato, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] utilizza il valore restituito dal `getSeconds` metodo.  
  
 Per impostare il valore dei minuti con l'ora UTC (Universal Coordinated Time), utilizzare il `setUTCMinutes` metodo.  
  
 Se il valore di un argomento è maggiore dell'intervallo specificato o è un numero negativo, gli altri valori memorizzati verranno modificati di conseguenza. Ad esempio, se la data memorizzata è "il 5 gennaio 1996 00:00:00" e **setMinutes(90)** viene chiamato, la data viene modificata in "5 gennaio 1996 01:30:00." I numeri negativi hanno un comportamento simile.  
  
## <a name="example"></a>Esempio  
 Nell'esempio riportato di seguito viene illustrato l'utilizzo del metodo `setMinutes`.  
  
```JavaScript  
function SetMinutesDemo(nmin, nsec){  
   var d, s;                     // Declare variables.  
   d = new Date();               // Create Date object.  
   d.setMinutes(nmin, nsec);     // Set minutes.  
   s = "Current setting is " + d.toLocaleString()   
   return(s);                    // Return new setting.  
}  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Si applica a**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getMinutes (Date)](../../javascript/reference/getminutes-method-date-javascript.md)   
 [Metodo getUTCMinutes (Date)](../../javascript/reference/getutcminutes-method-date-javascript.md)   
 [Metodo setUTCMinutes (Date)](../../javascript/reference/setutcminutes-method-date-javascript.md)