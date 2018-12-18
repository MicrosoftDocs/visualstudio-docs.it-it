---
title: "Proprietà stack (Error) (JavaScript) | Documenti Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Error.stack
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- JavaScript error stack
- error stack [JavaScript]
ms.assetid: 1dc21fdd-853c-4664-bf1c-24eb1f6f2daf
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 14e4a2537b1543b7e8d9727afdeb8ea5dee61bbc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="stack-property-error-javascript"></a>Proprietà stack (Error) (JavaScript)
Ottiene o imposta lo stack degli errori come una stringa contenente i frame di traccia dello stack.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
object  
.stack   
```  
  
## <a name="remarks"></a>Note  
 La proprietà `stack` è impostata su `undefined` quando l’errore viene costruito e ottiene le informazioni di traccia quando l'errore viene generato. Se un errore viene generato più volte, la proprietà `stack` viene aggiornata ogni volta che viene generato l'errore.  
  
 Stack frame vengono visualizzati nel formato seguente: **in FunctionName (\<nome/URL completo >:\<numero riga >:\<numero di colonna >)**  
  
 Se si crea un oggetto Error personalizzato e si imposta la traccia dello stack su un valore, il valore non verrà sovrascritto quando viene generato l'errore.  
  
 La proprietà `stack` non visualizza funzioni inline nei relativi frame. Visualizza solo lo stack fisico.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come ottenere lo stack quando viene intercettato un errore.  
  
```JavaScript  
try  
    {  
        var x = y.name;  
    }  
catch(e)  
    {  
        document.write ("Error stack: ")  
        document.write (e.stack);  
    }  
```  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come impostare e ottenere lo stack.  
  
```JavaScript  
try  
    {  
        var err = Error("my error");  
        err.stack = "my stack trace";  
        throw err;  
    }  
catch(e)  
    {  
        document.write ("Error stack: ")  
        document.write (e.stack);  
    }  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]  
  
 **Si applica a**: [oggetto Error](../../javascript/reference/error-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà Description (Error)](../../javascript/reference/description-property-error-javascript.md)   
 [Proprietà Message (Error)](../../javascript/reference/message-property-error-javascript.md)   
 [Proprietà Name (Error)](../../javascript/reference/name-property-error-javascript.md)   
 [Proprietà stackTraceLimit (Error)](../../javascript/reference/stacktracelimit-property-error-javascript.md)