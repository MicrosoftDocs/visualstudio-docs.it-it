---
title: Oggetto intl. NumberFormat (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: NumberFormat
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 820bc90f-f1e7-457a-b90d-487dfc3a736d
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0dcb02dbe0d7a7eef88750c440a4fbcdde3ea7ee
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="intlnumberformat-object-javascript"></a>Oggetto Intl.NumberFormat (JavaScript)
Fornisce la formattazione di numeri specifica delle impostazioni locali.  
  
## <a name="syntax"></a>Sintassi  
  
```  
numberFormatObj = new Intl.NumberFormat([locales][, options])  
```  
  
#### <a name="parameters"></a>Parametri  
 `numberFormatObj`  
 Obbligatorio. Il nome della variabile a cui assegnare l'oggetto `NumberFormat`.  
  
 `locales`  
 Parametro facoltativo. Una matrice di stringhe delle impostazioni locali che contengono uno o più linguaggi o tag per le impostazioni locali. Se si include più di una stringa delle impostazioni locali, elencarle in ordine decrescente di priorità in modo che la prima voce siano le impostazioni locali desiderate. Se si omette questo parametro, le impostazioni locali predefinite del runtime JavaScript vengono utilizzate. Per altre informazioni, vedere la sezione Osservazioni.  
  
 `options`  
 Parametro facoltativo. Oggetto che contiene uno o più proprietà che specificano le opzioni di formattazione numeriche. Per informazioni dettagliate, vedere la sezione Osservazioni.  
  
## <a name="remarks"></a>Note  
 Il `locales` parametro deve essere conforme alle [BCP 47](http://tools.ietf.org/html/rfc5646) tag di lingua e impostazioni locali, ad esempio "en-US" e "zh-CN". Il tag può includere il linguaggio, l'area, il paese e il variant. Per esempi di tag di linguaggio, vedere [appendice](http://tools.ietf.org/html/rfc5646#appendix-A) di BCP 47. Per `NumberFormat`, è possibile aggiungere il **-u** sottotag seguita da - nu per specificare un'estensione di sistema di numerazione:  
  
 "*language*-*area*-u-n -*numberingsystem*"  
  
 dove *numberingsystem* può essere uno dei seguenti: Emirati arabi, arabext, bali, beng, deva, fullwide, gujr, esperti, hanidec, khmr, knda, laoo, latn, esercizio, mylm, mong, mymr, orya, tamldec, telu, tailandese, tibt.  
  
 Il parametro `options` può includere le seguenti proprietà:  
  
|Proprietà|Descrizione|Valori possibili|Valore predefinito|  
|--------------|-----------------|---------------------|-------------------|  
|`localeMatcher`|Specifica l'algoritmo di corrispondenza delle impostazioni locali da utilizzare.|"ricerca", "adatta"|"best fit"|  
|`style`|Specifica lo stile del formato numero.|"decimale", "percentuale", "valuta"|"decimale"|  
|`currency`|Specifica il valore di valuta ISO 4217 come un codice alfabetico. Se il `style` è impostato su "valuta", questo valore è obbligatorio.|Vedere l'immagine ISO [valuta e fondi codice elenco](http://www.currency-iso.org/en/home/tables/table-a1.html).|undefined|  
|`currencyDisplay`|Specifica se visualizzare la valuta come un codice di valuta alfabetico lettere ISO 4217, un simbolo di valuta localizzata o un nome localizzato di valuta. Questo valore viene utilizzato solo se `style` è impostata su "valuta".|"code", "symbol", "name"|"symbol"|  
|`useGrouping`|Specifica se è necessario utilizzare un separatore di raggruppamento.|true, false|`true`.|  
|`minimumIntegerDigits`|Specifica il numero minimo di cifre integrali da utilizzare.|1-21.|21|  
|`minimumFractionDigits`|. Specifica il numero minimo di cifre frazionarie pari a essere utilizzato.|da 0 a 20.|0|  
|`maximumFractionDigits`|Specifica il numero massimo di cifre frazionarie pari a essere utilizzato.|Questo valore può variare da `minimumFractionDigits` a 20.|20.|  
|`minimumSignificantDigits`|Specifica il numero minimo di cifre frazionarie da visualizzare.|Questo valore può variare da 1 a 21.|1|  
|`maximumSignificantDigits`|Specifica il numero massimo di cifre frazionarie da visualizzare.|Questo valore può variare da `minimumSignificantDigits` su 21.|21|  
  
## <a name="properties"></a>Proprietà  
 Nella tabella seguente sono elencate le proprietà dell'oggetto `NumberFormat`.  
  
|||  
|-|-|  
|Proprietà|Descrizione|  
|[costruttore](../../javascript/reference/constructor-property-intl-numberformat.md)|Specifica la funzione che crea un oggetto formattatore number.|  
|[format](../../javascript/reference/format-property-intl-numberformat.md)|Restituisce una funzione che formatta un numero utilizzando le impostazioni del formattatore numero.|  
|[prototipo](../../javascript/reference/prototype-property-intl-numberformat.md)|Restituisce un riferimento al prototipo per un formattatore di numero.|  
  
## <a name="methods"></a>Metodi  
 Nella tabella seguente sono elencati i metodi dell'oggetto `NumberFormat`:  
  
|||  
|-|-|  
|Metodo|Descrizione|  
|[resolvedOptions](../../javascript/reference/resolvedoptions-method-intl-numberformat.md)|Restituisce un oggetto che contiene le proprietà e i valori dell'oggetto formattatore numero.|  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene creato un `NumberFormat` oggetto per le impostazioni locali en-US con le opzioni di formattazione specificate.  
  
```JavaScript  
var nf = new Intl.NumberFormat(["en-US"], {  
    style: "currency",  
    currency: "CNY",  
    currencyDisplay: "symbol",  
    maximumFractionDigit: 1  
});  
  
if (console && console.log) {  
    console.log(nf.format(100)); // Returns ¥100.00  
}  
```  
  
## <a name="example"></a>Esempio  
 Gli esempi seguenti mostrano il risultato usando diverse opzioni e impostazioni locali diverse.  
  
```JavaScript  
var number = 123456789;  
var options1 = { style: "percent" };  
var options2 = { style: "currency", currency: "INR" };  
  
if (console && console.log) {  
    console.log(new Intl.NumberFormat("en-US").format(number));  
    // Returns 123,456,789  
    console.log(new Intl.NumberFormat("ja-JP").format(number));  
    // Returns 123,456,789  
    console.log(new Intl.NumberFormat("ar-SA", options1).format(number));  
    // Returns ١٢,٣٤٥,٦٧٨,٩٠٠ %  
    console.log(new Intl.NumberFormat("hi-IN", options2).format(number));  
    // Returns ₹ 12,34,56,789.00  
}  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [toLocaleString (numero)](../../javascript/reference/tolocalestring-number.md)   
 [Oggetto intl. Collator](../../javascript/reference/intl-collator-object-javascript.md)   
 [Oggetto Intl.DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md)