---
title: Metodo Fill (Array) (JavaScript) | Documenti Microsoft
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
ms.assetid: 11526627-c0bb-4157-a8c4-0a039079b4a1
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4546bafb3fa3a8c242b8b7ef4ef2863ea86bf179
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="fill-method-array-javascript"></a>Metodo fill (Array) (JavaScript)
Popola una matrice con un valore specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
arrayObj.fill(value [ , start [ , end ] ]);  
```  
  
#### <a name="parameters"></a>Parametri  
 `arrayObj`  
 Obbligatorio. Oggetto array.  
  
 `value`  
 Obbligatorio. Valore usato per popolare la matrice.  
  
 `start`  
 Parametro facoltativo. Indice iniziale usato per popolare i valori della matrice. Il valore predefinito è 0.  
  
 `end`  
 Parametro facoltativo. Indice finale usato per popolare i valori della matrice. Il valore predefinito è la proprietà length dell'oggetto `this`.  
  
## <a name="remarks"></a>Note  
 Se `start` è negativo, `start` viene trattato come `length` + `start`, dove `length` è la lunghezza della matrice. Se `end` è negativo, `end` viene trattato come `length` + `end`.  
  
## <a name="example"></a>Esempio  
 Gli esempi di codice seguenti popolano una matrice con valori.  
  
```JavaScript  
[0, 0, 0].fill(7, 1);  
// Array contains [0,7,7]  
  
[0, 0, 0].fill(7);  
// Array contains [7,7,7]  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]