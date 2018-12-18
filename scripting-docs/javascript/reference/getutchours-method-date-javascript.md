---
title: Metodo getUTCHours (Date) (JavaScript) | Documenti Microsoft
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
- getUTCHours
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- hours
- UTC times, returning
- getUTCHours method
ms.assetid: 7c9825dd-4b3a-4614-8e09-f40df123b630
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c47fe66e6eecb9e3aaa53f0d0988631062676d17
ms.sourcegitcommit: ba29e4d37db92ec784d4acf9c6e120cf0ea677e9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2018
---
# <a name="getutchours-method-date-javascript"></a>Metodo getUTCHours (Date) (JavaScript)
Ottiene il valore delle ore in un `Date` utilizzando l'ora UTC (Universal Coordinated Time).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
dateObj.getUTCHours()   
```  
  
#### <a name="parameters"></a>Parametri  
 Il riferimento `dateObj` obbligatorio è un oggetto `Date` .  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un intero compreso tra 0 e 23 che indica il numero di ore da mezzanotte. Se l'ora prima 1:00:00 am, sarà restituito zero. Se un `Date` oggetto è stato creato senza specificare l'ora, per impostazione predefinita, l'ora è 0 in formato UTC. Tale periodo può essere diverso da zero fusi orari diversi.  
  
## <a name="remarks"></a>Note  
 Per ottenere il numero di ore trascorsi dalla mezzanotte ora locale, utilizzare il `getHours` metodo.  
  
## <a name="example"></a>Esempio  
 Nell'esempio riportato di seguito viene illustrato l'utilizzo del metodo `getUTCHours`.  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getUTCHours());  
document.write("<br/>");  
  
var date2 = new Date("1/1/2001 11:22:33");  
document.write(date2.getUTCHours());  
  
// Output (in the PST time zone):  
// 15 
// 2  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Si applica a**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getHours (Date)](../../javascript/reference/gethours-method-date-javascript.md)   
 [Metodo setHours (Date)](../../javascript/reference/sethours-method-date-javascript.md)   
 [Metodo setUTCHours (Date)](../../javascript/reference/setutchours-method-date-javascript.md)
