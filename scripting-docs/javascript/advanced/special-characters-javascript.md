---
title: Caratteri speciali (JavaScript) | Microsoft Docs
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
- line terminator character
- white space character
- Unicode character
- escape sequence
- backslash (\)
ms.assetid: 3b38b1bd-1f0f-4748-b13e-55cab36fd126
caps.latest.revision: "31"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0eaae8dfc84d9a3be6db54c50558d4cf675a53a8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="special-characters-javascript"></a>Caratteri speciali (JavaScript)
In [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] sono disponibili sequenze di escape che possono essere incluse nelle stringhe per creare caratteri che non è possibile digitare direttamente.  
  
## <a name="remarks"></a>Note  
 Un valore stringa è una serie di zero o più caratteri Unicode (lettere, cifre e altri caratteri). I valori letterali stringa sono racchiusi in coppie corrispondenti di virgolette singole o doppie. Le virgolette doppie possono essere contenute in una stringa racchiusa tra virgolette singole. Le virgolette singole possono essere contenute in una stringa racchiusa tra virgolette doppie.  
  
 Ogni carattere in un valore letterale stringa può essere rappresentato da una sequenza di escape. Una sequenza di escape inizia con una barra rovesciata(\\) per indicare all'interprete [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] che il carattere successivo è un carattere speciale.  
  
 È possibile specificare un carattere Unicode usando la sequenza di escape \u*hhhh* dove *hhhh* è un numero esadecimale di quattro cifre. Una sequenza di escape Unicode può rappresentare qualsiasi carattere a 16 bit. Per altre informazioni, vedere [Sequenze di escape di punti di codice Unicode](#CodePoint).  
  
 Per alcuni caratteri, è possibile usare una sequenza di escape di un solo carattere. Ad esempio, \t specifica un carattere di tabulazione.  
  
## <a name="escape-sequences"></a>Sequenze di escape  
 La tabella seguente elenca alcuni esempi di sequenze di escape per caratteri comuni.  
  
|Valore del carattere Unicode|Sequenza di escape|Significato|Categoria|  
|-----------------------------|---------------------|-------------|--------------|  
|\u0008|\b|Backspace||  
|\u0009|\t|Scheda|Spazio vuoto|  
|\u000A|\n|Avanzamento riga (nuova riga)|Terminatore di riga|  
|\u000B|\v<br /><br /> (Vedere la nota dopo questa tabella.)|Tabulazione verticale|Spazio vuoto|  
|\u000C|\f|Avanzamento carta|Spazio vuoto|  
|\u000D|\r|Ritorno a capo|Terminatore di riga|  
|\u0020||Spazio|Spazio vuoto|  
|\u0022|\\"|Virgolette doppie (")||  
|\u0027|\\'|Virgoletta singola (')||  
|\u005C|\\\|Barra rovesciata (\\)||  
|\u00A0||Spazio unificatore|Spazio vuoto|  
|\u2028||Separatore di riga|Terminatore di riga|  
|\u2029||Separatore di paragrafo |Terminatore di riga|  
|\uFEFF||Indicatore dell'ordine dei byte|Spazio vuoto|  
  
 La colonna Categoria specifica se il carattere è uno spazio vuoto o un carattere terminatore di riga. Il [metodo trim (Stringa)](../../javascript/reference/trim-method-string-javascript.md) rimuove gli spazi iniziali e finali e i caratteri di terminazione di riga da una stringa.  
  
 La stessa barra rovesciata viene usata come carattere di escape. Di conseguenza, non è possibile digitarla direttamente nello script. Per scrivere una barra rovesciata, è necessario digitarne due consecutive (\\\\).  
  
> [!NOTE]
>  A partire da [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)], non è possibile identificare il browser come Internet Explorer effettuando il test per l'equivalenza della tabulazione verticale (\v) e di "v". Nelle versioni precedenti, l'espressione `"\v" === "v"` restituisce `true`. In [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)] l'espressione restituisce `false`.  
  
## <a name="example"></a>Esempio  
  
### <a name="description"></a>Descrizione  
 L'esempio seguente illustra le sequenze di escape \\\ e \\'.  
  
### <a name="code"></a>Codice  
  
```JavaScript  
document.write('The image path is C:\\webstuff\\mypage\\gifs\\garden.gif.');  
document.write ("<br />");  
document.write('The caption reads, "After the snow of \'97. Grandma\'s house is covered."');  
```  
  
<a name="CodePoint"></a>   
## <a name="unicode-code-point-escape-sequences"></a>Sequenze di escape di punti di codice Unicode  
 In [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)] il formato Unicode è completamente supportato. I punti di codice Unicode più comuni sono rappresentati da quattro cifre esadecimali, ad esempio /u0009 per un carattere di tabulazione. I punti di codice "astrali", che includono tutti i simboli che richiedono più di quattro cifre esadecimali, sono supportati in un formato semplificato. Usando il formato "\u{*punto di codice*}", è possibile rappresentare l'intero set di caratteri Unicode in formato letterale. Per rappresentare il simbolo "𠮷", ad esempio, è possibile usare il formato seguente: "\u{20BB7}".  
  
 Nell'esempio di codice seguente le stringhe sono tutte equivalenti. \uD842\uDFB7 è il metodo alternativo per specificare questo simbolo nelle versioni precedenti.  
  
```JavaScript  
"\u{20BB7}"=="𠮷"=="\uD842\uDFB7"  
```  
  
 RegExp ora include un flag /u che abilita il supporto completo per i punti di codice astrali. Nell'esempio di codice seguente il flag/u nell'espressione regolare abilita la corrispondenza dei punti di codice astrali (il punto corrisponde a qualsiasi carattere nelle stringa fornita).  
  
```JavaScript  
"𠮷".match(/./u)[0].length == 2  
```  
  
 Il flag /u abilita l'analisi del nuovo formato, \u{puntodicodice}), come una sequenza di escape Unicode. Ciò è necessario perché \u{xxxxx} senza il flag /u ha un significato diverso in un'espressione regolare.  
  
> [!NOTE]
>  Per i punti di codice astrali la lunghezza è sempre 2 e corrisponde al comportamento nelle versioni precedenti.  
  
 Per supportare i punti ti codice astrali, l'oggetto String include ora due nuovi metodi, String.codePointAt e String.fromCodePoint. Ad esempio, è possibile usare codePointAt per restituire il punto di codice equivalente per il simbolo "𠮷".  
  
```JavaScript  
"𠮷".codePointAt(0) == 0x20BB7  
  
```  
  
 È anche possibile eseguire l'iterazione dei punti di codice usando l'istruzione `for...of`.  
  
```JavaScript  
for(var c of "𠮷") {  
    console.log(c);  
}  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione String.fromCharCode](../../javascript/reference/string-fromcharcode-function-javascript.md)