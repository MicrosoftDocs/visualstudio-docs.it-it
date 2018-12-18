---
title: Metodo join (Array) (JavaScript) | Documenti Microsoft
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
- join
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Join method
- concatenating strings, join method
- arrays [Visual Studio], joining
ms.assetid: 20f8fde1-014b-488e-9008-464a86e6b21f
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4591b12b3556384fef3e367d20cf9545d2f3dedd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="join-method-array-javascript"></a>Metodo join (Array) (JavaScript)
Aggiunge tutti gli elementi della matrice separati da una stringa di separazione specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
arrayObj.join([separator])   
```  
  
## <a name="parameters"></a>Parametri  
 `arrayObj`  
 Obbligatorio. Oggetto `Array`.  
  
 `separator`  
 Parametro facoltativo. Una stringa utilizzata per separare un elemento della matrice dall'elemento successivo nella finestra di `String`. Se omesso, gli elementi della matrice sono separati da una virgola.  
  
## <a name="remarks"></a>Note  
 Se qualsiasi elemento della matrice è **definito** o `null`, viene considerato come una stringa vuota.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del **join** metodo.  
  
```JavaScript  
var a, b;  
a = new Array(0,1,2,3,4);  
b = a.join("-");  
document.write(b);  
  
// Output:  
// 0-1-2-3-4  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto String](../../javascript/reference/string-object-javascript.md)