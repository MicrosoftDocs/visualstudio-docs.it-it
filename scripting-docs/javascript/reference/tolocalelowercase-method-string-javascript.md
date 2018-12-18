---
title: Metodo toLocaleLowerCase (String) (JavaScript) | Documenti Microsoft
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
- toLocaleLowerCase
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toLocaleLowerCase method
ms.assetid: add894d3-d14a-4dbc-a9b9-7ad1d3a2e581
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 642ced387e0d3b4cf763767ec147d6160ed7d36b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="tolocalelowercase-method-string-javascript"></a>Metodo toLocaleLowerCase (String) (JavaScript)
Converte tutti i caratteri alfabetici in lettere minuscole, tenendo conto delle impostazioni locali correnti dell'ambiente host.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
stringVar.toLocaleLowerCase( )  
```  
  
## <a name="remarks"></a>Note  
 Obbligatorio `stringVar` riferimento è un `String` o valore letterale stringa.  
  
 Il `toLocaleLowerCase` metodo converte i caratteri in una stringa, tenendo conto delle impostazioni locali correnti dell'ambiente host. Nella maggior parte dei casi, il risultato è lo stesso come il risultato di `toLowerCase` metodo. Risultati diversi se le regole per una lingua in conflitto con il mapping di maiuscole e Unicode regolare.  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Si applica a**: [oggetto stringa](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo toLocaleUpperCase (String)](../../javascript/reference/tolocaleuppercase-method-string-javascript.md)   
 [Metodo toLowerCase](../../javascript/reference/tolowercase-method-javascript.md)