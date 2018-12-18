---
title: "prototipo di proprietà (intl. Collator) | Documenti Microsoft"
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
ms.assetid: c1bbb523-fb55-4395-b357-34d91cf5bba0
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 696535afde8c497bc98fc2c81a03854d66add6f4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-intlcollator"></a>Proprietà prototype (Intl.Collator)
Restituisce un riferimento al prototipo per un'utilità di confronto.  
  
## <a name="syntax"></a>Sintassi  
  
```JavaScript  
collator.prototype  
```  
  
## <a name="remarks"></a>Note  
 Il `collator` argomento è il nome dell'utilità di confronto.  
  
 Usare la proprietà `prototype` per fornire un set di funzionalità di base a una classe di oggetti. Le nuove istanze di un oggetto "ereditano" il comportamento del prototipo assegnato all'oggetto.  
  
 Ad esempio, per aggiungere un metodo all'oggetto `Intl.Collator` che restituisce il valore dell'elemento più grande del set, dichiarare la funzione, aggiungerla a `Intl.Collator.prototype` e quindi usarla.  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]