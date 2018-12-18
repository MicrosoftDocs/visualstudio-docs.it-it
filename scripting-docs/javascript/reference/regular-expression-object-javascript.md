---
title: Oggetto di espressione regolare (JavaScript) | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- RegularExpression_JavaScript
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Regular Expression object
- regular expressions, RegExp object
- RegExp object, overview
ms.assetid: 346aa83e-a045-47ea-acae-b42c7b121534
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: df2d07e3b47e315ec804e5a7f20024dc2184eef0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="regular-expression-object-javascript"></a>Oggetto Regular Expression (JavaScript)
Un oggetto che contiene un modello di espressione regolare e i flag che specificano come applicare il modello.  
  
## <a name="syntax"></a>Sintassi  
  
```  
re = /pattern/[flags]  
```  
  
## <a name="syntax"></a>Sintassi  
  
```  
re = new RegExp("pattern"[,"flags"])   
```  
  
## <a name="parameters"></a>Parametri  
 *Re*  
 Obbligatorio. Il nome della variabile a cui è assegnato il modello di espressione regolare.  
  
 *modello*  
 Obbligatorio. Il modello di espressione regolare da usare. Se si usa la sintassi 1, delimitare il modello con i caratteri "/". Se si usa la sintassi 2, racchiudere il modello tra virgolette.  
  
 `flags`  
 Parametro facoltativo. Racchiudere il flag tra virgolette se si usa la sintassi 2. I flag disponibili, che possono essere combinati, sono:  
  
-   g (ricerca globale per tutte le occorrenze di *modello*)  
  
-   i (ignora maiuscole/minuscole)  
  
-   m (ricerca su più righe)  
  
-   u (unicode), Abilita EcmaScript 6 [funzionalità Unicode](../../javascript/advanced/special-characters-javascript.md). Supportato solo in [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)].  
  
-   y (corrispondenza temporanea), ricerca le corrispondenze nella proprietà `lastIndex` dell'espressione regolare (e non esegue la ricerca negli indici successivi). Supportato in [!INCLUDE[jsv12textExp](../../javascript/includes/jsv12textexp-md.md)].  
  
## <a name="remarks"></a>Note  
 Il **espressione regolare** oggetto non deve essere confuso con globale `RegExp` oggetto. Anche se sembrano uguali, sono distinti e separati. Le proprietà del **espressione regolare** contengono solo informazioni su una particolare **espressione regolare** istanza, mentre le proprietà dell'oggetto globale `RegExp` oggetto contiene Quando si verifica, aggiornato continuamente informazioni su ogni corrispondenza.  
  
 **Espressione regolare** oggetti archiviano i criteri usati nella ricerca di stringhe per le combinazioni di caratteri. Dopo il **espressione regolare** oggetto viene creato, viene passato a un metodo di stringa o una stringa viene passata a uno dei metodi delle espressioni regolari. Le informazioni sull'ultima ricerca eseguita vengono archiviate nell'oggetto globale `RegExp`.  
  
 Usare la sintassi 1 quando si conosce in anticipo la stringa di ricerca. Usare la sintassi 2 quando la stringa di ricerca cambia di frequente oppure è sconosciuta, come nel caso di stringhe ricavate dall'input dell'utente.  
  
 Il *modello* argomento, viene compilato in un formato interno prima dell'uso. Per la sintassi 1, *modello* viene compilato al caricamento dello script. Sintassi 2, *modello* viene compilato immediatamente prima di utilizzare, o quando il **compilare** metodo viene chiamato.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del **espressione regolare** creando un oggetto (re) contenente un criterio di espressione regolare con i flag associati. In questo caso, il valore risultante **espressione regolare** oggetto viene quindi utilizzato il `match` metodo:  
  
```JavaScript  
var s = "through the pages of the book";  
  
// Create regular expression pattern.  
var re = new RegExp("the", "i");  
  
// Attempt match on search string.  
var r = s.match(re);     
  
// Return first occurrence of "the".  
if(console && console.log) {  
    console.log(r);  
}  
  
// Output:  
//   
```  
  
## <a name="example"></a>Esempio  
 L'esempio seguente aggiorna il modello di espressione regolare per la ricerca di più istanze.  
  
```JavaScript  
// Create regular expression pattern using the i and g flags.  
var re = new RegExp("the", "ig");  
  
// Attempt match on search string.  
var r = s.match(re);     
  
// Return the two occurrences of "the".  
if(console && console.log) {  
    console.log(r.length);  
    console.log(r);  
}  
  
// Output:  
// 2  
// [object Array] ["the", "the"]  
```  
  
## <a name="example"></a>Esempio  
 Quando si usa il flag /y, se viene trovata una corrispondenza, aggiorna `lastindex` all'indice del carattere successivo dopo l'ultima corrispondenza. Se la corrispondenza non viene trovata, reimposta `lastindex` su 0.  
  
 L'esempio seguente cerca una corrispondenza in un indice specifico usando il flag /y e la proprietà `lastIndex`.  
  
```JavaScript  
// Create regular expression pattern using the i and y flags.  
var re = new RegExp("the", "iy");  
  
// Set the lastIndex property and attempt a match  
// at the specified index.  
re.lastIndex = 20;  
var r = s.match(re);     
  
// No matches returned.  
if(console && console.log) {  
    console.log(r);  
}  
// Reset the lastIndex property and attempt a match.  
re.lastIndex = 21;  
var r = s.match(re);  
  
// Return occurrence of "the" starting at index 21.  
if(console && console.log) {  
    console.log(r);  
}  
  
// Output:  
// null  
// [object Array] ["the"]  
```  
  
<a name="js56jsobjregexpressionprop"></a>   
## <a name="properties"></a>Proprietà  
 [Proprietà globale](../../javascript/reference/global-property-regular-expression-javascript.md) &#124; [proprietà ignoreCase](../../javascript/reference/ignorecase-property-regular-expression-javascript.md) &#124; [proprietà multiline](../../javascript/reference/multiline-property-regular-expression-javascript.md) &#124; [proprietà source](../../javascript/reference/source-property-regular-expression-javascript.md)  
  
<a name="js56jsobjregexpressionmeth"></a>   
## <a name="methods"></a>Metodi  
 [Metodo Compile](../../javascript/reference/compile-method-regular-expression-javascript.md) &#124; [metodo exec](../../javascript/reference/exec-method-regular-expression-javascript.md) &#124; [metodo di test](../../javascript/reference/test-method-regular-expression-javascript.md)  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 Il flag u è supportato in [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)].  
  
 Il flag y è supportato in [!INCLUDE[jsv12textExp](../../javascript/includes/jsv12textexp-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [RegExp (oggetto)](../../javascript/reference/regexp-object-javascript.md)   
 [Sintassi di espressione regolare (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [Oggetto String](../../javascript/reference/string-object-javascript.md)