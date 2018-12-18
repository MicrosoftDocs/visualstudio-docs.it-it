---
title: toLocaleString (numero) | Documenti Microsoft
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
ms.assetid: 42c05252-13c1-4943-b1a4-b33285aeab3e
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9b5e6378ec94e032c908a3502c0324c2a5a91b26
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="tolocalestring-number"></a>toLocaleString (Number)
Converte un numero in una stringa usando le impostazioni locali correnti o specificate.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
numberObj.toLocaleString([locales][, options])   
```  
  
#### <a name="parameters"></a>Parametri  
 `numberObj`  
 Obbligatorio. Il `Number` oggetto da convertire.  
  
 `locales`  
 Parametro facoltativo. Una matrice di stringhe delle impostazioni locali che contengono uno o più linguaggi o tag per le impostazioni locali. Se si include più di una stringa delle impostazioni locali, elencarle in ordine decrescente di priorità in modo che la prima voce siano le impostazioni locali desiderate. Se si omette questo parametro, le impostazioni locali predefinite del runtime JavaScript vengono utilizzate.  
  
 `options`  
 Parametro facoltativo. Oggetto che contiene una o più proprietà che specificano opzioni di formattazione per la data e l'ora.  
  
## <a name="remarks"></a>Note  
 A partire da Internet Explorer 11, `toLocaleString` Usa `Intl.NumberFormat` internamente per effettuare confronti, che aggiunge il supporto per il `locales` e `options` parametri. Per ulteriori informazioni su questi parametri, vedere [intl. NumberFormat](../../javascript/reference/intl-numberformat-object-javascript.md).  
  
> [!IMPORTANT]
>  Il `locales` e `options` parametri non sono supportati in tutte le modalità documento e le versioni del browser. Per ulteriori informazioni, vedere la sezione Requisiti di sicurezza.  
  
> [!NOTE]
>  Se si omette il `locales` parametro, utilizzare `toLocaleString` solo per visualizzare i risultati a un utente; mai utilizzato per calcolare i valori all'interno di uno script, perché il risultato restituito è specifiche del computer (il metodo restituisce le impostazioni locali correnti).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come utilizzare il `toLocaleString` metodo senza parametri.  
  
```JavaScript  
var n, s;  
n = new Number(100);  
s = "Current locale value is: ";  
s += n.toLocaleString();                 
document.write(s);  
  
// Output:  
// The value 100 as represented by the current locale.  
```  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come utilizzare il `toLocaleString` metodo con opzioni di confronto e delle impostazioni locali specificato.  
  
```JavaScript  
var number = 123456789;  
var options1 = { style: "percent" };  
var options2 = { style: "currency", currency: "INR" };  
  
document.write(number.toLocaleString("en-US"));  
// 123,456,789  
document.write(number.toLocaleString("ja-JP"));  
// 123,456,789  
document.write(number.toLocaleString("ar-SA", options1));  
// ١٢,٣٤٥,٦٧٨,٩٠٠ %  
document.write(number.toLocaleString("hi-IN", options2));  
// ₹ 12,34,56,789.00  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 `locales` e `options` parametri:  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo toLocaleDateString (Date)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)