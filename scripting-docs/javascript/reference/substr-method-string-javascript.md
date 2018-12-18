---
title: Metodo substr (String) (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: substr
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: substr method
ms.assetid: f12541c1-2623-482e-941d-2e22bc3c4a4a
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b002bfefbeb81c534c882fa4a4720c93ccca185
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="substr-method-string-javascript"></a>Metodo substr (String) (JavaScript)
Ottiene una sottostringa che inizia in corrispondenza della posizione specificata e con la lunghezza specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
stringvar.substr(start [, length ])   
```  
  
## <a name="parameters"></a>Parametri  
 `stringvar`  
 Obbligatorio. Un valore letterale stringa o `String` dell'oggetto da cui estrarre la sottostringa.  
  
 `start`  
 Obbligatorio. Posizione iniziale della sottostringa desiderata. L'indice del primo carattere nella stringa è zero.  
  
 `length`  
 Parametro facoltativo. Il numero di caratteri da includere nella sottostringa restituita.  
  
## <a name="remarks"></a>Note  
 Se `length` è zero o negativo, viene restituita una stringa vuota. Se non specificato, la sottostringa continua fino alla fine di `stringvar`.  
  
## <a name="example"></a>Esempio  
 Nell'esempio riportato di seguito viene illustrato l'utilizzo del metodo `substr`.  
  
```JavaScript  
var s = "The quick brown fox jumps over the lazy dog.";  
var ss = s.substr(10, 5);    
document.write("[" + ss + "] <br>");  
  
ss = s.substr(10);  
document.write("[" + ss + "] <br>");  
  
ss = s.substr(10, -5);  
document.write("[" + ss + "] <br>");  
  
// Output:  
// [brown]   
// [brown fox jumps over the lazy dog.]   
// []  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Si applica a**: [oggetto stringa](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo substring (String)](../../javascript/reference/substring-method-string-javascript.md)