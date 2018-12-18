---
title: "numero di proprietà (errore) (JavaScript) | Documenti Microsoft"
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
- Number
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Number property
ms.assetid: 8697e20b-a2b0-4e26-85c0-ab07ddfe8281
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bbc229e7d0572e1a3dbed056b344da7ff9ce7292
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="number-property-error-javascript"></a>Proprietà number (Error) (JavaScript)
Restituisce o imposta il valore numerico associato a un errore specifico. Il `Error` proprietà predefinita dell'oggetto è **numero**.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
object  
.number [= errorNumber]  
```  
  
## <a name="parameters"></a>Parametri  
 *Oggetto*  
 Qualsiasi istanza di `Error` oggetto.  
  
 *numeroerrore*  
 Intero che rappresenta un errore.  
  
## <a name="remarks"></a>Note  
 Un numero di errore è un valore a 32 bit. La parola a 16 bit superiore è il codice di funzionalità e la parola più bassa è il codice di errore. Per determinare il codice di errore, utilizzare il `&` (OR bit per bit e) (operatore) per combinare le proprietà del numero con il numero esadecimale `0xFFFF`.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene generata un'eccezione e viene visualizzato il codice di errore che è derivato dal numero di errore.  
  
```JavaScript  
try  
    {  
    // Cause an error.  
    var x = y;  
    }  
catch(e)  
    {  
    document.write ("Error Code: ");  
    document.write (e.number & 0xFFFF)  
    document.write ("<br />");  
  
    document.write ("Facility Code: ")  
    document.write(e.number>>16 & 0x1FFF)  
    document.write ("<br />");  
  
    document.write ("Error Message: ")  
    document.write (e.message)  
    }  
```  
  
## <a name="example"></a>Esempio  
 L'output di questo codice è come indicato di seguito.  
  
```JavaScript  
Error Code: 5009  
Facility Code: 10  
Error Message: 'y' is undefined  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
 **Si applica a**: [oggetto Error](../../javascript/reference/error-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà Description (Error)](../../javascript/reference/description-property-error-javascript.md)   
 [Proprietà Message (Error)](../../javascript/reference/message-property-error-javascript.md)   
 [Proprietà name (Error)](../../javascript/reference/name-property-error-javascript.md)