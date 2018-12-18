---
title: Errori di sintassi JavaScript | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: JavaScript
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- errors [JavaScript]
- syntax errors, JavaScript
ms.assetid: 0343dc19-5f5e-4a4c-83da-630b4fbcb3b6
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3bc3398d6a90ef308fd2b4b367bc1006ad95f5b1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="javascript-syntax-errors"></a>Errori di sintassi JavaScript
[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]si verificano errori di sintassi quando la struttura di uno del [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] istruzioni viola uno o più regole sintattiche.  
  
## <a name="errors"></a>Errori  
  
|Numero errore|Descrizione|  
|------------------|-----------------|  
|1019|[Impossibile utilizzare 'break' all'esterno del ciclo](../../javascript/misc/can-t-have-break-outside-of-loop.md)|  
|1020|[Impossibile utilizzare 'continue' all'esterno del ciclo](../../javascript/misc/can-t-have-continue-outside-of-loop.md)|  
|1030|[Compilazione condizionale disattivata](../../javascript/misc/conditional-compilation-is-turned-off.md)|  
|1027|['default' può essere utilizzato una sola volta in un'istruzione 'switch'](../../javascript/misc/default-can-only-appear-once-in-a-switch-statement.md)|  
|1005|[Previsto ' ('](../../javascript/misc/expected-left-parenthesis-javascript.md)|  
|1006|[Previsto ')'](../../javascript/misc/expected-right-parenthesis-javascript.md)|  
|1012|[Previsto '/'](../../javascript/misc/expected-minus.md)|  
|1003|[Previsto ':'](../../javascript/misc/expected-colon.md)|  
|1004|[Previsto ';'](../../javascript/misc/expected-semicolon.md)|  
|1032|[Previsto '@'](../../javascript/misc/expected-at.md)|  
|1029|[Previsto '@end'](../../javascript/misc/expected-at-end.md)|  
|1007|[Previsto ' &#93;'](../../javascript/misc/expected-right-square-bracket.md)|  
|1008|[Previsto '{'](../../javascript/misc/expected-left-curly-brace.md)|  
|1009|[Previsto '}'](../../javascript/misc/expected-right-curly-brace.md)|  
|1011|[Previsto '='](../../javascript/misc/expected-equal-javascript.md)|  
|1040|[Previsto 'catch'](../../javascript/misc/expected-catch.md)|  
|1031|[Prevista costante](../../javascript/misc/expected-constant.md)|  
|1023|[Prevista cifra esadecimale](../../javascript/misc/expected-hexadecimal-digit.md)|  
|1010|[Previsto identificatore](../../javascript/misc/expected-identifier-javascript.md)|  
|1028|[Previsto identificatore, stringa o numero](../../javascript/misc/expected-identifier-string-or-number.md)|  
|1024|[Previsto 'while'](../../javascript/misc/expected-while.md)|  
|1014|[Carattere non valido](../../javascript/misc/invalid-character-javascript.md)|  
|1026|[Impossibile trovare l'etichetta](../../javascript/misc/label-not-found.md)|  
|1025|[Etichetta ridefinita](../../javascript/misc/label-redefined.md)|  
|1018|[Istruzione 'return' esterna alla funzione](../../javascript/misc/return-statement-outside-of-function.md)|  
|1002|[Errore di sintassi](../../javascript/misc/syntax-error-javascript.md)|  
|1035|[La parola chiave 'throw' deve essere seguita da un'espressione nella stessa riga di codice sorgente](../../javascript/misc/throw-must-be-followed-by-an-expression-on-the-same-source-line.md)|  
|1016|[Commento non completo](../../javascript/misc/unterminated-comment.md)|  
|1015|[Costante stringa senza terminazione](../../javascript/misc/unterminated-string-constant-javascript.md)|  
  
### <a name="script-host-errors"></a>Errori di script Host  
 I seguenti errori parla correttamente gli errori relativi all'host di script, ma può vedere occasionalmente.  
  
|Errore|HRESULT|Descrizione|  
|-----------|-------------|-----------------|  
|SCRIPT_E_RECORDED|0x86664004|Per passare tra host e il motore di script è stato registrato un errore. L'host deve passare il codice di errore al chiamante.|  
|SCRIPT_E_REPORTED|0x80020101|Motore di script ha rilevato un'eccezione non gestita nell'host tramite IActiveScriptSite::OnScriptError. Host è possibile ignorare questo errore.|  
|SCRIPT_E_PROPAGATE|0x8002010|Un errore di script viene propagato al chiamante che potrebbe essere in un altro thread. L'host deve passare il codice di errore al chiamante.|  
  
## <a name="see-also"></a>Vedere anche  
 [Errori di runtime JavaScript](../../javascript/reference/javascript-run-time-errors.md)