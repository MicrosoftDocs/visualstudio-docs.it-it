---
title: "Proprietà prototype (Map) | Documenti Microsoft"
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
ms.assetid: c7b429cb-97b7-400e-a214-1b18bddd6b02
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 45601bdff2dfc8047f2499ab07dcdedd66662fc5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-map"></a>Proprietà prototype (Map)
Restituisce un riferimento al prototipo per una mappa.  
  
## <a name="syntax"></a>Sintassi  
  
```JavaScript  
map.prototype  
```  
  
## <a name="remarks"></a>Note  
 Il `map` argomento è il nome di una mappa.  
  
 Usare la proprietà `prototype` per fornire un set di funzionalità di base a una classe di oggetti. Le nuove istanze di un oggetto "ereditano" il comportamento del prototipo assegnato all'oggetto.  
  
 Ad esempio, per aggiungere un metodo all'oggetto `Map` che restituisce il valore dell'elemento più grande del set, dichiarare la funzione, aggiungerla a `Map.prototype` e quindi usarla.  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]