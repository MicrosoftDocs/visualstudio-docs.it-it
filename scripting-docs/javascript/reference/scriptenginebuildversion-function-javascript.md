---
title: Funzione ScriptEngineBuildVersion (JavaScript) | Documenti Microsoft
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
- ScriptEngineBuildVersion
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- ScriptEngineBuildVersion function
ms.assetid: 7e255030-b0a3-420b-9c96-bb3e93c9333f
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fd458d43bebfb0d0e0b2cb6bebb483c22a60b4f0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="scriptenginebuildversion-function-javascript"></a>Funzione ScriptEngineBuildVersion (JavaScript)
Ottiene il numero di versione build del motore di scripting in uso.  
  
## <a name="syntax"></a>Sintassi  
  
```  
ScriptEngineBuildVersion()  
```  
  
## <a name="remarks"></a>Note  
 Il valore restituito corrisponde direttamente alle informazioni sulla versione contenute nella libreria di collegamento dinamico (DLL) per il linguaggio di scripting in uso.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente illustra l'uso della funzione `ScriptEngineBuildVersion`:  
  
```JavaScript  
if(window.ScriptEngineBuildVersion) {  
    console.log(window.ScriptEngineBuildVersion());  
}  
  
// Output: <current build version>  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione ScriptEngine](../../javascript/reference/scriptengine-function-javascript.md)   
 [Funzione ScriptEngineMajorVersion](../../javascript/reference/scriptenginemajorversion-function-javascript.md)   
 [Funzione ScriptEngineMinorVersion](../../javascript/reference/scriptengineminorversion-function-javascript.md)