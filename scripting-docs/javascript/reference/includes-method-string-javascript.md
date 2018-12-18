---
title: Metodo Includes (String) (JavaScript) | Documenti Microsoft
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
ms.assetid: 2639e4e5-23ba-424a-80ea-be067a4cd65e
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 848143b64d3e32452aea41f08b6f5c57879d3e17
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="includes-method-string-javascript"></a>Metodo includes (String) (JavaScript)
Restituisce un valore booleano che indica se la stringa passata è contenuta nell'oggetto string.  
  
## <a name="syntax"></a>Sintassi  
  
```  
stringObj.includes(substring [, position]);  
```  
  
#### <a name="parameters"></a>Parametri  
 `stringObj`  
 Obbligatorio. Oggetto stringa rispetto da testare.  
  
 `substring`  
 Obbligatorio. Stringa da testare.  
  
 `position`  
 Parametro facoltativo. Posizione del primo carattere da testare nell'oggetto string, partendo da 0.  
  
## <a name="return-value"></a>Valore restituito  
 Se la stringa passata è contenuta nell'oggetto string, il metodo `includes` restituisce `true`; in caso contrario, restituisce `false`.  
  
## <a name="remarks"></a>Note  
  
## <a name="example"></a>Esempio  
  
```JavaScript  
// Returns true   
"abcde".includes("cd")  
"abcde".includes("cd", 2)  
  
// Returns false  
"abcde".includes("CD")  
"abcde".includes("cd", 3)  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]