---
title: Gestione di listener di eventi | Microsoft Docs
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
ms.assetid: 87717f5d-b0c6-4c8d-a293-476002b7bfcf
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6a97c579716b9964b8dfb93db419e9a70160d33a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="managing-event-listeners"></a>Gestione di listener di eventi
Se la durata dell'oggetto o dell'elemento DOM è diversa da quella del listener di eventi associato, può essere necessario usare il metodo [removeEventListener](http://msdn.microsoft.com/library/ie/ff975250\(v=vs.85\).aspx) per evitare perdite di memoria.  
  
## <a name="event-listeners-and-object-scope"></a>Listener di eventi e ambito di oggetto  
 L'esempio seguente visualizza un codice che potrebbe produrre una perdita di memoria se viene chiamata la funzione `dataObjFactory()`. In questo codice viene registrato un listener di eventi per un oggetto dati ogni volta che viene creato un nuovo oggetto dati. Per rendere disponibile l'oggetto dati corrente nel gestore eventi `dataReady()`, viene usato il [metodo Bind (Function)](../../javascript/reference/bind-method-function-javascript.md) in `addEventListener`.  
  
```JavaScript  
 var data;  
 var dataObj;  
  
 var dataReadyEvent = document.createEvent("Event");  
 dataReadyEvent.initEvent("dataReady", true, false);  
  
 function DataObject() {  
  
     this.name = "Data Object";  
     this.data = function () {  
         return data;  
     }  
     this.onDataCompleted = dataReady;  
     // this.handlerRef = this.onDataCompleted.bind(this);  
  
     // document.addEventListener('dataReady', this.handlerRef);  
     document.addEventListener('dataReady', this.onDataCompleted.bind(this));  
 }  
  
 // Runs when the data is available.  
 function dataReady() {  
     if (console && console.log) {  
         console.log("object value: " + this.name);  
         console.log("object value: " + this.data());  
     }  
 }  
  
setTimeout(function () {  
    // Generate data after a timeout period.  
    data = [0, 1, 2, 3];  
    document.dispatchEvent(dataReadyEvent);  
}, 10000);  
  
function dataObjFactory() {  
     for (var x = 0; x < 100; x++) {  
         if (dataObj) {  
             // The following line of code has no effect.  
             document.removeEventListener('dataReady', dataObj.onDataCompleted);  
             dataObj = null;  
         }  
         dataObj = new DataObject();  
     }  
 }  
  
 dataObjFactory();  
```  
  
 Il listener per ciascun oggetto dati viene registrato con l'oggetto `document`, che ha una durata diversa rispetto agli oggetti dati. Il listener di eventi registrato per ciascun oggetto dati impedisce che venga sottoposto a Garbage Collection finché l'oggetto `document` resta nell'ambito. In alcuni modelli di progettazione moderni JavaScript, l'oggetto document resta nell'ambito per tutta la durata dell'applicazione Web. Per prevenire una perdita di memoria, `removeEventListener` viene chiamato nella funzione `dataObjFactory`. Questo codice tuttavia non riesce perché `removeEventListener` non è stato chiamato nella versione associata del gestore eventi restituita dalla funzione `bind`.  
  
 Per correggere il codice e rendere disponibili gli oggetti dati per la Garbage Collection, è necessario archiviare un riferimento alla versione associata del gestore eventi, come mostrato nel codice, quindi passare il riferimento archiviato a `addEventListener`. Il codice corretto per `DataObject` è:  
  
```JavaScript  
function DataObject() {  
  
    this.name = "Data Object";  
    this.data = function () {  
        return data;  
    }  
    this.onDataCompleted = dataReady;  
    this.handlerRef = this.onDataCompleted.bind(this);  
  
    document.addEventListener('dataReady', this.handlerRef);  
    // document.addEventListener('dataReady', this.onDataCompleted.bind(this));  
}  
  
```  
  
 Infine, è necessario chiamare `removeEventListener` nel riferimento archiviato (`handlerRef`) della funzione associata. Il codice corretto per `dataObjFactory` è:  
  
```JavaScript  
function dataObjFactory() {  
     for (var x = 0; x < 100; x++) {  
         if (dataObj) {  
             document.removeEventListener('dataReady', dataObj.handlerRef);  
         }  
         dataObj = new DataObject();  
     }  
 }  
  
```  
  
 Ora la chiamata a `removeEventListener` risulta funzionante e gli oggetti dati non necessari possono essere sottoposti a Garbage Collection anche se l'oggetto `document` resta nell'ambito.