---
title: Metodo valueOf (Number) | Documenti Microsoft
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
ms.assetid: 0242a9ce-d41a-4c9b-af59-e8df32bbd913
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d7918fb94673803e99d476d63fd814bce19bf9a5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="valueof-method-number"></a>Metodo valueOf (Number)
Restituisce il valore primitivo del numero specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
number.valueOf()  
```  
  
#### <a name="parameters"></a>Parametri  
 Questo metodo non ha parametri.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce il numero.  
  
## <a name="remarks"></a>Note  
 Nell'esempio seguente, l'oggetto numero di istanza è lo stesso come il valore restituito di questo metodo.  
  
```JavaScript  
var num = 1234;  
var s = num.valueOf();  
  
if (num === s)  
document.write("same");  
else  
document.write("different");  
  
// Output:  
// same  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]