---
title: Oggetto Error (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Error
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: Error object
ms.assetid: 0b27d6ec-3997-4e91-a6c0-5afbaf494db7
caps.latest.revision: "25"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: efc03f13a501a1a13a2e7f3eea000b406559f30b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="error-object-javascript"></a>Oggetto Error (JavaScript)
Contiene informazioni relative agli errori.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
      errorObj = new Error()  
errorObj = new Error([number])  
errorObj = new Error([number[, description]])  
```  
  
## <a name="parameters"></a>Parametri  
 `errorObj`  
 Obbligatorio. Nome della variabile a cui l'oggetto `Error` è assegnato. L'assegnazione della variabile viene omessa quando si crea l'errore utilizzando un'istruzione `throw`.  
  
 `number`  
 Parametro facoltativo. Valore numerico assegnato a un errore. Se omesso, il valore è zero.  
  
 `description`  
 Parametro facoltativo. Stringa breve che descrive un errore. Se omessa, corrisponde a una stringa vuota.  
  
## <a name="remarks"></a>Note  
 Ogni volta che si verifica un errore di runtime, viene creata un'istanza dell'oggetto `Error` per descrivere l'errore. A questa istanza sono associate due proprietà intrinseche che contengono la descrizione dell'errore (proprietà `description`) e il numero dell'errore (proprietà `number`). Per ulteriori informazioni, vedere [errori di runtime JavaScript](../../javascript/reference/javascript-run-time-errors.md).  
  
 Un numero di errore è un valore a 32 bit. Il valore a 16 bit di livello superiore è il codice descrittivo, mentre il valore di livello inferiore rappresenta il codice effettivo dell'errore.  
  
 Gli oggetti `Error` possono essere creati anche in modo esplicito, utilizzando la sintassi indicata in precedenza o generati mediante l'istruzione `throw`. In entrambi i casi, è possibile aggiungere tutte le proprietà scelte per espandere le funzionalità dell'oggetto `Error`.  
  
 In genere, la variabile locale creata in un **try … catch** istruzione fa riferimento all'oggetto creato in modo implicito `Error` oggetto. Di conseguenza, è possibile utilizzare il numero e la descrizione dell'errore nel modo desiderato.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo dell'oggetto `Error`.  
  
```  
function checkInput(x) {  
    try  
    {  
        if (isNaN(parseInt(x))) {  
            throw new Error("Input is not a number.");  
        }  
    }  
    catch(e)  
    {  
        document.write(e.description);  
    }  
}  
  
checkInput("not a number");  
```  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo dell'oggetto `Error` creato in modo implicito.  
  
```JavaScript  
try  
   {  
   // Cause an error.  
   x = y;  
   }  
catch(e)  
   {  
      document.write(e);  
      document.write ("<br />");  
  
      document.write ("Number: ");  
      document.write (e.number & 0xFFFF);  
      document.write ("<br />");  
  
      document.write ("Facility Code: ");  
      document.write(e.number>>16 & 0x1FFF);  
      document.write ("<br />");  
  
      document.write ("Description: ");  
      document.write (e.description);  
   }  
  
// Output:  
// ReferenceError: 'y' is undefined  
// Number: 5009  
// Facility Code: 10  
// Description: 'y' is undefined  
  
```  
  
## <a name="methods"></a>Metodi  
 [Metodo toString (Error)](../../javascript/reference/tostring-method-error.md) &#124; [metodo valueOf (Date)](../../javascript/reference/valueof-method-date.md)  
  
## <a name="properties"></a>Proprietà  
 [Proprietà constructor (Error)](../../javascript/reference/constructor-property-error.md) &#124; [proprietà description](../../javascript/reference/description-property-error-javascript.md) &#124; [proprietà messaggio](../../javascript/reference/message-property-error-javascript.md) &#124; [proprietà name](../../javascript/reference/name-property-error-javascript.md) &#124; [proprietà number](../../javascript/reference/number-property-error-javascript.md) &#124; [proprietà prototype (Error)](../../javascript/reference/prototype-property-error.md) &#124; [proprietà stack (Error)](../../javascript/reference/stack-property-error-javascript.md) &#124; [proprietà stackTraceLimit (Error)](../../javascript/reference/stacktracelimit-property-error-javascript.md)  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Operatore new](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Istruzione throw](../../javascript/reference/throw-statement-javascript.md)   
 [try...... finally istruzione catch](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [Istruzione var](../../javascript/reference/var-statement-javascript.md)   
 [App di esempio JavaScript HiLo (Windows Store)](http://hilojs.codeplex.com/SourceControl/latest)