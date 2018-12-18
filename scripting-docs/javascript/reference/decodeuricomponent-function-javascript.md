---
title: Funzione decodeURIComponent (JavaScript) | Documenti Microsoft
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
- decodeURIComponent
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- decodeURIComponent method
ms.assetid: 486ccee2-afd7-4863-97ce-4adb50cf39c0
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ef7bdcd374a328bad632381d19e9823853d37f01
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="decodeuricomponent-function-javascript"></a>Funzione decodeURIComponent (JavaScript)
Ottiene la versione non codificata di un componente codificato di un URI (Uniform Resource Identifier).  
  
## <a name="syntax"></a>Sintassi  
  
```  
decodeURIComponent(encodedURIString)  
```  
  
## <a name="remarks"></a>Note  
 Obbligatorio `encodedURIString` argomento è un valore che rappresenta un componente URI codificato.  
  
 Un componente URI fa parte di un URI completo.  
  
 Se il `encodedURIString` non è valido, un URIError.  
  
## <a name="example"></a>Esempio  
 Il codice seguente prima codifica e decodifica quindi un URI.  
  
```JavaScript  
var uriEncode = encodeURI ("http://www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write (uriEncode);  
document.write("<br/>");  
document.write (uriDecode);  
  
// Output:  
// http://www.Not%20a%20URL.com  
// http://www.Not a URL.com  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione decodeURI](../../javascript/reference/decodeuri-function-javascript.md)   
 [Funzione encodeURI](../../javascript/reference/encodeuri-function-javascript.md)