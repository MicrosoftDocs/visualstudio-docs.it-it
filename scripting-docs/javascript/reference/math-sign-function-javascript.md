---
title: Funzione Math. Sign (JavaScript) | Documenti Microsoft
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
ms.assetid: 8b462020-ceff-4947-8dd1-c78e6aff8d98
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2cae32118f2265e02c67592facff8e49e8edd633
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="mathsign-function-javascript"></a>Funzione Math.sign (JavaScript)
Restituisce il segno di un numero, indicante se il numero è positivo, negativo o 0.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Math.sign(number)  
```  
  
## <a name="remarks"></a>Note  
 L'argomento `number` obbligatorio è un'espressione numerica per la quale è necessario il segno.  
  
 Il valore restituito è uno dei seguenti:  
  
-   `NaN`, se `number` è `NaN`.  
  
-   -0, se `number` è - 0.  
  
-   +0, se `number` è +0.  
  
-   -1, se `number` è negativo e non - 0.  
  
-   +1, se `number` è positivo e diverso da +0.  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]