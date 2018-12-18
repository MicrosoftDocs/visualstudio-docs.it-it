---
title: Funzione ScriptEngineMajorVersion (JavaScript) | Documenti Microsoft
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
- ScriptEngineMajorVersion
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- ScriptEngineMajorVersion function
ms.assetid: 3e251bce-1e14-4cb5-b79f-53845d1920fd
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 815e6fb92744fc2145cae2cbaa6a5574c3ea3ecc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="scriptenginemajorversion-function-javascript"></a>Funzione ScriptEngineMajorVersion (JavaScript)
Ottiene il numero di versione principale del motore di scripting in uso.  
  
## <a name="syntax"></a>Sintassi  
  
```  
ScriptEngineMajorVersion()  
```  
  
## <a name="remarks"></a>Note  
 Il valore restituito corrisponde direttamente alle informazioni sulla versione contenute nella libreria di collegamento dinamico (DLL) per il linguaggio di scripting in uso.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente illustra l'uso della funzione `ScriptEngineMajorVersion`:  
  
```JavaScript  
if (window.ScriptEngineMajorVersion) {  
    console.log(window.ScriptEngine());   
}  
  
Output: <current major version>  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione ScriptEngine](../../javascript/reference/scriptengine-function-javascript.md)   
 [Funzione ScriptEngineBuildVersion](../../javascript/reference/scriptenginebuildversion-function-javascript.md)   
 [Funzione ScriptEngineMinorVersion](../../javascript/reference/scriptengineminorversion-function-javascript.md)