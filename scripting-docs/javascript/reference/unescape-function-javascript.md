---
title: Funzione Unescape (JavaScript) | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- unescape
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Unescape method
ms.assetid: 4adf0270-88b5-4d54-8110-d879d6ae97c2
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 96601fc21f47c86aec8c3702a6861c3676aacacf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="unescape-function-javascript"></a>Funzione unescape (JavaScript)
Decodifica `String` oggetti codificati con il `escape` (funzione). Deprecato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
unescape(charString)   
```  
  
## <a name="remarks"></a>Note  
 Obbligatorio `charString` argomento è un `String` oggetto o un valore letterale che si desidera decodificare.  
  
 Il `unescape` funzione restituisce un valore stringa che contiene il contenuto di `charstring`. Tutti i caratteri codificati con %*xx* formato esadecimale sono sostituiti dai rispettivi equivalenti di set di caratteri ASCII.  
  
 I caratteri codificati in **%u** *xxxx* formato (caratteri Unicode) sono sostituiti con il carattere Unicode con codifica esadecimale *xxxx*.  
  
> [!NOTE]
>  Il `unescape` funzione non deve essere usata per decodificare Uniform Resource Identifiers (URI). Utilizzare `decodeURI` e `decodeURIComponent` funzioni.  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Si applica a**: [oggetto globale](../../javascript/reference/global-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione decodeURI](../../javascript/reference/decodeuri-function-javascript.md)   
 [Funzione decodeURIComponent](../../javascript/reference/decodeuricomponent-function-javascript.md)   
 [Funzione escape](../../javascript/reference/escape-function-javascript.md)   
 [Oggetto String](../../javascript/reference/string-object-javascript.md)