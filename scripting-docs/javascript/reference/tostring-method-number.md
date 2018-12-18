---
title: Metodo toString (Number) | Documenti Microsoft
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
ms.assetid: 07c3484b-d9d8-4451-a2be-88a19a081966
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f6be170061faf4c2782c7247c80c55065c3a6742
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="tostring-method-number"></a>Metodo toString (Number)
Restituisce una rappresentazione di stringa di un numero.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
number.toString()  
```  
  
## <a name="parameters"></a>Parametri  
 `number`  
 Obbligatorio. Il numero per rappresentare sotto forma di stringa.  
  
## <a name="return-value"></a>Valore restituito  
 Rappresentazione di stringa del numero.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del **toString** metodo con un numero.  
  
```JavaScript  
var number = 234.567;  
var s = number.toString();  
document.write(s.length);  
  
// Output: 7  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]