---
title: Metodo Trim (String) (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: trim method
ms.assetid: 03d38c7e-25cd-4ede-b58e-1a10b5249bab
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de358981cfbf569ef35be95b55b3e9856027df35
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="trim-method-string-javascript"></a>Metodo trim (String) (JavaScript)
Rimuove gli spazi iniziali e finali e i caratteri di terminazione di riga da una stringa.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
stringObj.trim()  
```  
  
## <a name="parameters"></a>Parametri  
 `stringObj`  
 Obbligatorio. Oggetto `String` o valore letterale stringa. Questa stringa non viene modificata dal metodo `trim`.  
  
## <a name="return-value"></a>Valore restituito  
 Stringa originale in cui sono stati rimossi spazi vuoti iniziali e finali e caratteri di terminazione di riga.  
  
## <a name="remarks"></a>Note  
 I caratteri rimossi includono spazio, tabulazione, avanzamento carta, ritorno a capo e avanzamento riga. Vedere [caratteri speciali](../../javascript/advanced/special-characters-javascript.md) per un elenco completo dei caratteri di terminazione di riga e di spazi vuoti.  
  
 Per un esempio che illustra come implementare il metodo trim, vedere [prototipi ed ereditarietà del prototipo](../../javascript/advanced/prototypes-and-prototype-inheritance.md).  
  
## <a name="example"></a>Esempio  
 Nell'esempio riportato di seguito viene illustrato l'utilizzo del metodo `trim`.  
  
```JavaScript  
var message = "    abc def     \r\n  ";  
  
document.write("[" + message.trim() + "]");  
document.write("<br/>");  
document.write("length: " + message.trim().length);  
  
// Output:  
//  [abc def]  
//  length: 7  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Caratteri speciali](../../javascript/advanced/special-characters-javascript.md)   
 [Oggetto String](../../javascript/reference/string-object-javascript.md)   
 [App di esempio di scorrimento, panoramica e zoom](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)