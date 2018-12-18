---
title: "Novità What&#39;s in JavaScript | Microsoft Docs"
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
ms.assetid: 342b68ef-df93-48c4-81de-bdf6b6ce58d9
caps.latest.revision: "33"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 540d10958a7f2d406a6d70a633fc09a2cada8f41
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="what39s-new-in-javascript"></a>Novità What&#39;s in JavaScript
Questo documento elenca le nuove funzionalità di JavaScript supportate sia in [Modalità Edge](http://blogs.msdn.com/b/ie/archive/2014/11/11/living-on-the-edge-our-next-step-in-interoperability.aspx), [!INCLUDE[win8_appname_long](../javascript/includes/win8-appname-long-md.md)] sia nelle app di Windows Phone Store.  
  
 Per sapere quali elementi JavaScript sono supportati in modalità bordo, ma deprecati nelle app di [!INCLUDE[win8_appname_long](../javascript/includes/win8-appname-long-md.md)], vedere [Informazioni sulla versione](../javascript/reference/javascript-version-information.md).  
  
> [!IMPORTANT]
>  Per informazioni su come creare app di [!INCLUDE[win8_appname_long](../javascript/includes/win8-appname-long-md.md)] e Windows Phone Store con JavaScript, incluse informazioni sull'editor JavaScript di Visual Studio e su altre funzionalità, vedere [Sviluppare app di Windows Store con Visual Studio 2013](http://go.microsoft.com/fwlink/p/?LinkID=238263).  
  
## <a name="new-features-in-javascript"></a>Nuove funzionalità di JavaScript  
  
|Funzionalità|Descrizione|  
|-------------|-----------------|  
|Classi|La nuova sintassi supporta la dichiarazione delle [classi](../javascript/reference/class-statement-javascript.md).|  
|Suggerimenti|I [suggerimenti](../javascript/reference/promise-object-javascript.md) consentono una codifica asincrona più semplice e chiara. I costruttori di suggerimenti sono supportati, con i metodi di utilità `all` e `race`.|  
|Iteratori|Ora è possibile scorrere gli oggetti iterabili (tra cui matrici, oggetti di tipo matrice e iteratori), richiamando un hook di iterazione personalizzato con istruzioni da eseguire per il valore di ogni singola proprietà. Per altre informazioni, vedere [Iteratori e Generatori](../javascript/advanced/iterators-and-generators-javascript.md). **Nota:** i generatori non sono ancora supportati.|  
|Funzioni freccia|La funzione freccia (=>) fornisce una sintassi abbreviata per la parola chiave `function` che offre un'associazione `this` lessicale.|  
|Nuovi metodi per gli oggetti predefiniti|Gli oggetti predefiniti [Array](../javascript/reference/array-object-javascript.md), [Math](../javascript/reference/math-object-javascript.md), [Number](../javascript/reference/number-object-javascript.md), [Object](../javascript/reference/object-object-javascript.md) e [String](../javascript/reference/string-object-javascript.md) includono diverse nuove proprietà e funzioni di utilità per la modifica e il controllo dei dati.|  
|Miglioramenti dei valori letterali di oggetto|Gli oggetti ora supportano proprietà calcolate, definizioni di metodo concise e sintassi abbreviata per le proprietà il cui valore viene inizializzato su una variabile con lo stesso nome. Per altre informazioni, vedere [Creazione di oggetti](../javascript/creating-objects-javascript.md).|  
|Proxy|I [proxy](../javascript/reference/proxy-object-javascript.md) abilitano il comportamento personalizzato per gli oggetti.|  
|Parametri rest|I parametri rest consentono di convertire in una matrice gli argomenti consecutivi in una chiamata di funzione. Per altre informazioni, vedere [Funzioni](../javascript/functions-javascript.md).|  
|Operatore spread|L'[operatore spread](../javascript/reference/spread-operator-decrement-dot-dot-dot-javascript.md) (`...`) espande le espressioni iterabili in singoli argomenti. Ad esempio, `a.b(...array)` è quasi come `a.b.apply(a, array)`.|  
|Simboli|Gli oggetti [Symbol](../javascript/reference/symbol-object-javascript.md) consentono di aggiungere proprietà agli oggetti esistenti senza possibilità di interferenza con le proprietà di questi ultimi, senza alcuna visibilità imprevista e senza altre aggiunte non coordinate mediante altro codice.|  
|Stringhe modello|Le [stringhe modello](../javascript/advanced/template-strings-javascript.md) sono valori letterali stringa che consentono di valutare le espressioni e di concatenarle con il valore letterale stringa.|  
|Miglioramenti di Unicode|Sono stati apportati miglioramenti al supporto per Unicode. Ad esempio, un nuovo formato di sequenza di escape supporta i punti di codice "astrali" (punti di codice con più di quattro cifre esadecimali). Per altre informazioni, vedere [Caratteri speciali](../javascript/advanced/special-characters-javascript.md).|  
|WeakSet|Un [WeakSet](../javascript/reference/weakset-object-javascript.md) è una raccolta di oggetti che vengono sottoposti a Garbage Collection se non vi si fa riferimento in nessun altro punto.|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti sul linguaggio JavaScript](../javascript/javascript-language-reference.md)