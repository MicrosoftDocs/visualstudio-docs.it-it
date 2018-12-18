---
title: Metodo toString (Array) | Documenti Microsoft
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
ms.assetid: 71fbea85-3e00-41b0-b167-25e4281e5e8a
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6dc7cbf843e47ffc2d21f5a2b1d03c43e675a130
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="tostring-method-array"></a>Metodo toString (Array)
Restituisce la rappresentazione in formato stringa di una matrice.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
array.toString()  
```  
  
## <a name="parameters"></a>Parametri  
 `array`  
 Obbligatorio. Matrice da rappresentare come una stringa.  
  
## <a name="return-value"></a>Valore restituito  
 Rappresentazione di stringa della matrice.  
  
## <a name="remarks"></a>Note  
 Gli elementi di un `Array` vengono convertiti in stringhe. Le stringhe risultanti vengono concatenate e separate da virgole.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del **toString** metodo con una matrice.  
  
```JavaScript  
var arr = [1, 2, 3, 4];  
var s = arr.toString();  
document.write(s);  
  
// Output: 1,2,3,4  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]