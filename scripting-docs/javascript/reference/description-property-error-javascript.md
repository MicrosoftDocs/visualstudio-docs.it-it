---
title: "Proprietà Description (Error) (JavaScript) | Documenti Microsoft"
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
- Description
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- error handling, error description
- Description property
- errors, description
ms.assetid: ea727f1e-2041-4400-965c-67e6d47a1ff0
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6135951fdf65698ed48b9bbacdcc55c1aac22d41
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="description-property-error-javascript"></a>Proprietà description (Error) (JavaScript)
Restituisce o imposta la stringa descrittiva associata a un errore specifico.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
object  
.description [= stringExpression]  
```  
  
## <a name="parameters"></a>Parametri  
 *object*  
 Obbligatorio. Qualsiasi istanza di un `Error` oggetto.  
  
 `stringExpression`  
 Parametro facoltativo. Un'espressione stringa contenente una descrizione dell'errore.  
  
## <a name="remarks"></a>Note  
 Il **descrizione** proprietà contiene la stringa di messaggio di errore associata a un errore specifico. Utilizzare il valore contenuto in questa proprietà per avvertire un utente a un errore.  
  
 Il **descrizione** e **messaggio** proprietà forniscono la stessa funzionalità; **descrizione** proprietà garantisce la compatibilità con le versioni precedenti;  **messaggio** è conforme allo standard ECMA.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del **descrizione** proprietà.  
  
```JavaScript  
try  
{  
// Cause an error:  
    x = y     
}  
catch(e)  
{  
// Prints "[object Error]":  
    document.write(e)  
    document.write (" ");  
// Prints 5009:  
    document.write((e.number & 0xFFFF))    
    document.write (" ");  
// Prints "'y' is undefined":  
    document.write(e.description);  
    document.write (" ");  
// Prints "'y' is undefined":  
    document.write(e.message)  
}  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
 **Si applica a**: [oggetto Error](../../javascript/reference/error-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà Number (Error)](../../javascript/reference/number-property-error-javascript.md)   
 [Proprietà Message (Error)](../../javascript/reference/message-property-error-javascript.md)   
 [Proprietà name (Error)](../../javascript/reference/name-property-error-javascript.md)