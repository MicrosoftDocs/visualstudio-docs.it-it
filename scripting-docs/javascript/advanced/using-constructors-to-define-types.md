---
title: Uso di costruttori per la definizione di tipi | Microsoft Docs
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
- creating objects, constructor functions
- constructor functions
- functions, constructor functions
- objects, creating [JavaScript]
- constructors, creating
ms.assetid: e869702e-4caf-4513-8dd5-fe690535f8aa
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0bff42606fda27e00a537cc227a0b636e016f7c6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="using-constructors-to-define-types"></a>Utilizzo di costruttori per la definizione di tipi
Un costruttore è una funzione che crea un'istanza di un tipo particolare di [oggetto](../../javascript/objects-and-arrays-javascript.md). Un costruttore viene chiamato con la parola chiave **new**. Di seguito vengono forniti alcuni esempi di costruttori con oggetti JavaScript incorporati e oggetti personalizzati.  
  
## <a name="constructor-examples"></a>Esempi di costruttore  
  
```JavaScript  
// Creates a generic object.  
var myObject = new Object();  
// Creates a Date object.  
var myBirthday = new Date(1961, 5, 10);  
// Creates a user defined object.  
var myCar = new Car();  
```  
  
 La funzione costruttore contiene la parola chiave **this**, che è un riferimento a un oggetto vuoto appena creato. Inizializza il nuovo oggetto creando le proprietà e assegnando a queste ultime i valori iniziali. Il costruttore restituisce un riferimento all'oggetto costruito.  
  
## <a name="writing-constructors"></a>Scrittura dei costruttori  
 È possibile creare oggetti usando l'operatore **new** insieme alle funzioni del costruttore predefinite come **Object()**, **Date()**, and **Function()**. È inoltre possibile creare funzioni costruttore personalizzate che definiscono un set di proprietà e metodi. Di seguito è riportato un esempio di un costruttore personalizzato.  
  
```JavaScript  
function Circle (xPoint, yPoint, radius) {  
    this.x = xPoint;  // The x component of the center of the circle.  
    this.y = yPoint;  // The y component of the center of the circle.  
    this.r = radius;  // The radius of the circle.  
}  
```  
  
 Quando si richiama il costruttore Circle, vengono forniti valori per il punto centrale e per il raggio del cerchio. Si termina con un oggetto Circle contenente tre proprietà. Di seguito viene mostrato come creare un'istanza di un oggetto Circle.  
  
```JavaScript  
var aCircle = new Circle(5, 11, 99);  
```  
  
 Il tipo di tutti gli oggetti creati con un costruttore personalizzato è `object`. Esistono solo sei tipi in JavaScript: `object`, `function`, `string`, `number`, `boolean` e `undefined`. Per altre informazioni, vedere [Operatore typeof](../../javascript/reference/typeof-operator-decrementjavascript.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Uso del metodo bind](../../javascript/advanced/using-the-bind-method-javascript.md)