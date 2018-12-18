---
title: Metodo charAt (String) (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: charAt
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- String object, returning characters
- charAt method
- characters, returning part of
ms.assetid: 63173e15-17f6-47c5-8f94-98ef1eb04c1a
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 201d85fec4ba184f0842c7401d986650b9ee078c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="charat-method-string-javascript"></a>Metodo charAt (String) (JavaScript)
Restituisce il carattere in corrispondenza dell'indice specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
strObj. charAt(index)  
```  
  
## <a name="parameters"></a>Parametri  
 `strObj`  
 Obbligatorio. Qualsiasi `String` o valore letterale stringa.  
  
 `index`  
 Obbligatorio. Indice in base zero del carattere desiderato.  
  
## <a name="remarks"></a>Note  
 Il `charAt` metodo restituisce un valore di carattere è uguale al carattere specificato `index`. Il primo carattere in una stringa è in corrispondenza dell'indice 0, il secondo è in corrispondenza dell'indice 1 e così via. I valori di `index` che sono raggiungibili restituito una stringa vuota.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del `charAt` metodo:  
  
```JavaScript  
var str = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";  
document.write(str.charAt(str.length - 1));  
  
// Output: Z  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Si applica a**: [oggetto stringa](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto String](../../javascript/reference/string-object-javascript.md)