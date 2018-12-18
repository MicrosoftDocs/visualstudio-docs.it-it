---
title: Direttiva use strict | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- strict_JavaScriptKeyword
- use strict
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- strict mode
- use strict directive
- use strict
ms.assetid: b532e8c9-548c-4bbe-b2fc-5459ebd62e56
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0bd951255f5d5719c3aa216965605840ba12010d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="use-strict-directive"></a>direttiva use strict
Impedisce l'uso di alcune funzionalità di JavaScript. Supportato in Internet Explorer 10 e [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] solo app.  
  
## <a name="syntax"></a>Sintassi  
  
```JavaScript  
use strict  
```  
  
## <a name="remarks"></a>Note  
  
## <a name="example"></a>Esempio  
 Il codice seguente causa un errore di sintassi perché in modalità strict tutte le variabili devono essere dichiarate con `var`.  
  
```JavaScript  
"use strict";  
function testFunction(){  
   var testvar = 4;  
    return testvar;  
}  
intvar = 5;  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Strict Mode](../../javascript/advanced/strict-mode-javascript.md)