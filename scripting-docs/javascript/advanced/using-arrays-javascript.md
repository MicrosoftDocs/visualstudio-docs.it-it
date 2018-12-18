---
title: Utilizzo di matrici JavaScript | Microsoft Docs
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
- arrays [JavaScript]
- arrays [JavaScript], objects
ms.assetid: 785c5acd-b8b3-4152-af9a-dd42ecdd75ba
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4c5218a8353a796128d8b672ecc781665c6bde20
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="using-arrays-javascript"></a>Utilizzo di matrici (JavaScript)
Le matrici presenti in [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] sono *sparse*. Ovvero, se si dispone di una matrice con tre elementi che sono numerati 0, 1 e 2, è possibile creare l'elemento 50 senza doversi preoccupare di elementi compresi tra 3 e 49. Se la matrice ha una variabile di lunghezza automatica (vedere [Oggetti intrinseci](../../javascript/intrinsic-objects-javascript.md) per una spiegazione del monitoraggio automatico della lunghezza della matrice), la variabile di lunghezza viene impostata a 51, anziché a 4. È possibile creare matrici in cui non siano presenti interruzioni della numerazione degli elementi, ma non è necessario eseguire questa operazione.  
  
 In [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], oggetti e matrici sono quasi identici tra loro. Le due principali differenze sono che gli oggetti non-matrice non dispongono di una proprietà di lunghezza automatica, e le matrici non dispongono di proprietà e metodi di un oggetto.  
  
## <a name="addressing-arrays"></a>Indirizzamento di matrici  
 Si indirizzano le matrici tramite parentesi quadre ([]), come illustrato nell'esempio seguente. Le parentesi quadre racchiudono un valore numerico o un'espressione che viene valutata come un numero intero.  
  
```JavaScript  
var entryNum = 5;  
  
sample = new Array();  
  
sample[1] = "Maple Street";  
sample[entryNum] = 25;  
  
document.write (sample[1]);  
document.write (" ");  
document.write (sample[entryNum]);  
  
// Output: Maple Street 25  
  
```  
  
## <a name="objects-as-associative-arrays"></a>Oggetti come matrici associative  
 In genere si usa l'operatore punto "." per accedere alle proprietà di un oggetto. Di seguito è riportato un esempio:  
  
```JavaScript  
myObject.aProperty  
```  
  
 In questo caso, il nome della proprietà è un identificatore. È anche possibile accedere alle proprietà di un oggetto tramite l'operatore di indice ([]). In questo caso si tratta l'oggetto come una *matrice associativa* nella quale i valori dei dati sono associati alle stringhe. Di seguito è riportato un esempio:  
  
```JavaScript  
myObject["aProperty"] // Same as above.  
```  
  
 L'operatore dell'indice è più comunemente associato all'accesso agli elementi della matrice. Quando viene usato con gli oggetti, l'indice è una stringa letterale che rappresenta il nome della proprietà.  
  
 Notare le differenze principali tra le due modalità di accesso alle proprietà dell'oggetto.  
  
1.  Un nome di proprietà trattato come un identificatore (la sintassi dell'operatore punto (.)) non può essere modificato come accade per i dati.  
  
2.  Un nome di proprietà trattato come un indice (la sintassi parentesi quadre([]) non può essere modificato come accade per i dati.  
  
 Questa differenza risulta utile quando non si conoscono i nomi della proprietà fino al runtime (ad esempio, durante la creazione di oggetti basati sull'input dell'utente). Per estrarre tutte le proprietà da una matrice associativa, è necessario usare il ciclo `for...in`.