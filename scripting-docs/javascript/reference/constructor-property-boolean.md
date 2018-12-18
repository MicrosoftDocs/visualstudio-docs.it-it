---
title: "Proprietà constructor (Boolean) | Documenti Microsoft"
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
ms.assetid: b67ca875-23c6-4687-a5ce-1cdd25d1c923
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 091da5342c4713c8eba646a8bd78c315a6a0fa48
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="constructor-property-boolean"></a>Proprietà constructor (Boolean)
Specifica la funzione che crea un valore booleano.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
boolean.constructor([[value])  
```  
  
#### <a name="parameters"></a>Parametri  
 `boolean`  
 Il nome della proprietà booleana.  
  
 `value`  
 Parametro facoltativo. Specifica il valore della proprietà booleana. Può trattarsi di numeri di 1 o 0, o le stringhe "true" o "false".  
  
## <a name="remarks"></a>Note  
 Il `constructor` proprietà contiene un riferimento alla funzione che costruisce istanze dell'oggetto Boolean.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo della proprietà di costruttore.  
  
```JavaScript  
var x = new Boolean("true");  
  
if (x.constructor == Boolean)  
    document.write("Object is a Boolelan.");  
  
// Output:  
// Object is a Boolean.  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]