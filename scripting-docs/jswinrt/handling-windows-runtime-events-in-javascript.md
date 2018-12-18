---
title: Gestione degli eventi di Windows Runtime in JavaScript | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JavaScript, Windows Runtime events
- Windows Runtime events [JavaScript]
ms.assetid: d9436aff-2c30-4846-b8df-eaa3e63fd75c
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e963472ee51f2439b50807a49425dcd7f6d8443a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="handling-windows-runtime-events-in-javascript"></a>Gestione degli eventi di Windows Runtime in JavaScript
Gli eventi di Windows Runtime non sono rappresentati nello stesso modo in JavaScript rispetto a C++ o .NET Framework. Non sono proprietà di classi, ma sono piuttosto rappresentati come identificatori di stringa passati ai metodi `addEventListener` e `removeEventListener` della classe. Ad esempio, è possibile aggiungere un gestore dell'evento per l'evento [Geolocator.PositionChanged](http://msdn.microsoft.com/library/windows/apps/xaml/windows.devices.geolocation.geolocator.positionchanged.aspx) passando la stringa "positionchanged" al metodo `Geolocator.addEventListener`:  
  
```JavaScript  
var locator =  new Windows.Devices.Geolocation.Geolocator();  
locator.addEventListener(  
    "positionchanged",   
     function (ev) {  
        console.log("Got event");  
    });  
```  
  
 È anche possibile impostare la proprietà `locator.onpositionchanged`.  
  
```  
locator.onpositionchanged =    
    function (ev) {  
        console.log("Got event");  
    };  
```  
  
 In JavaScript gli argomenti degli eventi di Windows Runtime sono rappresentati come singolo oggetto evento. Nell'esempio seguente, relativo a un metodo di gestore eventi, il parametro `ev` è un oggetto che contiene il mittente (proprietà di destinazione) e gli altri argomenti dell'evento. Gli argomenti dell'evento sono documentati per ogni evento.  
  
```JavaScript  
function (ev) {  
    console.log("Target: " + ev.target);  
    console.log("Position: " +  
        ev.position.latitude + "," +  
        ev.position.longitude);  
};  
  
```  
  
> [!IMPORTANT]
>  Le funzionalità di Windows Runtime non sono disponibili per app eseguite in Internet Explorer.  
  
## <a name="see-also"></a>Vedere anche  
 [Uso di Windows Runtime in JavaScript](../jswinrt/using-the-windows-runtime-in-javascript.md)