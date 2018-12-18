---
title: Metodo getFullYear (Date) (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getFullYear
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, returning year
- Date object
- getFullYear method
ms.assetid: f9ec1262-02e9-4791-90b5-48f33b1dc4bc
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 211d6c86435e39eb75b9b1ce3415738541ca07db
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="getfullyear-method-date-javascript"></a>Metodo getFullYear (Date) (JavaScript)
Ottiene l'anno, utilizzando l'ora locale.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
dateObj.getFullYear()   
```  
  
#### <a name="parameters"></a>Parametri  
 Il riferimento `dateObj` obbligatorio è un oggetto `Date` .  
  
## <a name="return-value"></a>Valore restituito  
 Anno, come numero a quattro cifre. Ad esempio, l'anno 1976 viene restituito come 1976. Anni specificato come due cifre di `Date` costruttore o in `setFullYear` si presuppone che siano ventesimo secolo, supponendo "5/14/12," `getFullYear` restituisce "1912".  
  
## <a name="remarks"></a>Note  
 Per ottenere l'anno utilizzando l'ora UTC (Universal Coordinated Time), utilizzare il `getUTCFullYear` metodo.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del **getFullYear** metodo.  
  
```JavaScript  
var date = new Date("1/1/01");  
document.write(date.getFullYear());  
  
// Output: 1901  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Si applica a**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getUTCFullYear (Date)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [Metodo setFullYear (Date)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [Metodo setUTCFullYear (Date)](../../javascript/reference/setutcfullyear-method-date-javascript.md)