---
title: Metodi Tag HTML (JavaScript) | Documenti Microsoft
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
helpviewer_keywords:
- link method [JavaScript]
- blink method [JavaScript]
- fontsize method [JavaScript]
- italics method [JavaScript]
- sup method [JavaScript]
- anchor method [JavaScript]
- fixed method [JavaScript]
- fontcolor method [JavaScript]
- bold method [JavaScript]
- small method [JavaScript]
- HTML Tag methods [JavaScript]
- sub method [JavaScript]
- big method [JavaScript]
ms.assetid: 50376223-be95-4aa4-9147-9e738a5d3cfa
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7639bc609d8e9b7e4b212fe67ae40f81487d708e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="html-tag-methods-javascript"></a>Metodi tag HTML (JavaScript)
È possibile utilizzare metodi tag HTML per posizionare gli elementi HTML attorno al testo in un `String` oggetto.  
  
## <a name="syntax"></a>Sintassi  
 La tabella seguente elenca la sintassi e una descrizione di ogni metodo di tag HTML.  
  
 Nella colonna sintassi `string1` è un `String` oggetto o un valore letterale.  
  
 Indica la colonna Standard [World Wide Web Consortium (W3C)](http://go.microsoft.com/fwlink/?LinkId=199553) indicazioni per HTML 4. "Sconsigliato" indica che l'elemento HTML è sconsigliato a favore di fogli di stile.  
  
|Sintassi|Descrizione del metodo|Descrizione parametro|Standard|  
|------------|------------------------|---------------------------|--------------|  
|`string1`.Anchor (`name`)|Inserisce un ancoraggio HTML con un attributo NAME intorno al testo.|Il `name` parametro è il testo da inserire nell'attributo NAME dell'ancoraggio HTML.||  
|`string1`.Big()|Codice HTML \<BIG > tag intorno al testo.||Sconsigliata|  
|`string1`.blink()|Codice HTML \<BLINK > tag intorno al testo. Il \<BLINK > tag non è supportato in Internet Explorer.||Non in standard|  
|`string1`.Bold()|Codice HTML \<B > il testo tra i tag.||Sconsigliata|  
|`string1`.fixed()|Codice HTML \<TT > tag intorno al testo.||Sconsigliata|  
|`string1`.fontcolor (`color`)|Codice HTML \<carattere > tag con un attributo COLOR intorno al testo.|Il `color` parametro è un valore stringa che contiene il valore esadecimale o il nome predefinito per un colore. I nomi predefiniti di colore validi dipendono il [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] host browser e la relativa versione.|Deprecato|  
|`string1`.FontSize (`size`)|Codice HTML \<carattere > tag con un attributo di dimensione intorno al testo.|Il `size` parametro è un valore intero che specifica la dimensione del testo. Valori integer validi dipendono il [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] host browser e la relativa versione.|Deprecato|  
|`string1`.italics()|Codice HTML \<I > il testo tra i tag.||Sconsigliata|  
|`string1`. Link (`href`)|Inserisce un ancoraggio HTML che ha un attributo HREF intorno al testo.|Il `href` parametro è il testo da inserire nell'attributo HREF di ancoraggio HTML.||  
|`string1`.Small()|Codice HTML \<SMALL > tag intorno al testo.||Sconsigliata|  
|`string1`.Strike()|Codice HTML \<STRIKE > tag intorno al testo.||Deprecato|  
|`string1`.Sub()|Codice HTML \<SUB > tag intorno al testo.|||  
|`string1`.sup()|Codice HTML \<SUP > tag intorno al testo.|||  
  
## <a name="remarks"></a>Note  
 Per determinare se i tag HTML sono già stati applicati per la stringa viene eseguito alcun controllo.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come utilizzare i metodi di tag HTML.  
  
```JavaScript  
// anchor method.  
var strVariable = "This is an anchor.";  
document.write(strVariable.anchor("Anchor1"));  
// Output: <A NAME="Anchor1">This is an anchor.</A>  
  
// big method.  
var strVariable = "This is a string.";  
document.write(strVariable.big());  
// Output: <BIG>This is a string.</BIG>  
  
//  blink method.  
var strVariable = "This is a string.";  
document.write(strVariable.blink());  
// Output: <BLINK>This is a string.</BLINK>  
  
//  bold method.  
var strVariable = "This is a string.";  
document.write(strVariable.bold());  
// Output: <B>This is a string.</B>  
  
//  fixed method.  
var strVariable = "This is a string.";  
document.write(strVariable.fixed());  
// Output: <TT>This is a string.</TT>  
  
//  fontcolor method.  
var strVariable = "This is a string.";  
document.write(strVariable.fontcolor("red"));  
// Output: <FONT COLOR="red">This is a string.</FONT>  
  
//  fontsize method.  
var strVariable = "This is a string.";  
document.write(strVariable.fontsize(-1));  
// Output: <FONT SIZE="-1">This is a string.</FONT>  
  
//  italics method  
var strVariable = "This is a string.";  
document.write(strVariable.italics());  
// Output: <I>This is a string.</I>  
  
//  link method.  
var strVariable = "This is a hyperlink.";  
document.write(strVariable.link("http://www.microsoft.com"));  
// Output: <A HREF="http://www.microsoft.com">This is a hyperlink.</A>  
  
//  small method.  
var strVariable = "This is a string.";  
document.write(strVariable.small());  
// Output: <SMALL>This is a string.</SMALL>  
  
//  strike method.  
var strVariable = "This is a string.";  
document.write(strVariable.strike());  
// Output: <STRIKE>This is a string.</STRIKE>  
  
//  sub method.  
var strVariable = "This is a string.";  
document.write(strVariable.sub());  
// Output: <SUB>This is a string.</SUB>  
  
//  sup method.  
var strVariable = "This is a string.";  
document.write(strVariable.sup());  
// Output: <SUP>This is a string.</SUP>  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Si applica a**: [oggetto stringa](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto String](../../javascript/reference/string-object-javascript.md)