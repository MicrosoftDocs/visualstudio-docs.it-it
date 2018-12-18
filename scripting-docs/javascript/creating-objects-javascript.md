---
title: Creazione di oggetti (JavaScript) | Microsoft Docs
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
- constructors, including properties and methods
- function constructor
- creating objects, constructor functions
- constructor functions
- prototype objects
- creating objects
- custom objects, creating
- creating objects, about creating objects
- objects, creating [JavaScript]
- creating objects, prototypes
- custom objects
- initializing objects, using constructors
ms.assetid: 58d1baa5-4fe8-4a56-a926-5b11765df704
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0ba7962179cc2f0fcb972caee692edabee368c7d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="creating-objects-javascript"></a>Creazione di oggetti (JavaScript)
Esistono diversi modi per creare oggetti personalizzati in JavaScript. È possibile creare direttamente un'istanza di un [Oggetto Oggetto](../javascript/reference/object-object-javascript.md), quindi aggiungere le proprie proprietà e metodi. In alternativa, è possibile usare un'annotazione letterale di oggetto per definire l'oggetto. È anche possibile usare una funzione del costruttore per definire un oggetto. Per altre informazioni sull'uso delle funzioni del costruttore, vedere [Uso di costruttori per la definizione di tipi](../javascript/advanced/using-constructors-to-define-types.md).  
  
## <a name="example"></a>Esempio  
 Il codice seguente mostra come creare un'istanza di un oggetto e come aggiungere alcune proprietà. In questo caso, solo l'oggetto `pasta` ha proprietà `grain`, `width` e `shape`.  
  
```JavaScript  
const pasta = new Object();  
pasta.grain = "wheat";  
pasta.width = 0.5;  
pasta.shape = "round";  
pasta.getShape = function() {   
    return this.shape;   
};  
document.write(pasta.grain);  
document.write("<br/>");  
document.write(pasta.getShape());  
  
// Output:  
// wheat  
// round  
  
```  
  
## <a name="object-literals"></a>Valori letterali di oggetto  
 È anche possibile usare un'annotazione del valore letterale di oggetto per creare una sola istanza di un oggetto. Il codice seguente mostra come creare un'istanza di un oggetto usando un'annotazione del valore letterale di oggetto.  
  
```JavaScript  
const pasta = {  
    grain: "wheat",  
    width: 0.5,  
    shape: "round"  
};  
```  
  
 È anche possibile usare un valore letterale di oggetto in un costruttore.  
  
> [!CAUTION]
>  Le funzionalità descritte di seguito sono supportate solo in [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)].  
  
 In [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)] è possibile usare la sintassi abbreviata per creare un valore letterale dell'oggetto.  
  
```JavaScript  
const key = 'a';  
const value = 5;  
  
// Older version  
const obj1 = {  
    key: key,  
    value: value  
};  
  
// Edge mode  
const obj2 = {key, value};  
  
console.log(obj2);  
  
// Output:  
// [object Object] {key: "a", value: 5}  
```  
  
 L'esempio seguente mostra l'uso della sintassi abbreviata per definire i metodi nei valori letterali di oggetto.  
  
```JavaScript  
// Older versions  
const obj = {  
    method1: function() {},  
    method2: function() {}  
};  
  
// Edge mode  
const obj = {  
    method1() {},  
    method2() {}  
};  
```  
  
 È anche possibile impostare dinamicamente i nomi delle proprietà nei valori letterali dell'oggetto in [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)]. L'esempio di codice seguente crea dinamicamente un nome della proprietà per un oggetto usando la sintassi set.  
  
```JavaScript  
const propName = "prop_42";  
  
const obj = {  
    value: 0,  
    set [propName](v) {  
        this.value = v;  
    }  
}  
  
console.log(obj.value);  
// Runs the setter property.  
obj.prop_42 = 777;  
console.log(obj.value);  
  
// Output:  
// 0  
// 777  
  
```  
  
 L'esempio di codice seguente crea dinamicamente un nome della proprietà per un oggetto usando la sintassi get.  
  
```JavaScript  
const propName = "prop_42";  
  
const obj = {  
    get [propName]() {  
        return 777;  
    }  
}  
  
console.log(obj.prop_42);  
  
// Output:  
// 777  
```  
  
 L'esempio di codice seguente crea una proprietà calcolata usando la [sintassi della funzione freccia](../javascript/functions-javascript.md) per aggiungere 42 al nome della proprietà.  
  
```JavaScript  
const obj = {  
    [ 'prop_' + (() => 42)() ]: 42  
};  
```
