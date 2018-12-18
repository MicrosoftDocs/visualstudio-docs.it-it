---
title: Prototipi ed ereditarietà del prototipo | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- prototype [JavaScript]
- prototype inheritance [JavaScript]
ms.assetid: 1e1d0631-2a9f-4011-b9fe-fa338e1ef34c
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 200ca757e72b2eec8f09fd48a841cc8eb816c85d
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/10/2018
---
# <a name="prototypes-and-prototype-inheritance"></a>Prototipi ed ereditarietà del prototipo
In JavaScript `prototype` è una proprietà di funzioni e di oggetti creati da funzioni costruttore. Il prototipo di una funzione è un oggetto e viene utilizzato principalmente con una funzione costruttore.  
  
```JavaScript  
function Vehicle(wheels, engine) {  
    this.wheels = wheels;  
    this.engine = engine;  
}  
```  
  
 Nell'esempio precedente il prototipo della funzione `Vehicle` è il prototipo di qualsiasi oggetto di cui viene creata un'istanza con il costruttore `Vehicle`.  
  
## <a name="using-prototypes-to-add-properties-and-methods"></a>Utilizzo di prototipi per l'aggiunta di proprietà e metodi  
 È possibile utilizzare la proprietà `prototype` per aggiungere proprietà e metodi a oggetti, anche a quelli già creati:  
  
```JavaScript  
var testVehicle = new Vehicle(2, false);  
Vehicle.prototype.color = "red";  
var testColor = testVehicle.color;  
```  
  
 Il valore di `testColor` è "red".  
  
 È anche possibile aggiungere proprietà e metodi agli oggetti predefiniti. È possibile ad esempio definire un metodo `Trim` nell'oggetto del prototipo `String` e tutte le stringhe nello script erediteranno il metodo.  
  
```JavaScript  
String.prototype.trim = function()  
{  
    // Replace leading and trailing spaces with the empty string  
    return this.replace(/(^\s*)|(\s*$)/g, "");  
}  
var s = "    leading and trailing spaces    ";  
// Displays "    leading and trailing spaces     (35)"  
window.alert(s + " (" + s.length + ")");  
// Remove the leading and trailing spaces  
s = s.trim();  
// Displays "leading and trailing spaces (27)"  
window.alert(s + " (" + s.length + ")");  
```  
  
### <a name="using-prototypes-to-derive-one-object-from-another-with-objectcreate"></a>Utilizzo di prototipi per derivare un oggetto da un altro con Object.create  

Il prototipo `Object` può essere utilizzato per derivare un oggetto da un altro. È possibile ad esempio usare la funzione [Object.create](../../javascript/reference/object-create-function-javascript.md) per derivare un nuovo oggetto `Bicycle` tramite il prototipo dell'oggetto `Vehicle` definito in precedenza, oltre a tutte le nuove proprietà necessarie.  
  
```JavaScript  
var bicycle = Object.create(Object.getPrototypeOf(Vehicle), {  
    "pedals" :{value: true}  
});  
  
```  
  
 All'oggetto `bicycle` sono associate le proprietà `wheels`, `engine`, `color` e `pedals` e il prototipo relativo è `Vehicle.prototype`. Il motore JavaScript rileva la proprietà `pedals`in `bicycle` e cerca la catena di prototipi per trovare le proprietà `wheels`, `engine` e `color` in `Vehicle`.  
  
### <a name="changing-an-objects-prototype"></a>Modifica del prototipo di un oggetto  
In Internet Explorer 11 è possibile sostituire il prototipo interno di un oggetto o una funzione con un nuovo prototipo tramite la proprietà [__proto__](../../javascript/reference/proto-property-object-javascript.md). Quando si utilizza questa proprietà, si ereditano le proprietà e i metodi del prototipo con altre proprietà e metodi nella catena di prototipi.  

> [!WARNING]
> La proprietà `__proto__` è una funzionalità legacy. Usare invece [Object.getPrototypeOf](../reference/object-getprototypeof-function-javascript.md).
  
Nell'esempio riportato di seguito viene illustrato come modificare il prototipo di un oggetto. In questo esempio viene illustrato come le proprietà ereditate dell'oggetto cambiano quando si modifica il prototipo.  
  
```JavaScript  
function Friend() {  
    this.demeanor = "happy";  
}  
  
function Foe() {  
    this.demeanor = "suspicious";  
}  
  
var friend = new Friend();  
var foe = new Foe();  
  
var player = new Object();  
player.__proto__ = foe;  
  
friend.ally = "Tom";  
  
if (console && console.log) {  
    console.log(player.demeanor === "happy" );      // Returns false  
    console.log(player.demeanor === "suspicious");  // Returns true  
    console.log(player.ally === "Tom");             // Returns false  
    // Turn the foe to a friend.  
    player.__proto__ = friend;  
    console.log(player.demeanor === "happy");       // Returns true  
    console.log(player.demeanor === "suspicious");  // Returns false  
    console.log(player.ally === "Tom");             // Returns true  
}  
```
