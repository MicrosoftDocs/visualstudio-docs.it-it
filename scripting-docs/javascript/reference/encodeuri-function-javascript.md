---
title: Funzione encodeURI (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- encodeURI
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- encodeURI method
ms.assetid: 17bab5a2-bcd4-46c2-8b52-b2b5a0ed98a3
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8cf9bbdf34c0481c889d1176bc32ab0246a333a4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="encodeuri-function-javascript"></a>Funzione encodeURI (JavaScript)
Codifica una stringa di testo come un valido identificatore URI (Uniform Resource)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
encodeURI(  
URIString  
)  
  
```  
  
## <a name="remarks"></a>Note  
 Obbligatorio `URIString` argomento è un valore che rappresenta un URI codificato.  
  
 Il `encodeURI` funzione restituisce un URI codificato. Se si passa il risultato a `decodeURI`, viene restituita la stringa originale. Il `encodeURI` funzione non esegue la codifica i caratteri seguenti: ":", "/", ";" e "?". Utilizzare `encodeURIComponent` per codificare i caratteri.  
  
## <a name="example"></a>Esempio  
 Il codice seguente prima codifica e decodifica quindi un URI.  
  
```JavaScript  
var uriEncode = encodeURI ("http://www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write(uriEncode);  
document.write("<br/>");  
document.write(uriDecode);  
  
// Output:  
// http://www.Not%20a%20URL.com  
// http://www.Not a URL.com  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione decodeURI](../../javascript/reference/decodeuri-function-javascript.md)   
 [Funzione DecodeURIComponent](../../javascript/reference/decodeuricomponent-function-javascript.md)