---
title: Funzione Array. From (Array) (JavaScript) | Documenti Microsoft
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
ms.assetid: 1bf59a99-f860-4c4d-b4c6-d5f1f946a490
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a240cb439942bfeb6b4c9a1febb4d24cef1c5c18
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="arrayfrom-function-array-javascript"></a>Funzione Array.from (Array) (JavaScript)
Restituisce una matrice da un oggetto di tipo matrice o iterabile.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Array.from (arrayLike [ , mapfn [ , thisArg ] ] );  
```  
  
#### <a name="parameters"></a>Parametri  
 `arrayLike`  
 Obbligatorio. Oggetto di tipo matrice o un oggetto iterabile.  
  
 `mapfn`  
 Parametro facoltativo. Funzione di mapping da chiamare su ogni elemento in `arrayLike`.  
  
 `thisArg`  
 Parametro facoltativo. Specifica l'oggetto `this` nella funzione di mapping.  
  
## <a name="remarks"></a>Note  
 Il parametro `arrayLike` deve essere un oggetto con elementi indicizzati e una proprietà `length` o un oggetto iterabile, ad esempio un oggetto `Set`.  
  
 La funzione di mapping facoltativa viene chiamata su ogni elemento nella matrice.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente restituisce una matrice da una raccolta di nodi elemento DOM.  
  
```JavaScript  
var elemArr = Array.from(document.querySelectorAll('*'));  
var elem = elemArr[0]; // elem contains a reference to the first DOM element  
  
```  
  
## <a name="example"></a>Esempio  
 L'esempio seguente restituisce una matrice di caratteri.  
  
```JavaScript  
var charArr = Array.from("abc");  
// charArr[0] == "a";  
```  
  
## <a name="example"></a>Esempio  
 L'esempio seguente restituisce una matrice di oggetti contenuti nella raccolta.  
  
```JavaScript  
var setObj = new Set("a", "b", "c");  
var objArr = Array.from(setObj);  
// objArr[1] == "b";   
```  
  
## <a name="example"></a>Esempio  
 L'esempio seguente illustra l'uso della sintassi freccia e una funzione di mapping per modificare il valore degli elementi.  
  
```JavaScript  
var arr = Array.from([1, 2, 3], x => x * 10);  
// arr[0] == 10;  
// arr[1] == 20;  
// arr[2] == 30;  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]