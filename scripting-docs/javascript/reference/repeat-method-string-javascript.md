---
title: Metodo Repeat (String) (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: fe02cdfd-f0f6-45a2-ad36-31c4300ef142
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b1a3d6edce877a97b0e46a69c43b667231c26981
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="repeat-method-string-javascript"></a>Metodo repeat (String) (JavaScript)
Restituisce un nuovo oggetto stringa con un valore uguale alla stringa originale ripetuto per il numero specificato di volte.  
  
## <a name="syntax"></a>Sintassi  
  
```  
stringObj.repeat(count);  
```  
  
#### <a name="parameters"></a>Parametri  
 `stringObj`  
 Obbligatorio. Oggetto stringa.  
  
 `count`  
 Obbligatorio. Numero di volte per cui ripetere la stringa originale nella stringa restituita.  
  
## <a name="exceptions"></a>Eccezioni  
 Questo metodo genera un oggetto RangeError se e solo se l'argomento è negativo o +Infinity.  
  
## <a name="remarks"></a>Note  
 Il metodo `repeat` concatena la stringa originale alla nuova stringa per il numero di volte specificato da `count`.  
  
 Questo metodo genera un errore se `count` non è un numero positivo minore di `Infinity`.  
  
## <a name="example"></a>Esempio  
  
```JavaScript  
"abc".repeat(3); // Returns "abcabcabc"  
"abc".repeat(0); // Returns an empty string.  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]