---
title: Precedenza tra gli operatori (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- operator precedence
- order of precedence
ms.assetid: cf3c510a-2214-4b47-b8fe-3521298efaab
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 82503a312a4a4996e3bd38f596eef3104af3f11b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="operator-precedence-javascript"></a>Precedenza tra gli operatori (JavaScript)
La precedenza tra gli operatori indica l'ordine di esecuzione delle operazioni quando viene valutata un'espressione. Le operazioni con precedenza maggiore vengono eseguite prima di quelle con precedenza minore. La moltiplicazione viene ad esempio eseguita prima dell'addizione.  
  
## <a name="includejavascriptjavascriptincludesjavascript-mdmd-operators"></a>Operatori [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]  
 Nella tabella seguente sono elencati gli operatori [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] nell'ordine di precedenza dalla più elevata alla più bassa. Gli operatori con la stessa precedenza vengono valutati da sinistra a destra.  
  
|Operatore|Descrizione|  
|--------------|-----------------|  
|. [ ] ( )|Accesso a campi, indicizzazione di matrici, chiamate di funzioni e raggruppamento di espressioni|  
|++ -- - ~ ! delete new typeof void|Operatori unari, tipo di dati restituito, creazione di oggetti, valori non definiti|  
|* / %|Moltiplicazione, divisione, divisione di modulo|  
|+ - +|Addizione, sottrazione, concatenazione di stringhe|  
|<\< >> >>>|Spostamento per bit|  
|< \<= > >= instanceof|Minore di, minore o uguale a, maggiore di, maggiore o uguale a instanceof|  
|== != === !==|Uguaglianza, disuguaglianza, identità e non identità|  
|&|AND bit per bit|  
|^|XOR bit per bit|  
|&#124;|OR bit per bit|  
|&&|AND logico|  
|&#124;&#124;|OR logico|  
|?:|Condizionale|  
|= *OP*=|Assegnazione, assegnazione con operazione (come += e &=)|  
|,|Valutazione multipla|  
  
 Le parentesi consentono di modificare l'ordine di valutazione determinato dalla precedenza tra gli operatori. L'espressione racchiusa tra parentesi viene quindi valutata prima che il relativo valore venga utilizzato nel resto dell'espressione.  
  
 Ad esempio:  
  
```JavaScript  
var result = 78 * 96 + 3;  
document.write(result);  
document.write("<br/>");  
  
result = 78 * (9 + 3);  
document.write(result);  
  
// Output:  
// 7491  
// 936  
```  
  
 Nella prima espressione sono presenti tre operatori: =, *, and +. In base alle regole di precedenza, tali operatori verranno valutati nel seguente ordine: \*, +, = (78 \* 96 = 7488, 7488 + 3 = 7491).  
  
 Nella seconda espressione l'operatore ( ) viene valutato per primo, di conseguenza l'espressione di addizione viene calcolata prima della moltiplicazione (9 + 3 = 12, 12 * 78 = 936).  
  
 Nell'esempio seguente viene illustrata un'istruzione che include vari operatori e viene risolta in `true`.  
  
```JavaScript  
var num = 10;  
  
if(5 == num / 2 && (2 + 2 * num).toString() === "22") {  
    document.write(true);  
}  
    // Output:  
    // true  
```  
  
 Gli operatori vengono valutati nell'ordine seguente: ( ) per il raggruppamento, *, + (nel raggruppamento), "." per la funzione, ( ) per la funzione, /, ==, === e &&.