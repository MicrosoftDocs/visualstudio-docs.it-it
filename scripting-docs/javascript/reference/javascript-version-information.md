---
title: Informazioni sulla versione JavaScript | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- JavaScript, version information
ms.assetid: 440f4924-f7a9-48e0-873e-bd599a93b437
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3a2335c3697be9ef3e2d674ac37047ddd3de242d
ms.sourcegitcommit: 873c0e1a31def013bcca1b0caa0eb0249de89bec
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2018
---
# <a name="javascript-version-information"></a>Informazioni sulla versione JavaScript
Versioni diverse di JavaScript supportano set di elementi JavaScript differenti. Le applicazioni[!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] supportano un set di funzionalità di Internet Explorer leggermente diverso.  
  
> [!IMPORTANT]
>  Un'app di [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] è un nuovo tipo di applicazione eseguibile sui dispositivi [!INCLUDE[win8](../../javascript/includes/win8-md.md)] . Per altre informazioni sulle app [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] , vedere [What's a Windows Store app?](http://msdn.microsoft.com/en-us/231c1fba-9f87-468e-94aa-45dd57edcc70)  
  
 La modalità standard, ovvero la modalità usata in tutte le versioni di Internet Explorer fino alla versione 11 quando esiste una direttiva `<!doctype>` , supporta un set di elementi diverso dalla modalità non standard, ovvero la modalità usata quando non esiste alcuna direttiva `<!doctype>` . Per altre informazioni sul controllo delle versioni, vedere l'articolo relativo alla [definizione della compatibilità del documento](http://go.microsoft.com/fwlink/?LinkId=208537).  
  
 La tabella seguente mostra le modalità documento di Internet Explorer (e le app che rappresentano [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] e [!INCLUDE[winphone_appname](../../javascript/reference/includes/winphone-appname-md.md)]) che supportano elementi del linguaggio specifici. Le modalità documento che supportano un determinato elemento sono indicate con la lettera **Y**, mentre quelle che non supportano un determinato elemento sono indicate con la lettera **N**.  
  
> [!IMPORTANT]
>  [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)] (Browser edge in Windows 10) non include il supporto per le modalità documento legacy. Il supporto per le app di [!INCLUDE[winphone_appname](../../javascript/reference/includes/winphone-appname-md.md)] inizierà con Windows Phone 8.1. Le funzionalità sperimentali (su: flag) sono indicate con "Exp".  
  
 La tabella include informazioni di riepilogo. Per altre informazioni, vedere la documentazione relativa all'elemento del linguaggio.  
  
