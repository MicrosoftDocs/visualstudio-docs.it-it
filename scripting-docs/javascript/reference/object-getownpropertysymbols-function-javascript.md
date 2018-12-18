---
title: Funzione Object. getownpropertysymbols (JavaScript) | Documenti Microsoft
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
ms.assetid: 68dd69b9-5a33-44c2-ba5f-21a4ae6c0879
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2cc47ae365841332f11cb02da1469a4c9fff80c3
ms.sourcegitcommit: abae48f476832f79cc2c5bac43bb1226d3fe4e48
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2018
---
# <a name="objectgetownpropertysymbols-function-javascript"></a>Funzione Object.getOwnPropertySymbols (JavaScript)
Restituisce le proprietà di simboli propri di un oggetto. Le proprietà di simboli propri di un oggetto sono le proprietà definite direttamente sull'oggetto stesso e non ereditate dal prototipo dell'oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Object.getOwnPropertySymbols(object);  
```  
  
#### <a name="parameters"></a>Parametri  
 `object`  
 Obbligatorio. Oggetto che contiene i simboli propri.  
  
## <a name="return-value"></a>Valore restituito  
 Matrice che contiene i simboli propri dell'oggetto.  
  
## <a name="remarks"></a>Note  
 Per ottenere le proprietà dei simboli di un oggetto, sarà necessario usare `Object.getOwnPropertySymbols`. `Object.getOwnPropertyNames` non restituirà le proprietà dei simboli.  
  
## <a name="example"></a>Esempio  
 L'esempio di codice seguente illustra come ottenere le proprietà dei simboli di un oggetto.  
  
```JavaScript  
var obj = {};  
var key = Symbol('description');  
  
obj[key] = 'data';  
  
var symbols = Object.getOwnPropertySymbols(obj);  
  
console.log(symbols[0].toString());  
  
// Output:  
// undefined  
// Symbol(description)  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]