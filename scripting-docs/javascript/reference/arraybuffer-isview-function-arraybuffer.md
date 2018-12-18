---
title: Funzione arraybuffer. Isview (ArrayBuffer) | Documenti Microsoft
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
ms.assetid: 1887324f-892b-4fcd-ad33-748ba9517a06
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5aaae2acb38aa2f8c4b5e49ea203e86665315700
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="arraybufferisview-function-arraybuffer"></a>Funzione ArrayBuffer.isView (ArrayBuffer)
Determina se un oggetto fornisce una visualizzazione del buffer.  
  
## <a name="syntax"></a>Sintassi  
  
```JavaScript  
ArrayBuffer.isView(object)  
```  
  
#### <a name="parameters"></a>Parametri  
 `object`  
 Obbligatorio. Oggetto da testare.  
  
## <a name="return-value"></a>Valore restituito  
 `true` se una delle seguenti condizioni è vera:  
  
-   `object` è un oggetto `DataView`.  
  
-   `object` è una matrice tipizzata.  
  
 In caso contrario, il metodo restituisce `false`.  
  
## <a name="remarks"></a>Note  
  
## <a name="example"></a>Esempio  
 L'esempio seguente illustra l'uso della funzione `isView` per testare una matrice tipizzata e un oggetto `DataView`.  
  
```JavaScript  
var uint = new UInt8ClampedArray(10);  
  
if(console && console.log) {  
    console.log( ArrayBuffer.isView(uint) ); // Outputs true  
{  
var dataView = new DataView(uint.buffer);  
  
if(console && console.log) {  
    console.log( ArrayBuffer.isView(dataView) ); // Outputs true.  
}  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Uint8ClampedArray](../../javascript/reference/uint8clampedarray-object-javascript.md)