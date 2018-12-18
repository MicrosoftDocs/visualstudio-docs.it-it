---
title: "Proprietà length (Array) (JavaScript) | Documenti Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: length Property
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Array object
- Length property
- length property (array)
ms.assetid: e1c6377c-2e84-440a-9660-f1f512e4a938
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6e69fd5387b1d7430491b1693dec07581f165cc9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="length-property-array-javascript"></a>Proprietà length (Array) (JavaScript)
Ottiene o imposta la lunghezza della matrice. Si tratta di un numero incrementato di uno rispetto all'elemento massimo definito in una matrice.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
numVar = arrayObj.length   
```  
  
## <a name="parameters"></a>Parametri  
 `numVar`  
 Obbligatorio. Qualsiasi numero.  
  
 `arrayObj`  
 Obbligatorio. Qualsiasi oggetto `Array`.  
  
## <a name="remarks"></a>Note  
 In JavaScript le matrici sono sparse e gli elementi in una matrice non sono contigue. La proprietà `length` non è necessariamente il numero di elementi nella matrice. Ad esempio, nella definizione di matrice seguente `my_array.length` contiene 7, non 2:  
  
```JavaScript  
var my_array = new Array( );  
my_array[0] = "Test";  
my_array[6] = "Another Test";  
```  
  
 Se la proprietà `length` ha un valore inferiore al suo valore precedente, la matrice verrà troncata e qualsiasi elemento con indici di matrice uguali o maggiori del nuovo valore della proprietà `length` viene perso.  
  
 Se la proprietà della lunghezza è maggiore rispetto al suo valore precedente, la matrice viene espansa e gli eventuali nuovi elementi creati hanno il valore `undefined`.  
  
 Nell'esempio seguente viene illustrato l'uso della proprietà `length`:  
  
```JavaScript  
var a;  
a = new Array(0,1,2,3,4);  
document.write(a.length);  
  
// Output  
// 5  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
> [!NOTE]
>  A partire dalla modalità standard di Internet Explorer 9, le virgole finali incluse nell'inizializzazione di una matrice vengono gestite in modo diverso.