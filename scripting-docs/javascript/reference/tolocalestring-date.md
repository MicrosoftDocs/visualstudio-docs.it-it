---
title: toLocaleString (Date) | Documenti Microsoft
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
ms.assetid: 3472d7bd-b255-4804-8407-c4a1e419a5a3
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b6dc7b1f38f7e57d1c10f7197bb73b13b3545380
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="tolocalestring-date"></a>toLocaleString (Date)
Converte una data in una stringa usando le impostazioni locali correnti o specificate.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
dateObj.toLocaleString([locales][, options])   
```  
  
#### <a name="parameters"></a>Parametri  
 `dateObj`  
 Obbligatorio. Il `Date` oggetto da convertire.  
  
 `locales`  
 Parametro facoltativo. Una matrice di stringhe delle impostazioni locali che contengono uno o più linguaggi o tag per le impostazioni locali. Se si include più di una stringa delle impostazioni locali, elencarle in ordine decrescente di priorità in modo che la prima voce siano le impostazioni locali desiderate. Se si omette questo parametro, le impostazioni locali predefinite del runtime JavaScript vengono utilizzate.  
  
 `options`  
 Parametro facoltativo. Oggetto che contiene una o più proprietà che specificano opzioni di formattazione per la data e l'ora.  
  
## <a name="remarks"></a>Note  
 A partire da Internet Explorer 11, `toLocaleString` Usa `Intl.DateTimeFormat` internamente per effettuare confronti, che aggiunge il supporto per il `locales` e `options` parametri. Per ulteriori informazioni su questi parametri, vedere [intl. DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md).  
  
> [!IMPORTANT]
>  Il `locales` e `options` parametri non sono supportati in tutte le modalità documento e le versioni del browser. Per ulteriori informazioni, vedere la sezione Requisiti di sicurezza.  
  
 Quando si utilizza `toLocaleString` in Internet Explorer 10 documento degli standard di modalità, modalità documento precedenti e la modalità non standard:  
  
-   Restituisce un `String` oggetto che contiene la data nel formato lungo predefinito di impostazioni locali correnti.  
  
-   Per le date comprese tra 1601 e D.C. 1999, la data viene formattata in base alle impostazioni internazionali di Pannello di controllo dell'utente.  
  
> [!NOTE]
>  Se si omette il `locales` parametro, utilizzare `toLocaleString` solo per visualizzare i risultati a un utente; mai utilizzato per calcolare i valori all'interno di uno script, perché il risultato restituito è specifica del computer.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come utilizzare il metodo `toLocaleString`.  
  
```JavaScript  
function toLocaleStrDemo(){     
   var d, s;                      //Declare variables.  
   d = new Date();                //Create Date object.  
   s = "Current setting is ";  
   s += d.toLocaleString();       //Convert to current locale.  
   return(s);                     //Return converted date  
}  
```  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come utilizzare il `toLocaleString` metodo con opzioni di confronto e delle impostazioni locali specificato.  
  
```JavaScript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = { weekday: "long", year: "numeric", month: "short",  
    day: "numeric" };  
  
// Using I18N toLocaleString  
document.write(date.toLocaleString("en-US"));  
document.write(date.toLocaleString("ja-JP"));  
document.write(date.toLocaleString("ar-SA", options));  
document.write(date.toLocaleString("hi-IN", options));  
  
// Output:  
// ‎2‎/‎1‎/‎2013‎ ‎6‎:‎00‎:‎00‎ ‎AM  
// ‎2013‎年‎2‎月‎1‎日‎ ‎6‎:‎00‎:‎00  
// ‏الجمعة‏, ‏٢٠‏ ‏ربيع الأول‏, ‏١٤٣٤  
// ‎शुक्रवार‎, ‎01‎ ‎फरवरी‎ ‎2013  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 `locales` e `options` parametri:  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo toLocaleDateString (Date)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)