---
title: Oggetto intl. DateTimeFormat (JavaScript) | Documenti Microsoft
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
- DateTimeFormat
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: cc555ac2-f31c-4239-a612-b84c08e3a37f
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9c50d6d7d939ebe05ce3ff9b434111413803ea40
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="intldatetimeformat-object-javascript"></a>Oggetto Intl.DateTimeFormat (JavaScript)
Fornisce la formattazione di data e ora specifica delle impostazioni locali.  
  
## <a name="syntax"></a>Sintassi  
  
```  
dateTimeFormatObj = new Intl.DateTimeFormat([locales][, options])  
```  
  
#### <a name="parameters"></a>Parametri  
 `dateTimeFormatObj`  
 Obbligatorio. Il nome della variabile a cui assegnare l'oggetto `DateTimeFormat`.  
  
 `locales`  
 Parametro facoltativo. Una matrice di stringhe delle impostazioni locali che contengono uno o più linguaggi o tag per le impostazioni locali. Se si include più di una stringa delle impostazioni locali, elencarle in ordine decrescente di priorità in modo che la prima voce siano le impostazioni locali desiderate. Se si omette questo parametro, le impostazioni locali predefinite del runtime JavaScript vengono utilizzate. Per altre informazioni, vedere la sezione Osservazioni.  
  
 `options`  
 Parametro facoltativo. Oggetto che contiene una o più proprietà che specificano opzioni di formattazione per la data e l'ora. Per informazioni dettagliate, vedere la sezione Osservazioni.  
  
