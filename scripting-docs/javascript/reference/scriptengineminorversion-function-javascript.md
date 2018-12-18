---
title: Funzione ScriptEngineMinorVersion (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ScriptEngineMinorVersion
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: ScriptEngineMinorVersion function
ms.assetid: caa506a5-e61d-4b2a-8b83-83d56a2f26cd
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b1be01c0ee10cac1c68d4750455151032a59a8e6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="scriptengineminorversion-function-javascript"></a>Funzione ScriptEngineMinorVersion (JavaScript)
Ottiene il numero di versione secondaria del motore di scripting in uso.  
  
## <a name="syntax"></a>Sintassi  
  
```  
ScriptEngineMinorVersion()  
```  
  
## <a name="remarks"></a>Note  
 Il valore restituito corrisponde direttamente alle informazioni sulla versione contenute nella libreria di collegamento dinamico (DLL) per il linguaggio di scripting in uso.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente illustra l'uso della funzione `ScriptEngineMinorVersion`.  
  
```JavaScript  
if (window.ScriptEngineMinorVersion) {  
    console.log(window.ScriptEngineMinorVersion());  
}  
  
//Output: <current minor version>  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione ScriptEngine](../../javascript/reference/scriptengine-function-javascript.md)   
 [Funzione ScriptEngineBuildVersion](../../javascript/reference/scriptenginebuildversion-function-javascript.md)   
 [Funzione ScriptEngineMajorVersion](../../javascript/reference/scriptenginemajorversion-function-javascript.md)