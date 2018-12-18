---
title: in (operatore) (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: in_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: in operator
ms.assetid: dcd8f901-96b8-4c91-848b-b1ec0ab1c11c
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eefcd4c53d2e3366a26f0d8dfb099f59038507ae
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="in-operator-javascript"></a>Operatore in (JavaScript)
Verifica l'esistenza di una proprietà in un oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
result = property in object  
```  
  
## <a name="parameters"></a>Parametri  
 `result`  
 Obbligatorio. Qualsiasi variabile.  
  
 `property`  
 Obbligatorio. Un'espressione che restituisce un'espressione stringa.  
  
 `object`  
 Obbligatorio. Qualsiasi oggetto.  
  
## <a name="remarks"></a>Note  
 Il `in` operatore determina se un oggetto ha una proprietà denominata `property`. Determina inoltre se la proprietà fa parte della catena di prototipi dell'oggetto. Per ulteriori informazioni su prototipi di oggetti, vedere [prototipi ed ereditarietà del prototipo](../../javascript/advanced/prototypes-and-prototype-inheritance.md).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come utilizzare il `in` operatore:  
  
```JavaScript  
// Create an object that has some properties.  
var myObject = new Object();  
myObject.name = "James";  
myObject.age = "22";  
myObject.phone = "555 0234";  
  
if ("phone" in myObject)  
   document.write ("property is present");  
else  
   document.write ("property is not present");  
  
// Output: property is present  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Precedenza tra operatori](../../javascript/operator-subtractprecedence-javascript.md)   
 [Riepilogo degli operatori (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)