---
title: Uso di metodi asincroni di Windows Runtime | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JavaScript, Windows Runtime asynchronous methods
ms.assetid: 70756833-44f7-4383-827f-2ac781558082
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 215a04a2f3f875743a7fbf910a3a565cf34fb558
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="using-windows-runtime-asynchronous-methods"></a>Uso di metodi asincroni di Windows Runtime
Molti metodi di Windows Runtime, in particolari i metodi il cui completamento richiede molto tempo, sono asincroni. Questi metodi restituiscono in genere un'azione o un'operazione asincrona, ad esempio, `Windows.Foundation.IAsyncAction`, `Windows.Foundation.IAsyncOperation`, `Windows.Foundation.IAsyncActionWithProgress` o `Windows.Foundation.IAsyncOperationWithProgress`. Questi metodi sono rappresentati in JavaScript con il modello [CommonJS/Promises/A](http://go.microsoft.com/fwlink/p/?LinkId=244434). Restituiscono quindi un oggetto Promise che include una funzione [quindi](https://msdn.microsoft.com/en-us/library/windows/apps/br229728.aspx), per cui è necessario fornire una funzione `completed` che gestisce il risultato in caso di esito positivo dell'operazione. Se non si vuole fornire alcun gestore degli errori, è consigliabile usare la funzione [fatto](https://msdn.microsoft.com/en-us/library/windows/apps/hh701079.aspx) invece della funzione `then`.  
  
> [!IMPORTANT]
>  Le funzionalità di Windows Runtime non sono disponibili per app eseguite in Internet Explorer.  
  
## <a name="examples-of-asynchronous-methods"></a>Esempi di metodi asincroni  
 Nell'esempio seguente la funzione `then` accetta un parametro che rappresenta il valore completo del metodo `createResourceAsync`.  
  
```JavaScript  
client.createResourceAsync(uri, description, item)  
    // Success.  
    .then(function(newItem) {   
        console.log("New item is: " + newItem.id);  
            });  
```  
  
 In questo caso, se il metodo `createResourceAsync` ha esito negativo, restituisce una promessa nello stato di errore, ma non genera eccezioni. È possibile gestire un errore usando la funzione `then` come indicato di seguito.  
  
```JavaScript  
client.createResourceAsync(uri, description, item)  
    // Success.  
    .then(function(newItem) {   
              console.log("New item is: " + newItem.id);  
          }  
          function(err) {  
              console.log("Got error: " + err.message);  
          });  
```  
  
 Se non si vuole gestire l'errore in modo esplicito, ma si vuole che generi un'eccezione, è possibile usare invece la funzione `done`.  
  
```JavaScript  
client.createResourceAsync(uri, description, item)  
    // Success.  
      .done(function(newItem) {   
               console.log("New item is: " + newItem.id);  
            });  
```  
  
 È anche possibile visualizzare lo stato relativo al completamento usando una terza funzione.  
  
```JavaScript  
client.createResourceAsync(uri, description, item)  
    // Success.  
      .then(function(newItem) {   
               console.log("New item is: " + newItem.id);  
            },  
    // Error.  
            function(error) {   
               alert("Failed to create a resource.");  
            },  
    // Progress.  
            function(progress, resultSoFar) {   
               setProgressBar(progress);  
            });  
```  
  
 Per altre informazioni sulla programmazione asincrona, vedere [Programmazione asincrona in JavaScript](https://msdn.microsoft.com/en-us/library/windows/apps/hh700330.aspx).  
  
## <a name="see-also"></a>Vedere anche  
 [Uso di Windows Runtime in JavaScript](../jswinrt/using-the-windows-runtime-in-javascript.md)