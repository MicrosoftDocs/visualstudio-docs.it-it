---
title: "Proprietà stackTraceLimit (Error) (JavaScript) | Documenti Microsoft"
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
- Error.stackTraceLimit
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- error stack track limit [JavaScript]
- JavaScript error stack
- error stack [JavaScript]
- JavaScript stack trace limit
ms.assetid: 127ef8e8-892e-4263-9ebc-03364af01212
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9af736ee8b385f93b761f1dfa021c23ee5376292
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="stacktracelimit-property-error-javascript"></a>Proprietà stackTraceLimit (Error) (JavaScript)
Ottiene o imposta il limite di traccia dello stack, che equivale al numero di frame di errore da visualizzare. Il limite predefinito è 10.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Error  
.stackTraceLimit   
```  
  
## <a name="remarks"></a>Note  
 È possibile impostare il `stackTraceLimit` su qualsiasi valore positivo compreso tra 0 e `Infinity`. Se il `stackTraceLimit` proprietà è impostata su 0 quando viene generato un errore, non viene visualizzata la traccia dello stack. Se la proprietà è impostata su un valore negativo o un valore non numerico, il valore viene convertito in 0. Se il stackTraceLimit è impostata su `Infinity`, viene visualizzato l'intero stack. In caso contrario, `ToUint32` viene usata per convertire il valore.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come impostare e ottenere il limite di traccia dello stack.  
  
```JavaScript  
try  
    {  
    var err = new Error("my error");  
    Error.stackTraceLimit = 7;  
    throw err;  
    }  
catch(e)  
    {  
    document.write ("Error stack trace limit: ")  
    document.write (Error.stackTraceLimit);  
    }  
```  
  
## <a name="requirements"></a>Requisiti  
 Supportato in Internet Explorer 10 e in [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] app.  
  
 **Si applica a**: [oggetto Error](../../javascript/reference/error-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà Description (Error)](../../javascript/reference/description-property-error-javascript.md)   
 [Proprietà Message (Error)](../../javascript/reference/message-property-error-javascript.md)   
 [Proprietà Name (Error)](../../javascript/reference/name-property-error-javascript.md)   
 [Proprietà stack (Error)](../../javascript/reference/stack-property-error-javascript.md)