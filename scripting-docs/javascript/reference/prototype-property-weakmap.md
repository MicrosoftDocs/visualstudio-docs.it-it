---
title: "Proprietà prototype (WeakMap) | Documenti Microsoft"
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
ms.assetid: d28b8a9b-38c9-443d-9586-7cc74784bd99
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5cc1bff0d62f2aeb8d6fb78a0857f287fb34078c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-weakmap"></a>Proprietà prototype (WeakMap)
Restituisce un riferimento al prototipo per un `WeakMap` oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```JavaScript  
weakmap.prototype  
```  
  
## <a name="remarks"></a>Note  
 Il `weakmap` argomento è il nome di un `WeakMap` oggetto.  
  
 Usare la proprietà `prototype` per fornire un set di funzionalità di base a una classe di oggetti. Le nuove istanze di un oggetto "ereditano" il comportamento del prototipo assegnato all'oggetto.  
  
 Ad esempio, per aggiungere un metodo per il `WeakMap` oggetto che restituisce il valore dell'elemento più grande del `WeakMap`, dichiarare la funzione, aggiungerla a `WeakMap.prototype`e quindi usarla.  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]