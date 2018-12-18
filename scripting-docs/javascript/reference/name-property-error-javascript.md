---
title: "Proprietà Name (Error) (JavaScript) | Documenti Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: name
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Name property
- name property, error name
ms.assetid: 94df2d6b-f1a1-4931-a956-0a930cb87f76
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1a12157b4c467499fab23f7c4cb1be91e9ac5440
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="name-property-error-javascript"></a>Proprietà name (Error) (JavaScript)
Restituisce il nome di un errore.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
errorObj.  
name  
  
```  
  
## <a name="parameters"></a>Parametri  
 `errorObj`  
 Obbligatorio. Istanza di `Error` oggetto.  
  
## <a name="remarks"></a>Note  
 Il **nome** proprietà restituisce il nome o l'eccezione del tipo di un errore. Quando si verifica un errore di runtime, la proprietà name è impostata su uno dei seguenti tipi di eccezione nativa:  
  
|Tipo di eccezione|Significato|  
|--------------------|-------------|  
|ConversionError|Questo errore si verifica ogni volta che viene eseguito un tentativo di convertire un oggetto in un elemento a cui non può essere convertito.|  
|RangeError|Questo errore si verifica quando viene specificata una funzione con un argomento che ha superato l'intervallo consentito. Questo errore si verifica ad esempio, se si tenta di costruire un `Array` oggetto con una lunghezza che non è un numero intero positivo valido.|  
|ReferenceError|Questo errore si verifica quando viene rilevato un riferimento non valido. Questo errore si verifica, ad esempio, se un riferimento previsto è `null`.|  
|RegExpError|Questo errore si verifica quando si verifica un errore di compilazione con un'espressione regolare. Una volta compilata l'espressione regolare, tuttavia, non può verificarsi l'errore. In questo esempio si verifica, ad esempio, quando un'espressione regolare viene dichiarata con un modello che ha una sintassi non valida o flag diverso da **si**, **g**, o **m**, o se contiene lo stesso flag più volte.|  
|SyntaxError|Questo errore si verifica quando viene analizzato il testo di origine e il testo di origine non segue sintassi corretta. Questo errore si verifica, ad esempio, se il `eval` funzione viene chiamata con un argomento non di testo di programma valido.|  
|TypeError|Questo errore si verifica ogni volta che il tipo effettivo di un operando non corrisponde al tipo previsto. Un esempio di quando si verifica questo errore è una chiamata di funzione su un elemento che non è un oggetto o non supporta la chiamata.|  
|URIError|Questo errore si verifica quando viene rilevato un valido indicatore URI (Uniform Resource). Ad esempio, si tratta di errore si verifica quando un carattere non valido si trova in una stringa da codificare o decodificare.|  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente genera un'eccezione TypeError generata e visualizza il nome dell'errore e il relativo messaggio.  
  
```JavaScript  
try  
{  
    var x = y;  
}  
catch(e)  
{  
    document.write ("Error Message: " + e.message);  
    document.write ("<br />");  
    document.write ("Error Code: ");  
    document.write (e.number & 0xFFFF)  
    document.write ("<br />");  
    document.write ("Error Name: " + e.name);  
}  
```  
  
## <a name="example"></a>Esempio  
 L'output di questo codice è come indicato di seguito.  
  
```JavaScript  
Error Message: 'y' is undefined  
Error Code: 5009  
Error Name: TypeError  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Si applica a**: [oggetto Error](../../javascript/reference/error-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà Description (Error)](../../javascript/reference/description-property-error-javascript.md)   
 [Proprietà Message (Error)](../../javascript/reference/message-property-error-javascript.md)   
 [Proprietà number (Error)](../../javascript/reference/number-property-error-javascript.md)