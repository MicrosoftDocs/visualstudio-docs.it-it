---
title: Metodo toLocaleDateString (Date) (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: toLocaleDateString
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: toLocaleDateString method
ms.assetid: 0b83715c-8ced-4bd7-8940-a8007d002d10
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d6b4b019ad329a73bec13766932fbcadfa2ed133
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="tolocaledatestring-method-date-javascript"></a>Metodo toLocaleDateString (Date) (JavaScript)
Restituisce una data come valore di stringa appropriato alle impostazioni locali correnti dell'ambiente host o le impostazioni locali specificate.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
dateObj.toLocaleDateString( [locales][, options])   
```  
  
#### <a name="parameters"></a>Parametri  
 `dateObj`  
 Obbligatorio. Oggetto `Date`.  
  
 `locales`  
 Parametro facoltativo. Una matrice di stringhe delle impostazioni locali che contengono uno o più linguaggi o tag per le impostazioni locali. Se si include più di una stringa delle impostazioni locali, elencarle in ordine decrescente di priorità in modo che la prima voce siano le impostazioni locali desiderate. Se si omette questo parametro, le impostazioni locali predefinite del runtime JavaScript vengono utilizzate.  
  
 `options`  
 Parametro facoltativo. Oggetto che contiene una o più proprietà che specificano opzioni di formattazione per la data e l'ora.  
  
## <a name="remarks"></a>Note  
 A partire da Internet Explorer 11, `toLocaleDateString` Usa `Intl.DateTimeFormat` internamente per formattare la data, che aggiunge il supporto per il `locales` e `options` parametri. Per ulteriori informazioni su questi parametri, vedere [intl. DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md).  
  
> [!IMPORTANT]
>  Il `locales` e `options` parametri non sono supportati in tutte le modalità documento e le versioni del browser. Per ulteriori informazioni, vedere la sezione Requisiti di sicurezza.  
  
 Quando si utilizza `toLocaleDateString` in Internet Explorer 10 documento degli standard di modalità, modalità documento precedenti e la modalità non standard:  
  
-   Restituisce un valore stringa che contiene una data nel fuso orario corrente.  
  
-   Data restituita è nel formato predefinito delle impostazioni locali correnti dell'ambiente host.  
  
 Se si omette il `locales` parametro, il valore restituito di questo metodo non può essere ritenuto scripting, perché cambia a seconda del computer. In questo scenario, utilizzare il metodo solo al testo visualizzato - mai come parte di un calcolo.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come utilizzare il `toLocaleDateString` metodo con opzioni di confronto e delle impostazioni locali specificato.  
  
```JavaScript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = { weekday: "long", year: "numeric", month: "short",  
    day: "numeric" };  
  
// Using I18N toLocaleString  
document.write(date.toLocaleDateString("en-US"));  
document.write(date.toLocaleDateString("ja-JP"));  
document.write(date.toLocaleDateString("ar-SA", options));  
document.write(date.toLocaleDateString("hi-IN", options));  
  
// Output:  
// ‎2‎/‎1‎/‎2013‎   
// ‎2013‎年‎2‎月‎1‎日‎  
// ‏الجمعة‏, ‏٢٠‏ ‏ربيع الأول‏, ‏١٤٣٤  
// ‎शुक्रवार‎, ‎01‎ ‎फरवरी‎ ‎2013  
  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 `locales` e `options` parametri:  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo toDateString (Date)](../../javascript/reference/todatestring-method-date-javascript.md)   
 [Metodo toLocaleTimeString (Date)](../../javascript/reference/tolocaletimestring-method-date-javascript.md)