---
title: Metodo Sort (Array) (JavaScript) | Documenti Microsoft
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
- sort
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Sort method
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0462e60e623b99af458beb61eb7ef4215fe8ef41
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/05/2018
---
# <a name="sort-method-array-javascript"></a>Metodo sort (Array) (JavaScript)
Ordina un `Array`.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
arrayobj.sort(sortFunction)   
```  
  
## <a name="parameters"></a>Parametri  
 `arrayObj`  
 Obbligatorio. Qualsiasi oggetto `Array`.  
  
 `sortFunction`  
 Facoltativo. Il nome della funzione utilizzata per determinare l'ordine degli elementi. Se omesso, gli elementi vengono ordinati in ordine crescente, ordine di caratteri ASCII.  
  
## <a name="return-value"></a>Valore restituito  
 Matrice ordinata.  
  
## <a name="remarks"></a>Note  
 Il `sort` metodo ordinamenti di `Array` oggetto sul posto; no nuovi `Array` oggetto viene creato durante l'esecuzione.  
  
 `sortFunction`accetta due argomenti e deve restituire uno dei valori seguenti:  
  
-   Un valore negativo (minore di 0) se il primo argomento passato è minore rispetto al secondo argomento.  Il primo argomento è ordinato in un indice più basso.
  
-   Zero (0) se i due argomenti sono equivalenti.  I due argomenti vengono ordinati in relazione gli altri elementi nella matrice, ma non vengono ordinati uno rispetto a altro.
  
-   Un valore positivo (maggiore di 0) se il primo argomento è maggiore del secondo argomento.  Il secondo argomento è ordinato in un indice più basso.
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come utilizzare il metodo `sort`.  
  
```JavaScript  
var a = new Array(4, 11, 2, 10, 3, 1);  
  
var b = a.sort();  
document.write(b);  
document.write("<br/>");  
  
// This is ASCII character order.  
// Output: 1,10,11,2,3,4)  
  
// Sort the array elements with a function that compares array elements.  
b = a.sort(CompareForSort);  
document.write(b);  
document.write("<br/>");  
// Output: 1,2,3,4,10,11.  
  
// Sorts array elements in ascending order numerically.  
function CompareForSort(first, second)  
{  
    if (first == second)  
        return 0;  
    if (first < second)  
        return -1;  
    else  
        return 1;   
}  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]