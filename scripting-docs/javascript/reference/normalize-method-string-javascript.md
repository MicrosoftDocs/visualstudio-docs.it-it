---
title: Metodo Normalize (stringa) (JavaScript) | Documenti Microsoft
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
ms.assetid: d50077c1-b5fa-4e7a-9c9d-dc66cfc423ac
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aece38339ea1ce8924f404938b2d35d07504d539
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="normalize-method-string-javascript"></a>Metodo normalize (stringa) (JavaScript)
Restituisce il formato di normalizzazione Unicode di una stringa specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
stringObj.normalize([form]);  
```  
  
#### <a name="parameters"></a>Parametri  
 `stringObj`  
 Obbligatorio. Oggetto stringa rispetto da testare.  
  
 `form`  
 Parametro facoltativo. Valore del formato di normalizzazione Unicode.  
  
## <a name="return-value"></a>Valore restituito  
 Formato di normalizzazione Unicode di una stringa specificata.  
  
## <a name="exceptions"></a>Eccezioni  
 Se `form` è un valore non supportato, viene generato un oggetto `RangeError`.  
  
## <a name="remarks"></a>Note  
 Se `stringObj` non è una stringa, viene convertito in stringa prima che il metodo tenti di restituire il formato di normalizzazione Unicode della stringa.  
  
 `form`deve essere un valore di formato di normalizzazione Unicode, "NFC", "NFD", "NFKC" o "NFKD", corrispondente ai valori specificati per [Unicode Standard Annex #15](http://www.unicode.org/reports/tr15/). Il valore predefinito di `form` è "NFC".  
  
## <a name="example"></a>Esempio  
 Negli esempi di codice viene mostrato utilizzare questo `normalize` metodo.  
  
```JavaScript  
// ANGSTORM SIGN and LATIN CAPITAL A WITH RING ABOVE is canonically equivalent  
"\u212b".normalize("NFC") === "\u00c5";  
  
// Decomposed, ANGSTOM SIGN is LATIN CAPITAL A followed by COMBINING RING ABOVE  
"\u212b".normalize("NFD") === "\u0041\u030a"  
  
// Normalization Form C will combine the result back into the precombined character  
"\u0041\u030a".normalize("NFC") === "\u00c5"  
  
// LATIN SMALL LIGATURE FI is compatibility equivalent with LATIN SMALL LETTER F followed by  
// LATIN SMALL LETTER I.  
"\ufb01".normalize("NFKD") === "fi";  
  
// Same mapping in NFKC  
"\ufb01".normalize("NFKC") === "fi";  
  
// NFKC will not recombine compatibility characters.  
"fi".normalize("NFKC") === "fi";  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]