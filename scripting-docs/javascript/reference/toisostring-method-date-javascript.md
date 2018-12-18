---
title: Metodo toISOString (Date) (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toISOString method [JavaScript]
ms.assetid: 58577d8f-3ae8-4887-8687-26233ea79ff6
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 31559e1bc44849573ec7dc903411ce98b0a4440d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="toisostring-method-date-javascript"></a>Metodo toISOString (Date) (JavaScript)
Restituisce una data come valore stringa in formato ISO.  
  
## <a name="syntax"></a>Sintassi  
  
```JavaScript  
  
objDate.toISOString()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Rappresentazione di stringa della data nel International Organization formato Standardization (ISO).  
  
## <a name="exceptions"></a>Eccezioni  
 Se `objDate` non contiene una data valida, un `RangeError` viene generata un'eccezione.  
  
## <a name="remarks"></a>Note  
 Il formato ISO è una semplificazione del formato ISO 8601. Per ulteriori informazioni, vedere [stringhe data e ora](../../javascript/date-and-time-strings-javascript.md).  
  
 Il fuso orario è sempre UTC, indicato dal suffisso Z nell'output.  
  
## <a name="example"></a>Esempio  
 Nell'esempio riportato di seguito viene illustrato l'utilizzo del metodo `toISOString`.  
  
```JavaScript  
var dt = new Date("30 July 2010 15:05 UTC");  
document.write(dt.toISOString());  
document.write("<br />");  
document.write(dt.toUTCString());  
  
// Output:  
//  2010-07-30T15:05:00.000Z  
//  Fri, 30 Jul 2010 15:05:00 UTC  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Date (oggetto)](../../javascript/reference/date-object-javascript.md)   
 [Stringhe di data e ora](../../javascript/date-and-time-strings-javascript.md)