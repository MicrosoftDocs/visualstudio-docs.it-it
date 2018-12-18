---
title: Funzione ScriptEngine (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ScriptEngine
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: ScriptEngine function
ms.assetid: 65674b2b-d2c2-4493-99b3-f0d20fda8249
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d441fcce065677f7b673a9979acff9cf9aa2ce90
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="scriptengine-function-javascript"></a>Funzione ScriptEngine (JavaScript)
Ottiene il nome del linguaggio di scripting in uso.  
  
## <a name="syntax"></a>Sintassi  
  
```  
ScriptEngine()  
```  
  
## <a name="remarks"></a>Note  
 La funzione `ScriptEngine` restituisce "JScript", che indica che [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] è il motore di script attuale.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente illustra l'uso della funzione `ScriptEngine`:  
  
```JavaScript  
if (window.ScriptEngine) {  
    console.log(window.ScriptEngine());  
}  
  
// Output: JScript  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione ScriptEngineBuildVersion](../../javascript/reference/scriptenginebuildversion-function-javascript.md)   
 [Funzione ScriptEngineMajorVersion](../../javascript/reference/scriptenginemajorversion-function-javascript.md)   
 [Funzione ScriptEngineMinorVersion](../../javascript/reference/scriptengineminorversion-function-javascript.md)