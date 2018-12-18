---
title: Metodo splice (Array) (JavaScript) | Documenti Microsoft
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
- splice
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- splice method
ms.assetid: 85fdfb13-e3d9-4c89-b524-3ccee7001c93
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0d56a22244f76f5ce7221c276629907811733d51
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="splice-method-array-javascript"></a>Metodo splice (Array) (JavaScript)
Rimuove elementi da una matrice e, se necessario, li sostituisce con nuovi elementi restituendo gli elementi eliminati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
arrayObj.splice(start, deleteCount, [item1[, item2[, . . . [,itemN]]]])  
```  
  
## <a name="parameters"></a>Parametri  
 `arrayObj`  
 Obbligatorio. Oggetto `Array`.  
  
 `start`  
 Obbligatorio. Posizione in base zero nella matrice da cui iniziare la rimozione di elementi.  
  
 `deleteCount`  
 Obbligatorio. Numero di elementi da rimuovere.  
  
 `item1, item2,. . ., itemN`  
 Parametro facoltativo. Elementi da inserire nella matrice al posto di elementi eliminati.  
  
## <a name="remarks"></a>Note  
 Il `splice` modificato dal metodo `arrayObj` rimuovendo il numero specificato di elementi dalla posizione `start` e l'inserimento di nuovi elementi. Gli elementi eliminati vengono restituiti come un nuovo `Array` oggetto.  
  
## <a name="example"></a>Esempio  
 Nell'esempio di codice seguente viene illustrato come utilizzare il metodo `splice`.  
  
```JavaScript  
var arr = new Array("4", "11", "2", "10", "3", "1");  
arr.splice(2, 2, "21", "31");  
document.write(arr);  
  
// Output: 4,11,21,31,3,1  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo slice (Array)](../../javascript/reference/slice-method-array-javascript.md)