## <a name="remarks"></a>Note  
 Il `locales` parametro deve essere conforme alle [BCP 47](http://tools.ietf.org/html/rfc5646) tag di lingua e impostazioni locali, ad esempio "en-US" e "zh-CN". Il tag può includere il linguaggio, l'area, il paese e il variant. Per esempi di tag di linguaggio, vedere [appendice](http://tools.ietf.org/html/rfc5646#appendix-A) di BCP 47. Per `DateTimeFormat`, è possibile aggiungere il **-u** sottotag nella stringa di impostazioni locali per includere una o entrambe le estensioni Unicode seguenti:  
  
-   -nu per specificare un'estensione di sistema di numerazione: *language*-*area*-u-n -*numberingsystem*  
  
     dove *numberingsystem* può essere uno dei seguenti: Emirati arabi, arabext, bali, beng, deva, fullwide, gujr, esperti, hanidec, khmr, knda, laoo, latn, esercizio, mylm, mong, mymr, orya, tamldec, telu, tailandese, tibt.  
  
-   -ca per specificare un calendario: *language*-*area*-u-Canada -*calendario*  
  
     dove *calendario* può essere uno dei seguenti: buddista, cinese, giapponese, gregory, islamica, islamicc.  
  
 Il parametro `options` può includere le seguenti proprietà:  
  
|Proprietà|Descrizione|Valori possibili|Valore predefinito|  
|--------------|-----------------|---------------------|-------------------|  
|`localeMatcher`|Specifica l'algoritmo di corrispondenza delle impostazioni locali da utilizzare.|"lookup","best fit"|"best fit"|  
|`formatMatcher`|Specifica l'algoritmo di corrispondenza del formato da utilizzare.|"basic", "best fit"|"best fit"|  
|`hour12`|Specifica se utilizzare un formato di 12 ore.|`true` (per il formato a 12 ore), `false` (per il formato a 24 ore)||  
|`timeZone`|Specifica il fuso orario. Come minimo, "UTC" è sempre supportato.|Valore di fuso orario come "UTC".|"UTC"|  
|`weekday`|Specifica la formattazione del giorno feriale.|"narrow", "short", "long".|undefined|  
|`era`|Specifica la formattazione dell'era.|"narrow", "short", "long".|undefined|  
|`year`|Specifica la formattazione dell'anno.|"2-digit", "numeric"|undefined o "numeric"|  
|`month`|Specifica la formattazione del mese.|"2-digit", "numeric", "narrow", "short", "long"|undefined o "numeric"|  
|`day`|Specifica la formattazione del giorno.|"2-digit", "numeric"|undefined o "numeric"|  
|`hour`|Specifica la formattazione dell'ora.|"2-digit", "numeric"|undefined|  
|`minute`|Specifica la formattazione del minuto.|"2-digit", "numeric"|undefined|  
|`second`|Specifica la formattazione del secondo.|"2-digit", "numeric"|undefined|  
|`timeZoneName`|Specifica la formattazione del fuso orario. La proprietà non è attualmente supportata.|"short", "long".|La proprietà non è attualmente supportata.|  
  
 I valori predefiniti per `weekday`, `era`, `year`, `month`, `day`, `hour`, `minute` e `second` sono `undefined`. Se non si impostano queste proprietà, per `year`, `month` e `day` viene utilizzata la formattazione "numeric".  
  
 Ogni impostazione locale deve supportare, come minimo, i seguenti formati:  
  
-   giorno della settimana, anno, mese, giorno, ora, minuto, secondo  
  
-   giorno della settimana, anno, mese, giorno  
  
-   anno, mese, giorno  
  
-   anno, mese  
  
-   mese, giorno  
  
-   ora. minuti, secondi  
  
-   ora, minuti  
  
## <a name="properties"></a>Proprietà  
 Nella tabella seguente sono elencate le proprietà dell'oggetto `DateTimeFormat`.  
  
|||  
|-|-|  
|Proprietà|Descrizione|  
|[costruttore](../../javascript/reference/constructor-property-intl-datetimeformat.md)|Specifica la funzione tramite cui viene creato un oggetto formattatore di data/ora.|  
|[format](../../javascript/reference/format-property-intl-datetimeformat.md)|Restituisce una funzione che formatta una data specifica delle impostazioni locali utilizzando le impostazioni del formattatore di data/ora.|  
|[prototipo](../../javascript/reference/prototype-property-intl-datetimeformat.md)|Restituisce un riferimento al prototipo per un formattatore di data/ora.|  
  
## <a name="methods"></a>Metodi  
 Nella tabella seguente sono elencati i metodi dell'oggetto `DateTimeFormat`:  
  
|||  
|-|-|  
|Metodo|Descrizione|  
|[resolvedOptions](../../javascript/reference/resolvedoptions-method-intl-datetimeformat.md)|Restituisce un oggetto in cui sono contenuti le proprietà e i valori dell'oggetto formattatore di data/ora.|  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato il risultato di passare un oggetto data a `DateTimeFormat` utilizzando impostazioni locali diverse.  
  
```JavaScript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = { weekday: "long", year: "numeric", month: "short",  
    day: "numeric" };  
  
if (console && console.log) {  
    console.log(new Intl.DateTimeFormat("en-US").format(date));  
    // Returns ‎2‎/‎1‎/‎2013  
    console.log(new Intl.DateTimeFormat("ja-JP").format(date));  
    // Returns ‎2013‎年‎2‎月‎1‎日  
    console.log(new Intl.DateTimeFormat("ar-SA", options).format(date));  
    // Returns ‏الجمعة‏, ‏٢٠‏ ‏ربيع الأول‏, ‏١٤٣٤  
    console.log(new Intl.DateTimeFormat("hi-IN", options).format(date));  
    // Returns ‎शुक्रवार‎, ‎01‎ ‎फरवरी‎ ‎2013  
}  
```  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene creato un oggetto `DateTimeFormat` che indica il giorno della settimana corrente nel formato lungo mediante le impostazioni locali di lingua araba (Arabia Saudita), il calendario islamico e il sistema di numerazione latino.  
  
```JavaScript  
var dtf = new Intl.DateTimeFormat(["ar-SA-u-ca-islamic-nu-latn"], {  
    weekday: "long",  
    year: "numeric",  
    day: "numeric",  
    month: "long"  
});   
  
If (console && console.log) {  
    console.log(dtf.format(new Date()));  
    // Returns ‏الجمعة‏, ‏19‏ ‏رمضان‏, ‏1434  
}  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [toLocaleString (Date)](../../javascript/reference/tolocalestring-date.md)   
 [Metodo toLocaleDateString (Date)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)   
 [Metodo toLocaleTimeString (Date)](../../javascript/reference/tolocaletimestring-method-date-javascript.md)   
 [Oggetto intl. Collator](../../javascript/reference/intl-collator-object-javascript.md)   
 [Oggetto Intl.NumberFormat](../../javascript/reference/intl-numberformat-object-javascript.md)