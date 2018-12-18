---
title: Metodo Keys (matrice) (JavaScript) | Documenti Microsoft
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
ms.assetid: fc5b6a30-642c-4bd7-ad31-a42667af2f3f
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f600facc91dd10219196f580abd0f52537010dfd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="keys-method-array-javascript"></a>Metodo keys (matrice) (JavaScript)
Restituisce un iteratore che contiene i valori di indice della matrice.  
  
## <a name="syntax"></a>Sintassi  
  
```  
arrayObj.keys();  
```  
  
#### <a name="parameters"></a>Parametri  
 `arrayObj`  
 Obbligatorio. Oggetto array.  
  
## <a name="remarks"></a>Note  
  
## <a name="example"></a>Esempio  
 L'esempio seguente mostra come ottenere i valori di chiave di una matrice.  
  
```JavaScript  
var k = ["a", "b", "c"].keys();  
// k.next().value == 0  
// k.next().value == 1  
// k.next().value == 2   
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]