---
title: Metodo getMinutes (Date) (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getMinutes
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- GetMinutes method
- minutes method
ms.assetid: d4139b5d-04e1-474c-9a83-e9d40597243a
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ff08fd84345c9ceb816444a1b44643a8353b60b1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="getminutes-method-date-javascript"></a>Metodo getMinutes (Date) (JavaScript)
Ottiene i minuti di un `Date` dell'oggetto, utilizzando l'ora locale.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
dateObj.getMinutes()   
```  
  
#### <a name="parameters"></a>Parametri  
 Il riferimento `dateObj` obbligatorio è un oggetto `Date` .  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un numero intero compreso tra 0 e 59. Viene restituito zero che il tempo è minore di un minuto. Se un `Date` oggetto è stato creato senza specificare l'ora, per impostazione predefinita, il valore dei minuti è 0.  
  
## <a name="remarks"></a>Note  
 Per ottenere il valore dei minuti con l'ora UTC (Universal Coordinated Time), utilizzare il `getUTCMinutes` metodo.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come il `getMinutes` metodo.  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getMinutes());  
document.write("<br/>");  
  
date.setMinutes(5);  
document.write(date.getMinutes());  
  
// Output:  
// 0  
// 5  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Si applica a**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getUTCMinutes (Date)](../../javascript/reference/getutcminutes-method-date-javascript.md)   
 [Metodo setMinutes (Date)](../../javascript/reference/setminutes-method-date-javascript.md)   
 [Metodo setUTCMinutes (Date)](../../javascript/reference/setutcminutes-method-date-javascript.md)