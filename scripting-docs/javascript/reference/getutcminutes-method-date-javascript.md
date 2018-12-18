---
title: Metodo getUTCMinutes (Date) (JavaScript) | Documenti Microsoft
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
- getUTCMinutes
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- minutes
- UTC times, returning
- getUTCMinutes method
ms.assetid: b6d92543-b285-4e46-8f47-bba36e53fabd
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fe691d3b52d18340eeeff81a91c049a262277c54
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="getutcminutes-method-date-javascript"></a>Metodo getUTCMinutes (Date) (JavaScript)
Ottiene i minuti di un `Date` utilizzando l'ora UTC (Universal Coordinated Time).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
dateObj.getUTCMinutes()   
```  
  
#### <a name="parameters"></a>Parametri  
 Il riferimento `dateObj` obbligatorio è un oggetto `Date` .  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un numero intero compreso tra 0 e 59. Viene restituito zero che il tempo è minore di un minuto. Se un `Date` oggetto è stato creato senza specificare l'ora, per impostazione predefinita, l'ora UTC valore dei minuti è 0. Tuttavia, in fusi orari diversi potrebbe essere diverso.  
  
## <a name="remarks"></a>Note  
 Per ottenere il numero di minuti memorizzato in ora locale, utilizzare il `getMinutes` metodo.  
  
## <a name="example"></a>Esempio  
 Nell'esempio riportato di seguito viene illustrato l'utilizzo del metodo `getUTCMinutes`.  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getUTCMinutes());  
document.write("<br/>");  
  
date.setMinutes(5);  
document.write(date.getUTCMinutes());  
  
// Output:   
// 0  
// 5  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Si applica a**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getMinutes (Date)](../../javascript/reference/getminutes-method-date-javascript.md)   
 [Metodo setMinutes (Date)](../../javascript/reference/setminutes-method-date-javascript.md)   
 [Metodo setUTCMinutes (Date)](../../javascript/reference/setutcminutes-method-date-javascript.md)