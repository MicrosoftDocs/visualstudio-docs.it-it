---
title: Metodo toTimeString (Date) (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: toTimeString
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: toTimeString method
ms.assetid: a4a8c0f2-55a9-4e84-94c3-f0a547fb04b5
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4d9af1f688fee0c066158d8504e00f22af9b3a21
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="totimestring-method-date-javascript"></a>Metodo toTimeString (Date) (JavaScript)
Restituisce un'ora come valore stringa.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
objDate. toTimeString( )  
```  
  
## <a name="remarks"></a>Note  
 Il riferimento `objDate` obbligatorio è un oggetto `Date`.  
  
 Il `toTimeString` metodo restituisce un valore stringa che contiene l'ora nel fuso orario corrente.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente, l'ora viene impostato su 2000 millisecondi dopo mezzanotte dell'1 gennaio 1970 ora UTC e quindi viene scritto.  
  
```JavaScript  
var aDate = new Date();  
     aDate.setTime(2000);  
     document.write(aDate.toTimeString());  
  
// Output depends on the time in the current time zone.  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo toDateString (Date)](../../javascript/reference/todatestring-method-date-javascript.md)   
 [Metodo toLocaleTimeString (Date)](../../javascript/reference/tolocaletimestring-method-date-javascript.md)