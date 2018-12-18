---
title: Funzione decodeURI (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: decodeURI
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: decodeURI method
ms.assetid: af6c81dc-10f4-4243-a7ce-d18ae3ea0fb8
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 97291142083ae88c7dc84d9cd08af5c3c39ff9e8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="decodeuri-function-javascript"></a>Funzione decodeURI (JavaScript)
Ottiene la versione non codificata di un codificato identificatore URI (Uniform Resource).  
  
## <a name="syntax"></a>Sintassi  
  
```  
decodeURI(URIstring)  
```  
  
## <a name="remarks"></a>Note  
 Obbligatorio `URIstring` argomento è un valore che rappresenta un URI codificato.  
  
 Utilizzare il `decodeURI` funzione anziché deprecate `unescape` (funzione).  
  
 Il `decodeURI` funzione restituisce un valore stringa.  
  
 Se il `URIString` non è valido, un URIError.  
  
 **Si applica a**: [oggetto globale](../../javascript/reference/global-object-javascript.md)  
  
## <a name="example"></a>Esempio  
 Il codice seguente consente innanzitutto di codificare un componente URI e lo decodifica.  
  
```JavaScript  
var uriEncode = encodeURIComponent ("www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write (uriEncode);  
document.write ("<br/>");  
document.write (uriDecode);  
  
// Output:  
// www.Not%20a%20URL.com  
// www.Not a URL.com  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione decodeURIComponent](../../javascript/reference/decodeuricomponent-function-javascript.md)   
 [Funzione encodeURI](../../javascript/reference/encodeuri-function-javascript.md)   
 [Oggetto Global](../../javascript/reference/global-object-javascript.md)