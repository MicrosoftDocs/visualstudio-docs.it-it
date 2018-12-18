---
title: "Proprietà constructor (WeakSet) | Documenti Microsoft"
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
ms.assetid: 234e7104-9b78-4bfa-8f77-2bc44a570928
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5519c37f459e8236c6ed482b181799076832c50b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="constructor-property-weakset"></a>Proprietà constructor (WeakSet)
Specifica la funzione che crea un oggetto `WeakSet`.  
  
## <a name="syntax"></a>Sintassi  
  
```JavaScript  
weakset.constructor  
```  
  
## <a name="remarks"></a>Note  
 Il parametro `weakset` obbligatorio è il nome del set.  
  
 La proprietà `constructor` è un membro del prototipo di ogni oggetto per cui esiste un prototipo. Sono inclusi tutti gli oggetti JavaScript intrinseci ad eccezione degli oggetti `Global` e `Math`. La proprietà `constructor` contiene un riferimento alla funzione che costruisce istanze di tale oggetto specifico.  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]