---
title: Metodo setUTCMinutes (Date) (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: setUTCMinutes
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- minutes
- dates, UTC
- UTC times, setting
- setUTCMinutes method
ms.assetid: 2415e788-6d28-46dd-a103-0931a1fd1446
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 37df1bcefa358f2c9076a3da877bd642d19178b0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="setutcminutes-method-date-javascript"></a>Metodo setUTCMinutes (Date) (JavaScript)
Imposta il valore dei minuti il `Date` utilizzando l'ora UTC (Universal Coordinated Time).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
dateObj.setUTCMinutes(numMinutes[, numSeconds[, numMilli]])   
```  
  
## <a name="parameters"></a>Parametri  
 `dateObj`  
 Obbligatorio. Qualsiasi oggetto `Date`.  
  
 `numMinutes`  
 Obbligatorio. Valore numerico che rappresenta il valore dei minuti. È necessario specificare se uno degli argomenti seguenti viene utilizzato.  
  
 *numSeconds*  
 Parametro facoltativo. Valore numerico che rappresenta il valore dei secondi. È necessario specificare se `numMilli` viene utilizzato.  
  
 `numMilli`  
 Parametro facoltativo. Valore numerico che rappresenta il valore dei millisecondi.  
  
## <a name="remarks"></a>Note  
 Tutti **impostare** i metodi che gli argomenti facoltativi utilizzato il valore restituito dal corrispondente **ottenere** metodi, se non si specifica un argomento facoltativo. Ad esempio, se il *numSeconds* argomento non viene specificato, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] utilizza il valore restituito dal `getUTCSeconds` metodo.  
  
 Per modificare il valore dei minuti utilizzando l'ora locale, utilizzare il `setMinutes` metodo.  
  
 Se il valore di un argomento è maggiore dell'intervallo specificato o è un numero negativo, gli altri valori memorizzati verranno modificati di conseguenza. Ad esempio, se la data memorizzata è "5 gennaio 1996 00.00.00.00", e **setUTCMinutes(70)** viene chiamato, la data viene modificata in "5 gennaio 1996 01.10.00.00".  
  
 Il **setUTCHours** metodo può essere utilizzato per impostare le ore, minuti, secondi e millisecondi.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del `setUTCMinutes` metodo:  
  
```JavaScript  
function SetUTCMinutesDemo(nmin, nsec){  
   var d, s;                    // Declare variables.  
   d = new Date();              // Create Date object.  
   d.setUTCMinutes(nmin,nsec);  // Set UTC minutes.  
   s = "Current setting is " + d.toUTCString()   
   return(s);                   // Return new setting.  
}  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Si applica a**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getMinutes (Date)](../../javascript/reference/getminutes-method-date-javascript.md)   
 [Metodo getUTCMinutes (Date)](../../javascript/reference/getutcminutes-method-date-javascript.md)   
 [Metodo setMinutes (Date)](../../javascript/reference/setminutes-method-date-javascript.md)