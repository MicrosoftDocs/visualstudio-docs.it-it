---
title: Funzione Eval (JavaScript) | Documenti Microsoft
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
- eval
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- eval function
- parsing, code
- parser
ms.assetid: 85587e39-9325-4b75-b9f9-9d7d475a2120
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 388e486f58bb70fd192701060a5faefaed8bd98e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="eval-function-javascript"></a>Funzione eval (JavaScript)
Valuta [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] codice e lo esegue.  
  
## <a name="syntax"></a>Sintassi  
  
```  
eval(codeString)   
```  
  
## <a name="parameters"></a>Parametri  
 `codeString`  
 Obbligatorio. Oggetto `String` valore contenente valido [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] codice.  
  
## <a name="remarks"></a>Note  
 Il `eval` funzione consente l'esecuzione dinamica di [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] codice sorgente.  
  
 Il `codeString` stringa viene analizzata dal [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] parser ed eseguito.  
  
 Il codice è passato per il `eval` funzione viene eseguita nello stesso contesto della chiamata al `eval` (funzione).  
  
 Se possibile, utilizzare il [funzione JSON. Parse](../../javascript/reference/json-parse-function-javascript.md) deserializzare testo JavaScript Object Notation (JSON). Il `JSON.parse` funzione è più sicura e viene eseguita più velocemente rispetto al `eval` (funzione).  
  
## <a name="example"></a>Esempio  
 Il codice seguente consente di inizializzare la variabile `myDate` a una data di test.  
  
```JavaScript  
var dateFn = "Date(1971,3,8)";  
var myDate;  
eval("myDate = new " + dateFn + ";");  
  
document.write(myDate);  
  
// Output: Thu Apr 8 00:00:00 PDT 1971  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Si applica a**: [oggetto globale](../../javascript/reference/global-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto String](../../javascript/reference/string-object-javascript.md)