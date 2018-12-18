---
title: "Proprietà Message (Error) (JavaScript) | Documenti Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: message
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: Message property
ms.assetid: 8cab0392-e0db-4714-827c-47ab04e8b4f2
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9dbd2db6c6d31dc48d90c3b07d2388eacf73ae7a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="message-property-error-javascript"></a>Proprietà message (Error) (JavaScript)
Restituisce una stringa di messaggio di errore.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
errorObj.message  
```  
  
## <a name="parameters"></a>Parametri  
 `errorObj`  
 Obbligatorio. Istanza di `Error` oggetto.  
  
## <a name="remarks"></a>Note  
 Il `message` proprietà restituisce una stringa che contiene un messaggio di errore associato a un errore specifico.  
  
 Il `description` e `message` proprietà forniscono la stessa funzionalità. Il `description` proprietà fornisce la compatibilità; `message` è conforme allo standard ECMA.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente genera un'eccezione TypeError generata e visualizza il nome dell'errore e il relativo messaggio.  
  
```JavaScript  
try  
{  
    // Cause an error.  
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
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
 **Si applica a**: [oggetto Error](../../javascript/reference/error-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà Description (Error)](../../javascript/reference/description-property-error-javascript.md)   
 [Proprietà name (Error)](../../javascript/reference/name-property-error-javascript.md)