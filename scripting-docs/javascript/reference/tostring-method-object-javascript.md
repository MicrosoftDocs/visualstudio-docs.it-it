---
title: Metodo toString (Object) (JavaScript) | Documenti Microsoft
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
- toString
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- ToString method
ms.assetid: c4ae9da2-60c9-486f-b00a-9df03fda4a35
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 518f988486bb527220884052768e61d099dbd716
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="tostring-method-object-javascript"></a>Metodo toString (Object) (JavaScript)
Restituisce la rappresentazione in formato stringa di un oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
objectname.toString([radix])  
```  
  
## <a name="parameters"></a>Parametri  
 `objectname`  
 Obbligatorio. Un oggetto per i quali è richiesta una rappresentazione di stringa.  
  
 `radix`  
 Parametro facoltativo. Specifica una radice per la conversione di valori numerici in stringhe. Questo valore viene utilizzato solo per i numeri.  
  
## <a name="remarks"></a>Note  
 Il **toString** metodo è un membro di tutti predefiniti [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] oggetti. Il comportamento dipende dal tipo di oggetto:  
  
|Oggetto|Comportamento|  
|------------|--------------|  
|Matrice|Elementi di un `Array` vengono convertiti in stringhe. Le stringhe risultanti sono concatenate, separati da virgole.|  
|Booleano|Se il valore booleano è **true**, restituisce "`true`". In caso contrario, restituisce "`false`".|  
|Data|Restituisce la rappresentazione testuale della data.|  
|Errore|Restituisce una stringa contenente il messaggio di errore associato.|  
|Funzione|Restituisce una stringa nel formato seguente, dove *functionname* è il nome della funzione il cui **toString** chiamata al metodo:<br /><br /> `function functionname( ) { [native code] }`|  
|Number|Restituisce la rappresentazione testuale del numero.|  
|String|Restituisce il valore di `String` oggetto.|  
|Predefinito|Restituisce `"[object objectname]"`, dove `objectname` è il nome del tipo di oggetto.|  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del **toString** metodo con un argomento di radice. Il valore restituito di funzione illustrata di seguito è una tabella di conversione radice.  
  
```JavaScript  
function CreateRadixTable (){  
   var s = "";  
  
   // Create table heading.  
   s += "Hex  Dec  Bin \n";  
  
   for (x = 0; x < 16; x++)  
   {  
      s += "   ";  
  
      // Convert to hexidecimal.  
      s += x.toString(16);  
      s += "     ";  
      if (x < 10) s += "  ";  
  
      // Convert to decimal.  
      s += x.toString(10);  
      s += "     ";  
  
      // Convert to binary.  
      s += x.toString(2);  
      s += "\n";  
   }  
  
   return(s);  
}  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
 **Si applica a**: [oggetto matrice](../../javascript/reference/array-object-javascript.md)&#124; [Oggetto Boolean](../../javascript/reference/boolean-object-javascript.md)&#124; [Data oggetto](../../javascript/reference/date-object-javascript.md)&#124; [Oggetto error](../../javascript/reference/error-object-javascript.md)&#124; [Funzione oggetto](../../javascript/reference/function-object-javascript.md)&#124; [Numero oggetto](../../javascript/reference/number-object-javascript.md)&#124; [Oggetto](../../javascript/reference/object-object-javascript.md)&#124; [Oggetto stringa](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzione function](../../javascript/reference/function-statement-javascript.md)