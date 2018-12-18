---
title: Oggetto intl. Collator (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Collator
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: acbb9461-f956-4b5b-ae5f-6a47815ae15c
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b9a41507face20285124257be95197ef5ea53ef6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="intlcollator-object-javascript"></a>Oggetto Intl.Collator (JavaScript)
Fornisce confronti di stringhe specifici delle impostazioni locali.  
  
## <a name="syntax"></a>Sintassi  
  
```  
collatorObj = new Intl.Collator([locales][, options])  
```  
  
#### <a name="parameters"></a>Parametri  
 `collatorObj`  
 Obbligatorio. Il nome della variabile a cui assegnare l'oggetto `Collator`.  
  
 `locales`  
 Parametro facoltativo. Una matrice di stringhe delle impostazioni locali che contengono uno o più linguaggi o tag per le impostazioni locali. Se si include più di una stringa delle impostazioni locali, elencarle in ordine decrescente di priorità in modo che la prima voce siano le impostazioni locali desiderate. Se si omette questo parametro, le impostazioni locali predefinite del runtime JavaScript vengono utilizzate. Per altre informazioni, vedere la sezione Osservazioni.  
  
 `options`  
 Parametro facoltativo. Oggetto che contiene una o più proprietà che specificano opzioni di formattazione per la data e l'ora. Per informazioni dettagliate, vedere la sezione Osservazioni.  
  
## <a name="remarks"></a>Note  
 Il `locales` parametro deve essere conforme alle [BCP 47](http://tools.ietf.org/html/rfc5646) tag di lingua e impostazioni locali, ad esempio "en-US" e "Hans-zh-CN". Il tag può includere il linguaggio, l'area, il paese e il variant. Per un elenco di lingue, vedere il [registro sottotag di linguaggio IANA](http://go.microsoft.com/fwlink/p/?linkid=227303). Per esempi di tag di linguaggio, vedere [appendice](http://tools.ietf.org/html/rfc5646#appendix-A) di BCP 47. Per `Collator`, è possibile includere l'estensione -u nella stringa di impostazioni locali per specificare uno o più delle estensioni Unicode seguenti:  
  
-   co - per specificare le regole di confronto di variant (specifiche delle impostazioni locali): "*language*-*area*-u-co -*valore*".  
  
-   -kn per specificare un confronto numerico: "*language*-*area*- u-kn-true &#124; false".  
  
-   -kf per specificare se ordinare i caratteri maiuscoli o minuscoli prima: "*language*-*area*- u-kf-superiore &#124; inferiore &#124; false"). Questa estensione non è attualmente supportata.  
  
 Per specificare un confronto numerico, è possibile impostare l'estensione -kn nella stringa delle impostazioni locali o usare il `numeric` proprietà il `options` parametro. Se si usa il `numeric` proprietà, il valore di -kn non verrà applicate.  
  
 Il parametro `options` può includere le seguenti proprietà:  
  
-   `localeMatcher`. Specifica l'algoritmo di corrispondenza delle impostazioni locali da utilizzare. I valori possibili sono "ricerca" e "adatta". Il valore predefinito è "migliore".  
  
-   `usage`. Specifica se l'obiettivo di confronto è ordinamento o la ricerca. I valori possibili sono "ordinamento" e "Cerca". Il valore predefinito è "ordinamento".  
  
-   `sensitivity`. Specifica la sensibilità dell'utilità di confronto. I valori possibili sono "base", "accento", "casi" e "variant". Il valore predefinito è `undefined`.  
  
-   `ignorePunctuation`. Specifica se la punteggiatura viene ignorata nel confronto. I valori possibili sono "true" e "false". Il valore predefinito è `false`.  
  
-   `numeric`. Specifica se viene utilizzato un ordinamento numerico. I valori possibili sono "true" e "false". Il valore predefinito è `false`.  
  
-   `caseFirst`. Non è attualmente supportato.  
  
## <a name="properties"></a>Proprietà  
 Nella tabella seguente sono elencate le proprietà dell'oggetto `Collator`.  
  
|||  
|-|-|  
|Proprietà|Descrizione|  
|[compare](../../javascript/reference/compare-property-intl-collator.md)|Restituisce una funzione che confronta due stringhe utilizzando di ordinamento dell'utilità di confronto.|  
|[costruttore](../../javascript/reference/constructor-property-intl-collator.md)|Specifica la funzione che crea un'utilità di confronto.|  
|[prototipo](../../javascript/reference/prototype-property-intl-collator.md)|Restituisce un riferimento al prototipo per un'utilità di confronto.|  
  
## <a name="methods"></a>Metodi  
 Nella tabella seguente sono elencati i metodi dell'oggetto `Collator`:  
  
|||  
|-|-|  
|Metodo|Descrizione|  
|[resolvedOptions](../../javascript/reference/resolvedoptions-method-intl-collator.md)|Restituisce un oggetto che contiene le proprietà e i valori dell'utilità di confronto.|  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene creato un `Collator` oggetto ed esegue un confronto.  
  
```JavaScript  
var co = new Intl.Collator(["de-DE"]);  
co.compare("a", "b"); // Returns -1  
  
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
 Nell'esempio seguente viene utilizzato un `Collator` dell'oggetto per cercare una stringa e specifica le opzioni di confronto.  
  
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
 [Metodo localeCompare (String)](../../javascript/reference/localecompare-method-string-javascript.md)   
 [Oggetto intl. DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md)   
 [Oggetto Intl.NumberFormat](../../javascript/reference/intl-numberformat-object-javascript.md)