---
title: Funzione escape (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: escape
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- encoding string objects
- Escape method
- hexadecimal
- String object, encoding
ms.assetid: caa92bea-ba69-4109-a68a-6e2debda463a
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b53a447ae6dde917c12a4711d9038136dc4500cf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="escape-function-javascript"></a>Funzione escape (JavaScript)
Codifica delle stringhe in modo che possano essere letti su tutti i computer. Deprecato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
escape(charString)   
```  
  
## <a name="remarks"></a>Note  
 Obbligatorio `charString` è qualsiasi valore `String` oggetto o un valore letterale da codificare.  
  
 Il **escape** funzione restituisce un valore stringa (in formato Unicode) che contiene il contenuto di `charstring`. Tutti gli spazi, segni di punteggiatura, i caratteri accentati e altri caratteri non ASCII vengono sostituiti con `%` *xx* codifica, in cui *xx* equivalente per il numero esadecimale che rappresenta il carattere. Ad esempio, uno spazio viene restituito come "% 20".  
  
 I caratteri con un valore maggiore di 255 vengono archiviati usando il **%u** *xxxx* formato.  
  
> [!NOTE]
>  Il **escape** funzione non deve essere usata per codificare Uniform Resource Identifiers (URI). Utilizzare `encodeURI` e `encodeURIComponent` funzioni.  
  
 **Si applica a**: [oggetto globale](../../javascript/reference/global-object-javascript.md)  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione encodeURI](../../javascript/reference/encodeuri-function-javascript.md)   
 [Funzione encodeURIComponent](../../javascript/reference/encodeuricomponent-function-javascript.md)   
 [Oggetto String](../../javascript/reference/string-object-javascript.md)   
 [Funzione unescape](../../javascript/reference/unescape-function-javascript.md)