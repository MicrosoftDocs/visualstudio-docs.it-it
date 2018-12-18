---
title: "Proprietà constructor (Date) | Documenti Microsoft"
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
ms.assetid: 5db153a1-788b-4a61-bfc8-2d2ec38f36ea
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 798064117e17ee5b2988396de3c6545917373b10
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="constructor-property-date"></a>Proprietà constructor (Date)
Specifica la funzione che crea una data.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
date.constructor  
```  
  
## <a name="remarks"></a>Note  
 Obbligatorio `date` è il nome di un oggetto Data.  
  
 La proprietà `constructor` è un membro del prototipo di ogni oggetto per cui esiste un prototipo. La proprietà `constructor` contiene un riferimento alla funzione che costruisce istanze di tale oggetto specifico.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo della proprietà di costruttore.  
  
```JavaScript  
var x = new Date("Hi");  
  
if (x.constructor == Date)  
    document.write("Object is a date.");  
  
// Output:  
// Object is a date.  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]