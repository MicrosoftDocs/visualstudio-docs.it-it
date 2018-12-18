---
title: "prototipo di proprietà (intl. NumberFormat) | Documenti Microsoft"
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
ms.assetid: 7f6a7e26-108b-4b32-97c2-7f96b9252c50
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b037ce7476574252966e17fcf64246beeaaea1e8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-intlnumberformat"></a>Proprietà prototype (Intl.NumberFormat)
Restituisce un riferimento al prototipo per un formattatore.  
  
## <a name="syntax"></a>Sintassi  
  
```JavaScript  
numberFormat.prototype  
```  
  
## <a name="remarks"></a>Note  
 Il `numberFormat` argomento è il nome di un formattatore.  
  
 Usare la proprietà `prototype` per fornire un set di funzionalità di base a una classe di oggetti. Le nuove istanze di un oggetto "ereditano" il comportamento del prototipo assegnato all'oggetto.  
  
 Ad esempio, per aggiungere un metodo all'oggetto `Intl.NumberFormat` che restituisce il valore dell'elemento più grande del set, dichiarare la funzione, aggiungerla a `Intl.NumberFormat.prototype` e quindi usarla.  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]