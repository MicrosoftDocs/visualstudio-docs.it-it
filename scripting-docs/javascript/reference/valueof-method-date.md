---
title: Metodo valueOf (Date) | Documenti Microsoft
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
ms.assetid: 39a1f96e-14b0-4db2-b53d-cdfd67cbb208
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 87c5e6ea3c3e28d866f7cabf92dc97b81703b5b1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="valueof-method-date"></a>Metodo valueOf (Date)
Restituisce il valore di ora stored in millisecondi trascorsi dalla mezzanotte del 1 gennaio 1970 ora UTC.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
date.valueOf()  
```  
  
#### <a name="parameters"></a>Parametri  
 Il `date` oggetto è un'istanza di una data.  
  
## <a name="return-value"></a>Valore restituito  
 Il valore di ora stored in millisecondi trascorsi dalla mezzanotte del 1 gennaio 1970 ora UTC. Questo è lo stesso valore di `getTime`.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del `valueOf` metodo con una data.  
  
```JavaScript  
var myDate = new Date();  
myDate.setFullYear(2100, 5, 5);  
if (myDate.getTime() == myDate.valueOf())  
    document.write("values are the same");  
else  
    document.write("values are different");  
  
// Output: values are the same  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]