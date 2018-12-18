---
title: Metodo toGMTString (Date) (JavaScript) | Documenti Microsoft
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
- toGMTString
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toGMTString method
ms.assetid: 9dc1e722-5722-4b8c-a213-a2650f55f207
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cef8a61e04fbb5ada6e03fa946f434327422d9d7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="togmtstring-method-date-javascript"></a>Metodo toGMTString (Date) (JavaScript)
Restituisce una data convertita in una stringa utilizzando Time(GMT) significa Greenwich.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
dateObj.toGMTString()   
```  
  
## <a name="remarks"></a>Note  
 Obbligatorio `dateObj` si intende qualsiasi riferimento `Date` oggetto.  
  
 Il `toGMTString` metodo è obsoleto e viene fornito per la compatibilità solo. È consigliabile utilizzare il `toUTCString` metodo invece.  
  
 Il `toGMTString` metodo restituisce un `String` oggetto che contiene la data formattata utilizzando la convenzione GMT. Il formato del valore restituito è il seguente: "05 gen 1996 GMT di 00:00:00".  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Si applica a**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo toUTCString (Date)](../../javascript/reference/toutcstring-method-date-javascript.md)