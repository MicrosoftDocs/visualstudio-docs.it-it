---
title: Metodo localeCompare (String) (JavaScript) | Documenti Microsoft
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
- localeCompare
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- localeCompare method
ms.assetid: 66914079-12dd-4393-a84c-c05f58231c36
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 056a440d26c4ebf48bd762968fa32ea1efdfb443
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="localecompare-method-string-javascript"></a>Metodo localeCompare (String) (JavaScript)
Determina se due stringhe sono equivalenti nelle impostazioni locali correnti.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
stringVar.localeCompare(stringExp[, locales][, options])   
```  
  
## <a name="parameters"></a>Parametri  
 `stringVar`  
 Obbligatorio. Prima stringa da confrontare.  
  
 `stringExp`  
 Obbligatorio. Seconda stringa da confrontare.  
  
 `locales`  
 Parametro facoltativo. Una matrice di stringhe delle impostazioni locali che contengono uno o più linguaggi o tag per le impostazioni locali. Se si include più di una stringa delle impostazioni locali, elencarle in ordine decrescente di priorità in modo che la prima voce siano le impostazioni locali desiderate. Se si omette questo parametro, le impostazioni locali predefinite del runtime JavaScript vengono utilizzate. Questo parametro deve essere conforme alle [BCP 47](http://tools.ietf.org/html/rfc5646) standard, vedere il [oggetto intl. Collator](../../javascript/reference/intl-collator-object-javascript.md) per informazioni dettagliate.  
  
 `options`  
 Parametro facoltativo. Oggetto che contiene una o più proprietà che specificano opzioni di formattazione per la data e l'ora. vedere il [oggetto intl. Collator](../../javascript/reference/intl-collator-object-javascript.md) per informazioni dettagliate.  
  
## <a name="remarks"></a>Note  
 Per le stringhe di confronto, è possibile specificare `String` oggetti o valori letterali stringa.  
  
 A partire da Internet Explorer 11, `localeCompare` utilizza il `Intl.Collator` oggetto internamente per eseguire confronti, che aggiunge il supporto per il `locales` e `options` parametri. Per ulteriori informazioni su questi parametri, vedere [intl. Collator](../../javascript/reference/intl-collator-object-javascript.md) e [Intl.Collator.compare](../../javascript/reference/compare-property-intl-collator.md).  
  
> [!IMPORTANT]
>  Il `locales` e `options` parametri non sono supportati in tutte le modalità documento e le versioni del browser. Per ulteriori informazioni, vedere la sezione Requisiti di sicurezza.  
  
 Il `localeCompare` metodo esegue un confronto di stringhe con distinzione delle impostazioni locali di `stringVar` e `stringExp` e restituisce uno dei seguenti risultati, a seconda dell'ordinamento delle impostazioni locali predefinite di sistema:  
  
-   -1 se `stringVar` precede `stringExp`.  
  
-   + 1 se `stringVar` ordinato alfabeticamente dopo `stringExp`.  
  
-   0 (zero) se le due stringhe sono equivalenti.  
  
## <a name="example"></a>Esempio  
 Il codice seguente viene illustrato come utilizzare `localeCompare`.  
  
```JavaScript  
var str1 = "def";  
var str2 = "abc"  
  
document.write(str1.localeCompare(str2) + "<br/>");  
  
// Output: 1  
var str3 = "ghi";  
  
document.write(str1.localeCompare(str3)+ "<br/>");  
  
// Output: -1  
var str4 = "def";  
  
document.write(str1.localeCompare(str4));  
  
// Output: 0  
```  
  
## <a name="example"></a>Esempio  
 Il codice seguente viene illustrato come utilizzare `localeCompare` con le impostazioni locali italiano (Italia).  
  
```JavaScript  
var str1 = "a";  
var str2 = "b";  
  
document.write(str1.localeCompare(str2, "de-DE"));  
  
// Output  
// - 1  
```  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come utilizzare `localeCompare` con le impostazioni locali italiano (Italia) e un'estensione specifica delle impostazioni locali che specifica l'ordinamento per tedesche rubriche. Questo esempio illustra le differenze specifiche delle impostazioni locali.  
  
```JavaScript  
var arr = ["ä", "ad", "af", "a"];  
  
document.write(arr[0].localeCompare(arr[1], "de-DE-u-co-phonebk"));  // Returns 1  
document.write (arr[0].localeCompare(arr[2], "de-DE-u-co-phonebk"));  // Returns -1  
document.write (arr[0].localeCompare(arr[3], "de-DE-u-co-phonebk"));  // Returns 1  
  
document.write (arr[0].localeCompare(arr[1], "de-DE"));  // Returns -1  
document.write (arr[0].localeCompare(arr[2], "de-DE"));  // Returns -1  
document.write (arr[0].localeCompare(arr[3], "de-DE"));  // Returns 1  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 `locales` e `options` parametri:  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo toLocaleString (Object)](../../javascript/reference/tolocalestring-method-object-javascript.md)