|Elemento di linguaggio|Modalità non standard, modalità standard di Internet Explorer 6, modalità standard di Internet Explorer 7|Modalità standard di Internet Explorer 8|Modalità standard di Internet Explorer 9|Modalità standard di Internet Explorer 10|Modalità standard di Internet Explorer 11|Microsoft Edge|Applicazioni Windows Store|  
|----------------------|--------------------------------------------------------------------------|-----------------------------------|-----------------------------------|------------------------------------|------------------------------------|----------|----------------|  
|[__proto\_ \_ proprietà (oggetto)](../../javascript/reference/proto-property-object-javascript.md)|N|N|N|N|Y|Y|v8 (Win): N<br />v8.1 (Win): Y<br />v8.1 (Phone): Y|  
|[Proprietà $1...$9 (RegExp)](../../javascript/reference/dollar-1-dot-dot-dot-dollar-9-properties-regexp-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Proprietà 0n](../../javascript/reference/0-dot-dot-dot-n-properties-arguments-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Funzione abs](../../javascript/reference/math-abs-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Funzione acos](../../javascript/reference/math-acos-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Funzione acosh](../../javascript/reference/math-acosh-function-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[Oggetto ActiveXObject](../../javascript/reference/activexobject-object-javascript.md)|Y|Y|Y|Y|Y|Y|N|  
|[Operatore di assegnazione di addizione (+=)](../../javascript/reference/addition-assignment-operator-decrement-equal-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Operatore addizione (+)](../../javascript/reference/addition-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo apply](../../javascript/reference/apply-method-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Oggetto arguments](../../javascript/reference/arguments-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Proprietà arguments](../../javascript/reference/arguments-property-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Oggetto Array](../../javascript/reference/array-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Funzione Array.from (Array)](../../javascript/reference/array-from-function-array-javascript.md)|N|N|N|N|N|N|v8.1: N<br />v10: Y|  
|[Funzione Array.isArray](../../javascript/reference/array-isarray-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Funzione Array.of (Array)](../../javascript/reference/array-of-function-array-javascript.md)|N|N|N|N|N|N|v8.1: N<br />v10: Y|  
|[Oggetto ArrayBuffer](../../javascript/reference/arraybuffer-object.md)|N|N|N|Y|Y|Y|Y|  
|[Funzioni](../../javascript/functions-javascript.md)|N|N|N|N|N|N|v8.1: N<br />v10: Y|  
|[Funzione asin](../../javascript/reference/math-asin-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Funzione Object.assign (Object)](../../javascript/reference/object-assign-function-object-javascript.md)|N|N|N|N|N|N|v8.1: N<br />v10: Y|  
|[Operatore di assegnazione (=)](../../javascript/reference/assignment-operator-decrement-equal-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Funzione atan](../../javascript/reference/math-atan-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Funzione atan2](../../javascript/reference/math-atan2-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo atEnd](../../javascript/reference/atend-method-enumerator-javascript.md)|Y|Y|Y|Y|Y|Y|N|  
|[Metodo bind](../../javascript/reference/bind-method-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Operatore di assegnazione AND bit per bit (&=)](../../javascript/reference/bitwise-and-assignment-operator-decrement-equal-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Operatore AND bit per bit (&)](../../javascript/reference/bitwise-and-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Bit per bit operatore Left Shift (<\<)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Operatore NOT bit per bit (~)](../../javascript/reference/bitwise-not-operator-decrement-tilde-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Bit per bit o operatore di assegnazione (&#124; =)](../../javascript/reference/bitwise-or-assignment-operator-decrement-equal-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[OR bit per bit (operatore) (&#124;)](../../javascript/reference/bitwise-or-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Operatore Right Shift bit per bit (>>)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Operatore di assegnazione YOR bit per bit (^=)](../../javascript/reference/bitwise-xor-assignment-operator-decrement-hat-equal-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Operatore YOR bit per bit (^)](../../javascript/reference/bitwise-xor-operator-decrement-hat-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo blink](../../javascript/reference/html-tag-methods-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo bold](../../javascript/reference/html-tag-methods-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Oggetto Boolean](../../javascript/reference/boolean-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Istruzione break](../../javascript/reference/break-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo call](../../javascript/reference/call-method-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Proprietà callee](../../javascript/reference/callee-property-arguments-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Proprietà caller](../../javascript/reference/caller-property-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Istruzione catch](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Funzione ceil](../../javascript/reference/math-ceil-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo charAt](../../javascript/reference/charat-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo charCodeAt](../../javascript/reference/charcodeat-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Istruzione class](../../javascript/reference/class-statement-javascript.md)|N|N|N|N|N|Exp.|v8.1: N<br />v10: Exp.|  
|[Metodo codePointAt (String)](../../javascript/reference/codepointat-method-string-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[Operatore virgola (,)](../../javascript/reference/comma-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[// (Istruzione per commento a riga singola)](../../javascript/reference/comment-statements-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[/*.. \*/ (Istruzione per commento su più righe)](../../javascript/reference/comment-statements-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Operatori di confronto](../../javascript/reference/comparison-operators-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo compile](../../javascript/reference/compile-method-regular-expression-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo concat (Array)](../../javascript/reference/concat-method-array-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo concat (String)](../../javascript/reference/concat-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Compilazione condizionale](../../javascript/advanced/conditional-compilation-javascript.md)|Y|Y|Y|Y|N|N|N|  
|[Variabili di compilazione condizionale](../../javascript/advanced/conditional-compilation-variables-javascript.md)|Y|Y|Y|Y|N|N|N|  
|[Operatore condizionale ternario (?:)](../../javascript/reference/conditional-ternary-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Proprietà constructor](../../javascript/reference/constructor-property-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Istruzione const](../../javascript/reference/const-statement-javascript.md)|N|N|N|N|Y|Y|v8 (Win): N<br />v8.1 (Win): Y<br />v8.1 (Phone): Y|  
|[Istruzione continue](../../javascript/reference/continue-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Funzione cos](../../javascript/reference/math-cos-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Funzione create](../../javascript/reference/object-create-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Oggetto DataView](../../javascript/reference/dataview-object.md)|N|N|N|Y|Y|Y|Y|  
|[Oggetto Date](../../javascript/reference/date-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Oggetto Debug](../../javascript/reference/debug-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Proprietà Debug.setNonUserCodeExceptions](../../javascript/reference/debug-setnonusercodeexceptions-property.md)|N|N|N|Y|Y|Y|Y|  
|[Proprietà Debug.setNonUserCodeExceptions](../../javascript/reference/debug-setnonusercodeexceptions-property.md)|N|N|N|Y|Y|Y|Y|  
|[Istruzione debugger](../../javascript/reference/debugger-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Funzione decodeURI](../../javascript/reference/decodeuri-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Funzione DecodeURIComponent](../../javascript/reference/decodeuricomponent-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Operatore di decremento (--)](../../javascript/reference/increment-and-decrement-operators-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Funzioni](../../javascript/functions-javascript.md)|N|N|N|N|N|Exp.|v8.1: N<br />v10: Exp.|  
|[Funzione defineProperties](../../javascript/reference/object-defineproperties-function-javascript.md)|N|Y*|Y|Y|Y|Y|Y|  
|[Funzione defineProperty](../../javascript/reference/object-defineproperty-function-javascript.md)|N|Y*|Y|Y|Y|Y|Y|  
|[Operatore delete](../../javascript/reference/delete-operator-decrementjavascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Proprietà description](../../javascript/reference/description-property-error-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo dimensions](../../javascript/reference/dimensions-method-vbarray-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Operatore di assegnazione di divisione (/=)](../../javascript/reference/division-assignment-operator-decrement-equal-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Operatore di divisione (/)](../../javascript/reference/division-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Istruzione do...while](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Costante E](../../javascript/reference/math-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Funzione encodeURI](../../javascript/reference/encodeuri-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Funzione encodeURI Component](../../javascript/reference/encodeuricomponent-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo entries (Array)](../../javascript/reference/entries-method-array-javascript.md)|N|N|N|N|N|N|v8.1: N<br />v10: Y|  
|[Oggetto Enumerator](../../javascript/reference/enumerator-object-javascript.md)|Y|Y|Y|Y|Y|Y|N|  
|[Costanti Number](../../javascript/reference/number-constants-javascript.md)|N|N|N|N|N|N|v8.1: N<br />v10: Y|  
|[Operatore di uguaglianza (==)](../../javascript/reference/comparison-operators-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Oggetto Error](../../javascript/reference/error-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Proprietà stack (Error)](../../javascript/reference/stack-property-error-javascript.md)|N|N|N|Y|Y|Y|Y|  
|[Proprietà stackTraceLimit (Error)](../../javascript/reference/stacktracelimit-property-error-javascript.md)|N|N|N|Y|Y|Y|Y|  
|[Funzione escape](../../javascript/reference/escape-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Funzione eval](../../javascript/reference/eval-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo exec](../../javascript/reference/exec-method-regular-expression-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo every](../../javascript/reference/every-method-array-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Funzione exp](../../javascript/reference/math-exp-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo fill (Array)](../../javascript/reference/fill-method-array-javascript.md)|N|N|N|N|N|N|v8.1: N<br />v10: Y|  
|[Metodo filter](../../javascript/reference/filter-method-array-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Istruzione finally](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo findIndex (Array)](../../javascript/reference/findindex-method-array-javascript.md)|N|N|N|N|N|N|v8.1: N<br />v10: Y|  
|[Metodo fixed](../../javascript/reference/html-tag-methods-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Oggetto Float32Array](../../javascript/reference/float32array-object.md)|N|N|N|Y|Y|Y|Y|  
|[Oggetto Float64Array](../../javascript/reference/float64array-object.md)|N|N|N|Y|Y|Y|Y|  
|[Funzione floor](../../javascript/reference/math-floor-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo fontcolor](../../javascript/reference/html-tag-methods-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo fontsize](../../javascript/reference/html-tag-methods-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Istruzione for](../../javascript/reference/for-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo forEach](../../javascript/reference/foreach-method-array-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Istruzione for...in](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Istruzione for...of](../../javascript/reference/for-dot-dot-dot-of-statement-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[Funzione freeze](../../javascript/reference/object-freeze-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Funzione fromCharCode](../../javascript/reference/string-fromcharcode-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Funzione fromCodePoint](../../javascript/reference/string-fromcodepoint-function-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[Oggetto Function](../../javascript/reference/function-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Istruzione function](../../javascript/reference/function-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Generatori](../../javascript/advanced/iterators-and-generators-javascript.md)|N|N|N|N|N|Exp.|v8.1: N<br />v10: Exp.|  
|[Metodo getDate](../../javascript/reference/getdate-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo getDay](../../javascript/reference/getday-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo getFullYear](../../javascript/reference/getfullyear-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo getHours](../../javascript/reference/gethours-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo getItem](../../javascript/reference/getitem-method-vbarray-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo getMilliseconds](../../javascript/reference/getmilliseconds-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo getMinutes](../../javascript/reference/getminutes-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo getMonth](../../javascript/reference/getmonth-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Funzione GetObject](../../javascript/reference/getobject-function-javascript.md)|Y|Y|N|N|N|N|N|  
|[Funzione getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)|N|Y*|Y|Y|Y|Y|Y|  
|[Funzione getOwnPropertyNames](../../javascript/reference/object-getownpropertynames-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Funzione getPrototypeOf](../../javascript/reference/object-getprototypeof-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Metodo getSeconds](../../javascript/reference/getseconds-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo getTime](../../javascript/reference/gettime-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo getTimezoneOffset](../../javascript/reference/gettimezoneoffset-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo getUTCDate](../../javascript/reference/getutcdate-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo getUTCDay](../../javascript/reference/getutcday-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo getUTCFullYear](../../javascript/reference/getutcfullyear-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo getUTCHours](../../javascript/reference/getutchours-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo getUTCMilliseconds](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo getUTCMinutes](../../javascript/reference/getutcminutes-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo getUTCMonth](../../javascript/reference/getutcmonth-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo getUTCSeconds](../../javascript/reference/getutcseconds-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo getVarDate](../../javascript/reference/getvardate-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|N|  
|[Metodo getYear](../../javascript/reference/getyear-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Oggetto Global](../../javascript/reference/global-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Proprietà global](../../javascript/reference/global-property-regular-expression-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Operatore maggiore di (>)](../../javascript/reference/comparison-operators-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Operatore maggiore o uguale a (>=)](../../javascript/reference/comparison-operators-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo hasOwnProperty](../../javascript/reference/hasownproperty-method-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodi tag HTML](../../javascript/reference/html-tag-methods-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Funzione hypot](../../javascript/reference/math-hypot-function-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[Operatore di identità (===)](../../javascript/reference/comparison-operators-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Istruzione if...else](../../javascript/reference/if-dot-dot-dot-else-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Proprietà ignoreCase](../../javascript/reference/ignorecase-property-regular-expression-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Funzione imul](../../javascript/reference/math-imul-function-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[Operatore In](../../javascript/reference/in-operator-decrementjavascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo includes (String)](../../javascript/reference/includes-method-string-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[Operatore di incremento (++)](../../javascript/reference/increment-and-decrement-operators-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Proprietà index](../../javascript/reference/index-property-regexp-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo indexOf (Array)](../../javascript/reference/indexof-method-array-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Metodo indexOf (String)](../../javascript/reference/indexof-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Operatore di disuguaglianza (!=)](../../javascript/reference/comparison-operators-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Costante Infinity](../../javascript/reference/infinity-constant-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Proprietà input ($_)](../../javascript/reference/input-property-dollar-regexp-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Operatore instanceof](../../javascript/reference/instanceof-operator-decrementjavascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Oggetto Int8Array](../../javascript/reference/int8array-object.md)|N|N|N|Y|Y|Y|Y|  
|[Oggetto Int16Array](../../javascript/reference/int16array-object.md)|N|N|N|Y|Y|Y|Y|  
|[Oggetto Int32Array](../../javascript/reference/int32array-object.md)|N|N|N|Y|Y|Y|Y|  
|[Oggetto Intl.Collator](../../javascript/reference/intl-collator-object-javascript.md)|N|N|N|N|Y|Y|v8 (Win): N<br />v8.1 (Win): Y<br />v8.1 (Phone): Y|  
|[Oggetto Intl.DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md)|N|N|N|N|Y|Y|v8: N<br />v8.1: Y|  
|[Oggetto Intl.NumberFormat](../../javascript/reference/intl-numberformat-object-javascript.md)|N|N|N|N|Y|Y|v8: N<br />v8.1: Y|  
|[Funzione isFinite](../../javascript/reference/isfinite-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Funzione isArray](../../javascript/reference/array-isarray-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Funzione IsExtensible](../../javascript/reference/object-isextensible-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Funzione isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[isInteger Function](../../javascript/reference/number-isinteger-function-number-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[Funzione isNaN](../../javascript/reference/isnan-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Funzione isNaN (Number)](../../javascript/reference/number-isnan-function-number-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[Formato di data ISO](../../javascript/date-and-time-strings-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Metodo IsPrototypeOf](../../javascript/reference/isprototypeof-method-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Funzione isSealed](../../javascript/reference/object-issealed-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Metodo italics](../../javascript/reference/html-tag-methods-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Iteratori](../../javascript/advanced/iterators-and-generators-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[Metodo item](../../javascript/reference/item-method-enumerator-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo join](../../javascript/reference/join-method-array-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Oggetto JSON](../../javascript/reference/json-object-javascript.md)|N|Y|Y|Y|Y|Y|Y|  
|[Funzione keys](../../javascript/reference/object-keys-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Metodo keys (Array)](../../javascript/reference/keys-method-array-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[Istruzione con etichetta](../../javascript/reference/labeled-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Proprietà lastIndex](../../javascript/reference/lastindex-property-regexp-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo lastIndexOf (Array)](../../javascript/reference/lastindexof-method-array-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Metodo lastIndexOf (String)](../../javascript/reference/lastindexof-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Proprietà lastMatch ($&)](../../javascript/reference/lastmatch-property-dollar-regexp-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Proprietà lastParen ($+)](../../javascript/reference/lastparen-property-dollar-regexp-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo lbound](../../javascript/reference/lbound-method-vbarray-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Proprietà leftContext ($')](../../javascript/reference/leftcontext-property-dollar-grave-regexp-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Operatore di assegnazione Left Shift (<<=)](../../javascript/reference/left-shift-assignment-operator-decrement-equal-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Proprietà length (Arguments)](../../javascript/reference/length-property-arguments-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Proprietà length (Array)](../../javascript/reference/length-property-array-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Proprietà length (Function)](../../javascript/reference/length-property-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Proprietà length (String)](../../javascript/reference/length-property-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Operatore minore di (<)](../../javascript/reference/comparison-operators-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Operatore minore o uguale a (<=)](../../javascript/reference/comparison-operators-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Istruzione let](../../javascript/reference/let-statement-javascript.md)|N|N|N|N|Y|Y|v8: N<br />v8.1: Y|  
|[Metodo link](../../javascript/reference/html-tag-methods-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Costante LN2](../../javascript/reference/math-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Costante LN10](../../javascript/reference/math-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo localeCompare](../../javascript/reference/localecompare-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Funzione log](../../javascript/reference/math-log-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Costante LOG2E](../../javascript/reference/math-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Costante LOG10E](../../javascript/reference/math-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Operatore AND logico (&&)](../../javascript/reference/logical-and-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Operatore NOT logico (!)](../../javascript/reference/logical-not-operator-decrement-exclpt-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Operatore logico OR (operatore) (&#124; &#124;)](../../javascript/reference/logical-or-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo map](../../javascript/reference/map-method-array-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Oggetto Map](../../javascript/reference/map-object-javascript.md)|N|N|N|N|Y|Y|v8: N<br />v8.1: Y|  
|[Metodo match](../../javascript/reference/match-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Oggetto Math](../../javascript/reference/math-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Funzione max](../../javascript/reference/math-max-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Costante MAX_VALUE](../../javascript/reference/number-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Proprietà message](../../javascript/reference/message-property-error-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Funzione min](../../javascript/reference/math-min-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Costante MIN_VALUE](../../javascript/reference/number-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Operatore di assegnazione di resto (% =)](../../javascript/reference/modulus-assignment-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Operatore di resto (%)](../../javascript/reference/modulus-operator-decrementjavascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo moveFirst](../../javascript/reference/movefirst-method-enumerator-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo moveNext](../../javascript/reference/movenext-method-enumerator-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Proprietà multiline](../../javascript/reference/multiline-property-regular-expression-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Operatore di assegnazione di moltiplicazione (*=)](../../javascript/reference/multiplication-assignment-operator-decrement-equal-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Operatore di moltiplicazione (*)](../../javascript/reference/multiplication-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Proprietà name](../../javascript/reference/name-property-error-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Costante NaN (Global)](../../javascript/reference/nan-constant-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Costante NaN (Number)](../../javascript/reference/number-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Costante NEGATIVE_INFINITY](../../javascript/reference/number-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Operatore new](../../javascript/reference/new-operator-decrementjavascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Operatore di non identità (!==)](../../javascript/reference/comparison-operators-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Funzione now](../../javascript/reference/date-now-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Oggetto Number](../../javascript/reference/number-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Proprietà number](../../javascript/reference/number-property-error-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Oggetto Object](../../javascript/reference/object-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Precedenza tra gli operatori](../../javascript/operator-subtractprecedence-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Funzione Date.parse](../../javascript/reference/date-parse-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Funzione JSON.parse](../../javascript/reference/json-parse-function-javascript.md)|N|Y|Y|Y|Y|Y|Y|  
|[Funzione parseFloat](../../javascript/reference/parsefloat-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Funzione parseInt](../../javascript/reference/parseint-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Costante PI](../../javascript/reference/math-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo pop](../../javascript/reference/pop-method-array-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Costante POSITIVE_INFINITY](../../javascript/reference/number-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Funzione pow](../../javascript/reference/math-pow-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Funzione preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Oggetto Promise](../../javascript/reference/promise-object-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[Proprietà prototype](../../javascript/reference/prototype-property-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo propertyIsEnumerable](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Oggetto Proxy](../../javascript/reference/proxy-object-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[Metodo push](../../javascript/reference/push-method-array-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Funzione random](../../javascript/reference/math-random-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Funzione raw](../../javascript/reference/string-raw-function-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[Metodo reduce](../../javascript/reference/reduce-method-array-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Metodo reduceRight](../../javascript/reference/reduceright-method-array-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Oggetto RegExp](../../javascript/reference/regexp-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Oggetto Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Sintassi delle espressioni regolari](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)|Y|Y|Y|Y|Y|Y|Y|  
|[Flag /y di espressione regolare](../../javascript/reference/regular-expression-object-javascript.md)|N|N|N|N|N|Exp.|v8.1: N<br />v10: Exp.|  
|[Metodo repeat (String)](../../javascript/reference/repeat-method-string-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[Metodo replace](../../javascript/reference/replace-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Funzioni](../../javascript/functions-javascript.md)|N|N|N|N|N|N|v8.1: N<br />v10: Y|  
|[Istruzione return](../../javascript/reference/return-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo reverse](../../javascript/reference/reverse-method-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Proprietà rightContext ($')](../../javascript/reference/rightcontext-property-dollar-regexp-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Operatore di assegnazione Right Shift (>>=)](../../javascript/reference/right-shift-assignment-operator-decrement-equal-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Funzione round](../../javascript/reference/math-round-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Funzione ScriptEngine](../../javascript/reference/scriptengine-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Funzione ScriptEngineBuildVersion](../../javascript/reference/scriptenginebuildversion-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Funzione ScriptEngineMajorVersion](../../javascript/reference/scriptenginemajorversion-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Funzione ScriptEngineMinorVersion](../../javascript/reference/scriptengineminorversion-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Funzione seal](../../javascript/reference/object-seal-function-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Metodo search](../../javascript/reference/search-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Oggetto Set](../../javascript/reference/set-object-javascript.md)|N|N|N|N|Y|Y|v8: N<br />v8.1: Y|  
|[Metodo setDate](../../javascript/reference/setdate-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo setFullYear](../../javascript/reference/setfullyear-method-date-javascript.md)||Y|Y|Y|Y|Y|Y|  
|[Metodo setHours](../../javascript/reference/sethours-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo setMilliseconds](../../javascript/reference/setmilliseconds-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo setMinutes](../../javascript/reference/setminutes-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo setMonth](../../javascript/reference/setmonth-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo setSeconds](../../javascript/reference/setseconds-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo setTime](../../javascript/reference/settime-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo setUTCDate](../../javascript/reference/setutcdate-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo setUTCFullYear](../../javascript/reference/setutcfullyear-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo setUTCHours](../../javascript/reference/setutchours-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo setUTCMilliseconds](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo setUTCMinutes](../../javascript/reference/setutcminutes-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo setUTCMonth](../../javascript/reference/setutcmonth-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo setUTCSeconds](../../javascript/reference/setutcseconds-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo setYear](../../javascript/reference/setyear-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo shift](../../javascript/reference/shift-method-array-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Funzione sin](../../javascript/reference/math-sin-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo slice (Array)](../../javascript/reference/slice-method-array-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo slice (String)](../../javascript/reference/slice-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo small](../../javascript/reference/html-tag-methods-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo some](../../javascript/reference/some-method-array-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Metodo sort](../../javascript/reference/sort-method-array-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Proprietà source](../../javascript/reference/source-property-regular-expression-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo splice](../../javascript/reference/splice-method-array-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo split](../../javascript/reference/split-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Funzioni](../../javascript/functions-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[Funzione sqrt](../../javascript/reference/math-sqrt-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Costante SQRT1_2](../../javascript/reference/math-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Costante SQRT2](../../javascript/reference/math-constants-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Direttiva use strict](../../javascript/reference/use-strict-directive.md)|N|N|N|Y|Y|Y|Y|  
|[Metodo strike](../../javascript/reference/html-tag-methods-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Oggetto String](../../javascript/reference/string-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Funzione JSON.stringify](../../javascript/reference/json-stringify-function-javascript.md)|N|Y|Y|Y|Y|Y|Y|  
|[Metodo sub](../../javascript/reference/html-tag-methods-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo substr](../../javascript/reference/substr-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo substring](../../javascript/reference/substring-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Operatore di assegnazione di sottrazione (-=)](../../javascript/reference/subtraction-assignment-operator-decrement-equal-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Operatore di sottrazione (-)](../../javascript/reference/subtraction-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo sup](../../javascript/reference/html-tag-methods-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Istruzione switch](../../javascript/reference/switch-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Oggetto Symbol](../../javascript/reference/symbol-object-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[Funzione tan](../../javascript/reference/math-tan-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Stringhe modello](../../javascript/advanced/template-strings-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[Metodo test](../../javascript/reference/test-method-regular-expression-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Istruzione this](../../javascript/reference/this-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Istruzione throw](../../javascript/reference/throw-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo toArray](../../javascript/reference/toarray-method-vbarray-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo toDateString](../../javascript/reference/todatestring-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo toExponential](../../javascript/reference/toexponential-method-number-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo toFixed](../../javascript/reference/tofixed-method-number-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo toGMTString](../../javascript/reference/togmtstring-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo toISOString](../../javascript/reference/toisostring-method-date-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Metodo toJSON](../../javascript/reference/tojson-method-date-javascript.md)|N|Y|Y|Y|Y|Y|Y|  
|[Metodo toLocaleDateString](../../javascript/reference/tolocaledatestring-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo toLocaleLowercase](../../javascript/reference/tolocalelowercase-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo toLocaleString](../../javascript/reference/tolocalestring-method-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo toLocaleTimeString](../../javascript/reference/tolocaletimestring-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo toLocaleUppercase](../../javascript/reference/tolocaleuppercase-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo toLowerCase](../../javascript/reference/tolowercase-method-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo toPrecision](../../javascript/reference/toprecision-method-number-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo toString](../../javascript/reference/tostring-method-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo toTimeString](../../javascript/reference/totimestring-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo toUpperCase](../../javascript/reference/touppercase-method-string-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo toUTCString](../../javascript/reference/toutcstring-method-date-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo trim](../../javascript/reference/trim-method-string-javascript.md)|N|N|Y|Y|Y|Y|Y|  
|[Istruzione try](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Operatore typeof](../../javascript/reference/typeof-operator-decrementjavascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo ubound](../../javascript/reference/ubound-method-vbarray-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Oggetto Uint8Array](../../javascript/reference/uint8array-object.md)|N|N|N|Y|Y|Y|Y|  
|[Oggetto Uint16Array](../../javascript/reference/uint16array-object.md)|N|N|N|Y|Y|Y|Y|  
|[Oggetto Uint32Array](../../javascript/reference/uint32array-object.md)|N|N|N|Y|Y|Y|Y|  
|[Oggetto Uint8ClampedArray](../../javascript/reference/uint8clampedarray-object-javascript.md)|N|N|N|N|Y|Y|v8: N<br />v8.1 (Win): Y<br />v8.1 (Phone): N<br />v10: Y|  
|[Operatore di negazione unario (-)](../../javascript/reference/subtraction-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Costante undefined](../../javascript/reference/undefined-constant-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Funzione unescape](../../javascript/reference/unescape-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Caratteri di escape di punti di codice Unicode](../../javascript/advanced/special-characters-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[Metodo unshift](../../javascript/reference/unshift-method-array-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Operatore di assegnazione Right Shift senza segno (>>>=)](../../javascript/reference/unsigned-right-shift-assignment-operator-decrement-equal-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Operatore Right Shift senza segno (>>>)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Direttiva use strict](../../javascript/reference/use-strict-directive.md)|N|N|N|Y|Y|Y|Y|  
|[Funzione UTC](../../javascript/reference/date-utc-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo valueOf](../../javascript/reference/valueof-method-object-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Metodo values (Array)](../../javascript/reference/values-method-array-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[Istruzione var](../../javascript/reference/var-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Oggetto VBArray](../../javascript/reference/vbarray-object-javascript.md)|Y|Y|Y|Y|Y|Y|N|  
|[Operatore void](../../javascript/reference/void-operator-decrementjavascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Oggetto WeakMap](../../javascript/reference/weakmap-object-javascript.md)|N|N|N|N|Y|Y|v8: N<br />v8.1: Y|  
|[Oggetto WeakSet](../../javascript/reference/weakset-object-javascript.md)|N|N|N|N|N|Y|v8.1: N<br />v10: Y|  
|[Istruzione while](../../javascript/reference/while-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Oggetto WinRTError](../../javascript/reference/winrterror-object-javascript.md)|N|N|N|Y|Y|Y|Y|  
|[Istruzione with](../../javascript/reference/with-statement-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Funzione write](../../javascript/reference/debug-write-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
|[Funzione writeln](../../javascript/reference/debug-writeln-function-javascript.md)|Y|Y|Y|Y|Y|Y|Y|  
  
 \* Supporta gli oggetti DOM ma gli oggetti non definiti dall'utente. Gli attributi `enumerable` e `configurable` possono essere specificati, ma non vengono usati.  
  
## <a name="see-also"></a>Vedere anche  
 [definizione della compatibilità del documento](http://go.microsoft.com/fwlink/?LinkId=208537)