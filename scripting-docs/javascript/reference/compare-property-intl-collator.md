---
title: "confrontare una proprietà (intl. Collator) | Documenti Microsoft"
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
ms.assetid: 59f274dc-6e52-4344-8d5c-b9f0000b66e0
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5bfd222ac8d2c94efe279177e7f4d8ffdf850f44
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="compare-property-intlcollator"></a>Proprietà compare (Intl.Collator)
Restituisce una funzione che confronta due stringhe utilizzando di ordinamento dell'utilità di confronto.  
  
## <a name="syntax"></a>Sintassi  
  
```JavaScript  
collatorObj.compare  
```  
  
#### <a name="parameters"></a>Parametri  
 `collatorObj`  
 Obbligatorio. Il nome del `Collator` oggetto da utilizzare per il confronto.  
  
## <a name="remarks"></a>Note  
 La funzione restituita dal `compare` proprietà accetta due argomenti, `x` e `y`e restituisce il risultato di un confronto specifiche delle impostazioni locali di `x` e `y` utilizzando le opzioni specificate nel `Collator` oggetto.  
  
 Il risultato del confronto sarà:  
  
-   -1 se `x` prima `y` nell'ordinamento.  
  
-   0 (zero) se `x` è uguale a `y` nell'ordinamento.  
  
-   1 se `x` dopo `y` nell'ordinamento.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene creato un `Collator` oggetto ed esegue un confronto.  
  
```JavaScript  
var co = new Intl.Collator(["de-DE-u-co-phonebk"]);  
  
if (console && console.log) {  
    console.log(co.compare("a", "b")); // Returns -1  
}  
```  
  
## <a name="example"></a>Esempio  
 L'esempio seguente usa `Collator` oggetti da ordinare una matrice. Questo esempio illustra le differenze specifiche delle impostazioni locali.  
  
```JavaScript  
var co1 = new Intl.Collator(["de-DE-u-co-phonebk"]);  
var co2 = new Intl.Collator(["de-DE"]);  
var co3 = new Intl.Collator(["en-US"]);  
  
var arr = ["ä", "ad", "af", "a"];  
  
if (console && console.log) {  
    console.log(arr.sort(co1.compare));  // Returns a,ad,ä,af  
    console.log(arr.sort(co2.compare));  // Returns a,ä,ad,af  
    console.log(arr.sort(co3.compare));  // Returns a,ä,ad,af  
}  
```  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene utilizzato un `Collator` oggetto per cercare una stringa.  
  
```JavaScript  
// String to search  
var arr = ["ä", "ad", "af", "a"];  
// String searched for  
var s = "af";  
  
var co = new Intl.Collator("de-DE", { usage: "search" });  
var matches = arr.filter(function (i) {  
    return co.compare(i, s) === 0;  
});  
  
if (console && console.log) {  
    console.log(matches);  // Returns af  
}  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Intl.Collator](../../javascript/reference/intl-collator-object-javascript.md)