---
title: "prototipo di proprietà (intl. DateTimeFormat) | Documenti Microsoft"
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
ms.assetid: e1e693ff-1775-407e-b655-18a60d238ded
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 64dff17e4aaf62940f4c9c5f8b422fcbceb7212a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-intldatetimeformat"></a>Proprietà prototype (Intl.DateTimeFormat)
Restituisce un riferimento al prototipo per un formattatore.  
  
## <a name="syntax"></a>Sintassi  
  
```JavaScript  
dateTimeFormat.prototype  
```  
  
## <a name="remarks"></a>Note  
 Il `dateTimeFormat` argomento è il nome di un formattatore.  
  
 Usare la proprietà `prototype` per fornire un set di funzionalità di base a una classe di oggetti. Le nuove istanze di un oggetto "ereditano" il comportamento del prototipo assegnato all'oggetto.  
  
 Ad esempio, per aggiungere un metodo all'oggetto `Intl.DateTimeFormat` che restituisce il valore dell'elemento più grande del set, dichiarare la funzione, aggiungerla a `Intl.DateTimeFormat.prototype` e quindi usarla.  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]