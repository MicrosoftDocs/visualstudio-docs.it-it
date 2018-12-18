---
title: toString (metodo) 1 (booleano) | Documenti Microsoft
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
ms.assetid: c46b43c0-6946-407a-b0e0-49cba90e226a
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 17dd9503e4e09aafca3d153662bf7487538cda3d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="tostring-method-boolean-1"></a>toString (Boolean) 1 (metodo)
Restituisce la rappresentazione in formato stringa di un oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
boolean.toString()  
```  
  
## <a name="parameters"></a>Parametri  
 `boolean`  
 Obbligatorio. Oggetto per cui ottenere una rappresentazione di stringa.  
  
## <a name="return-value"></a>Valore restituito  
 Se il valore booleano è `true`, restituisce "true". In caso contrario, restituisce "false".  
  
## <a name="remarks"></a>Note  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del **toString** metodo.  
  
```JavaScript  
var s = new Boolean(0);  
document.write(s.toString());  
  
// Output: false;  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]