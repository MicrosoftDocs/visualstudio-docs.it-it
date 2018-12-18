---
title: Metodo toJSON (Date) (JavaScript) | Documenti Microsoft
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
- toJSON method
ms.assetid: f91df030-e9c9-425e-8e6d-b46bdda66cb6
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a131c7b248ca0486ab0b3b02d40e4351136c37c9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="tojson-method-date-javascript"></a>Metodo toJSON (Date) (JavaScript)
Utilizzato per il [JSON. stringify](../../javascript/reference/json-stringify-function-javascript.md) metodo per consentire la trasformazione di dati di un oggetto per la serializzazione di JavaScript Object Notation (JSON).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
objectname.toJSON()  
```  
  
## <a name="parameters"></a>Parametri  
 `objectname`  
 Obbligatorio. Un oggetto per cui JSON serializzazione desiderata.  
  
## <a name="remarks"></a>Note  
 Il `toJSON` metodo viene utilizzato il `JSON.stringify` (funzione). `JSON.stringify`Serializza un [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] valore in testo JSON. Se un `toJSON` metodo è fornito per `JSON.stringify`, `toJSON` metodo viene chiamato quando `JSON.stringify` viene chiamato.  
  
 Il `toJSON` metodo è un membro predefinito del [data](../../javascript/reference/date-object-javascript.md) [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] oggetto. Restituisce una stringa di data con formato ISO per il fuso orario UTC (indicato dal suffisso Z).  
  
 È possibile eseguire l'override di `toJSON` metodo per il `Date` digitare oppure definire un `toJSON` metodo per altri tipi di oggetto ottenere una trasformazione dei dati per il tipo di oggetto specifico prima della serializzazione JSON.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente usa il `toJSON` metodo per serializzare i valori dei membri di stringa in lettere maiuscole. Il `toJSON` metodo viene chiamato quando `JSON.stringify` viene chiamato.  
  
```JavaScript  
var contact = new Object();  
contact.firstname = "Jesper";  
contact.surname = "Aaberg";  
contact.phone = ["555-0100", "555-0120"];  
  
contact.toJSON = function(key)  
 {  
    var replacement = new Object();  
    for (var val in this)  
    {  
        if (typeof (this[val]) === 'string')  
            replacement[val] = this[val].toUpperCase();  
        else  
            replacement[val] = this[val]  
    }  
    return replacement;  
};  
  
var jsonText = JSON.stringify(contact);  
  
/* The value of jsonText is:  
'{"firstname":"JESPER","surname":"AABERG","phone":["555-0100","555-0120"]}'  
*/  
```  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come utilizzare il `toJSON` metodo che è membro predefinito di [data](../../javascript/reference/date-object-javascript.md) oggetto.  
  
```JavaScript  
var dt = new Date('8/24/2009');  
dt.setUTCHours(7, 30, 0);  
var jsonText = JSON.stringify(dt);  
  
/* The value of jsonText is:  
'"2009-08-24T07:30:00Z"'  
*/  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv58](../../javascript/reference/includes/jsv58-md.md)]**Si applica a:** [oggetto data](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto JSON](../../javascript/reference/json-object-javascript.md)   
 [Funzione JSON. Parse](../../javascript/reference/json-parse-function-javascript.md)   
 [Funzione JSON. stringify](../../javascript/reference/json-stringify-function-javascript.md)   
 [Metodi JavaScript](../../javascript/reference/javascript-methods.md)