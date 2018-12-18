---
title: '@cc_onIstruzione (JavaScript) | Documenti Microsoft'
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
- '@cc_on_JavaScriptKeyword'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- conditional compilation, activating
- '@cc_on statement'
- '@set statement'
- '@if statement'
ms.assetid: fdeda7ee-b9f4-4e52-8aa2-21c90c02a332
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d7e993d5bc8302931a5722495da70612e79f7dfd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="ccon-statement-javascript"></a>@cc_onIstruzione (JavaScript)
Attiva il supporto della compilazione condizionale all'interno di commenti in uno script.  
  
> [!WARNING]
>  La compilazione condizionale non è supportata nella modalità standard di Internet Explorer 11 e nelle applicazioni [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]. La compilazione condizionale è supportata nella modalità standard di Internet Explorer 10 e in tutte le versioni precedenti.  
  
## <a name="syntax"></a>Sintassi  
  
```  
@cc_on   
```  
  
## <a name="remarks"></a>Note  
 L'istruzione `@cc_on` può attivare la compilazione condizionale all'interno di commenti in uno script.  
  
 È invece infrequente l'utilizzo delle variabili di compilazione condizionale in script creati per pagine ASP o ASP.NET o per programmi per la riga di comando, in quanto le funzionalità dei compilatori possono essere determinate mediante metodi diversi.  
  
 Quando si scrive uno script per una pagina Web, inserire sempre il codice di compilazione condizionale nei commenti. In questo modo gli host che non supportano la compilazione condizionale potranno ignorarlo.  
  
 Si consiglia di utilizzare l'istruzione `@cc_on` in un commento, in modo che i browser che non supportano la compilazione condizionale accettino lo script come sintassi valida:  
  
 La compilazione condizionale viene attivata anche da un'istruzione `@if` o `@set` esterna a un commento.  
  
## <a name="example"></a>Esempio  
 Nel codice seguente viene illustrato l'utilizzo dell'istruzione `@cc_on`.  
  
```JavaScript  
/*@cc_on @*/  
/*@  
    document.write("JavaScript version: " + @_jscript_version + ".");  
    document.write("<br />");  
    @if (@_win32)  
        document.write("Running on the 32-bit version of Windows.");  
    @elif (@_win16)  
        document.write("Running on the 16-bit version of Windows.");  
    @else  
        document.write("Running on a different operating system.");  
    @end  
@*/  
```  
  
## <a name="requirements"></a>Requisiti  
 Supportato in tutte le versioni di Internet Explorer, ma non nelle applicazioni [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Compilazione condizionale](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Variabili di compilazione condizionale](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@ifIstruzione](../../javascript/reference/at-if-statement-javascript.md)   
 [Istruzione @set](../../javascript/reference/at-set-statement-javascript.md)