---
title: Metodo toLocaleUpperCase (String) (JavaScript) | Documenti Microsoft
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
- toLocaleUpperCase
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toLocaleUpperCase method
ms.assetid: e927adb6-475e-44b2-91f7-cedda10a39b0
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 07a89560dde0319598da30fc3451524112b99eac
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="tolocaleuppercase-method-string-javascript"></a>Metodo toLocaleUpperCase (String) (JavaScript)
Restituisce una stringa in cui tutti i caratteri alfabetici sono stati impostazioni locali correnti dell'ambiente convertito in caratteri maiuscoli, prendendo in considerazione l'host.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
stringVar.toLocaleUpperCase( )  
```  
  
## <a name="remarks"></a>Note  
 Obbligatorio `stringVar` riferimento è un `String` o valore letterale stringa.  
  
 Il `toLocaleUpperCase` metodo converte i caratteri in una stringa, tenendo conto delle impostazioni locali correnti dell'ambiente host. Nella maggior parte dei casi, il risultato è lo stesso come risultato di `toUpperCase` metodo. Risultati diversi se le regole per una lingua in conflitto con il mapping di maiuscole e Unicode regolare.  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Si applica a**: [oggetto stringa](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo toLocaleLowerCase (String)](../../javascript/reference/tolocalelowercase-method-string-javascript.md)   
 [Metodo toUpperCase (String)](../../javascript/reference/touppercase-method-string-javascript.md)