---
title: Funzione encodeURIComponent (JavaScript) | Documenti Microsoft
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
- encodeURIComponent
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- encodeURIComponent method
ms.assetid: 8202bce6-1342-40dc-a5ef-ac6d210a7d15
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 56680e9bcfe1de61d8a1eabd0ff8d2eced01d603
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="encodeuricomponent-function-javascript"></a>Funzione encodeURIComponent (JavaScript)
Codifica una stringa di testo come un componente valido di un URI (Uniform Resource Identifier).  
  
## <a name="syntax"></a>Sintassi  
  
```  
encodeURIComponent(encodedURIString)  
```  
  
## <a name="remarks"></a>Note  
 Obbligatorio `encodedURIString` argomento è un valore che rappresenta un componente URI codificato.  
  
 Il `encodeURIComponent` funzione restituisce un URI codificato. Se si passa il risultato a `decodeURIComponent`, viene restituita la stringa originale. Poiché il `encodeURIComponent` funzione codifica tutti i caratteri, prestare attenzione se la stringa rappresenta un percorso, ad esempio **/folder1/folder2/default.html**. I caratteri di barra verranno codificati e non sarà validi se inviato come richiesta a un server web. Utilizzare il `encodeURI` funzione se la stringa contiene più di un componente URI.  
  
## <a name="example"></a>Esempio  
 Il codice seguente consente innanzitutto di codificare un componente URI e lo decodifica.  
  
```JavaScript  
var uriEncode = encodeURIComponent ("www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write(uriEncode);  
document.write("<br/>");  
document.write(uriDecode);  
  
// Output:  
// www.Not%20a%20URL.com  
// www.Not a URL.com  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione decodeURI](../../javascript/reference/decodeuri-function-javascript.md)   
 [Funzione DecodeURIComponent](../../javascript/reference/decodeuricomponent-function-javascript.md)