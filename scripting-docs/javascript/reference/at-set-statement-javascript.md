---
title: '@setIstruzione (JavaScript) | Documenti Microsoft'
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '@set_JavaScriptKeyword'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '@set statement'
- conditional compilation, variables
ms.assetid: 36f15926-3e69-422d-82a2-d186dc088203
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 10f74a1d57a61d78897b660812a6fd8078244b6b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="set-statement-javascript"></a>@setIstruzione (JavaScript)
Crea le variabili usate con le istruzioni di compilazione condizionale.  
  
> [!WARNING]
>  La compilazione condizionale non è supportata nella modalità standard di Internet Explorer 11 e nelle applicazioni [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]. La compilazione condizionale è supportata nella modalità standard di Internet Explorer 10 e in tutte le versioni precedenti.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
@set @varname = term   
```  
  
## <a name="parameters"></a>Parametri  
 *VarName*  
 Obbligatorio. Nome di variabile [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] valido. Deve essere sempre preceduto dal carattere "@".  
  
 `term`  
 Obbligatorio. Zero o più operatori unari seguiti da una costante, una variabile di compilazione condizionale o un'espressione tra parentesi.  
  
## <a name="remarks"></a>Note  
 Per la compilazione condizionale sono supportate variabili numeriche e booleane, ma non variabili stringa. Le variabili create tramite l'istruzione `@set` vengono in genere utilizzate in istruzioni di compilazione condizionale, ma possono essere utilizzate in qualsiasi punto del codice [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
 Di seguito sono riportati alcuni esempi di dichiarazioni di variabili:  
  
```JavaScript  
  
      @set @myvar1 = 12  
  
@set @myvar2 = (@myvar1 * 20)  
  
@set @myvar3 = @_jscript_version  
```  
  
 Nelle espressioni tra parentesi sono supportati i seguenti operatori:  
  
-   `! ~`  
  
-   `* / %`  
  
-   `+ -`  
  
-   `<< >> >>>`  
  
-   `< <= > >=`  
  
-   `== != === !==`  
  
-   `& ^ |`  
  
-   `&& | |`  
  
 Se si utilizza una variabile prima di averla definita, il relativo valore sarà `NaN`. Per verificare la presenza di valori `NaN` è possibile utilizzare l'istruzione `@if`:  
  
```JavaScript  
@if (@newVar != @newVar)  
   ...  
```  
  
 Questo procedimento funziona perché `NaN` è l'unico valore che non risulta mai uguale a se stesso.  
  
## <a name="requirements"></a>Requisiti  
 Supportato in tutte le versioni di Internet Explorer, ma non nelle applicazioni [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Compilazione condizionale](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Variabili di compilazione condizionale](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@cc_onIstruzione](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [Istruzione @if](../../javascript/reference/at-if-statement-javascript.md)