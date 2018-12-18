---
title: "Proprietà constructor (WeakMap) | Documenti Microsoft"
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
ms.assetid: 1e3f9333-ce75-4d32-9b14-fbe81fd73dfb
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5c7340e1e5eeff9a80e231cf1aa49443adc94e72
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="constructor-property-weakmap"></a>Proprietà constructor (WeakMap)
Specifica la funzione che crea un `WeakMap` oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```JavaScript  
weakmap.constructor  
```  
  
## <a name="remarks"></a>Note  
 Obbligatorio `weakmap` è il nome di `WeakMap` oggetto.  
  
 La proprietà `constructor` è un membro del prototipo di ogni oggetto per cui esiste un prototipo. Sono inclusi tutti gli oggetti JavaScript intrinseci ad eccezione degli oggetti `Global` e `Math`. La proprietà `constructor` contiene un riferimento alla funzione che costruisce istanze di tale oggetto specifico.  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]