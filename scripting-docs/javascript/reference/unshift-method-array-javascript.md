---
title: Metodo unshift (Array) (JavaScript) | Documenti Microsoft
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
- unshift
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- unshift method
ms.assetid: 8c6a39ed-bab3-4ca4-9350-571a9427ec94
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c3f0d210514d04afa5cf467819a5e843925e1a68
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="unshift-method-array-javascript"></a>Metodo unshift (Array) (JavaScript)
Inserisce nuovi elementi all'inizio di una matrice.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
arrayObj.unshift([item1[, item2 [, . . . [, itemN]]]])  
```  
  
## <a name="parameters"></a>Parametri  
 `arrayObj`  
 Obbligatorio. Oggetto `Array`.  
  
 `item1, item2,. . ., itemN`  
 Parametro facoltativo. Elementi da inserire all'inizio del `Array`.  
  
## <a name="remarks"></a>Note  
 Il `unshift` metodo consente di inserire elementi all'inizio di una matrice, pertanto verranno visualizzati nello stesso ordine in cui compaiono nell'elenco di argomenti.  
  
## <a name="example"></a>Esempio  
 Nell'esempio riportato di seguito viene illustrato l'utilizzo del metodo `unshift`.  
  
```JavaScript  
var ar = new Array();  
ar.unshift(10, 11);  
ar.unshift(12, 13, 14);  
document.write(ar.toString());  
  
// Output: 12,13,14,10,11  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo shift (Array)](../../javascript/reference/shift-method-array-javascript.md)