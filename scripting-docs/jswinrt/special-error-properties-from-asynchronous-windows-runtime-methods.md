---
title: "Proprietà speciali degli errori restituiti da metodi asincroni di Windows Runtime | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 45155584-06d8-4e7f-93a6-8564a93f643d
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 120d8f699c8bedd0fe5762300203c5d5ec18e73e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="special-error-properties-from-asynchronous-windows-runtime-methods"></a>Proprietà speciali degli errori restituiti da metodi asincroni di Windows Runtime
Può essere difficile eseguire il debug di metodi asincroni di Windows Runtime in JavaScript, perché l'errore potrebbe essere generato da un punto profondo qualsiasi nello stack di chiamate. L'oggetto `Error` JavaScript dispone di proprietà aggiuntive che vengono visualizzate solo quando viene generato l'errore da un metodo asincrono di Windows Runtime quando l'app è in esecuzione in modalità di debug.  
  
## <a name="special-error-properties"></a>Proprietà speciali degli errori  
 Un oggetto dell'errore che risulta da un'operazione asincrona di Windows Runtime che ha avuto esito negativo in modalità di debug ha le seguenti proprietà speciali:  
  
-   `asyncOpSource` (Oggetto) Ottiene informazioni sulla posizione originale in cui è stata eseguita la chiamata che ha generato un errore. La proprietà `asyncOpSource.originatingCall` (stringa) visualizza la posizione nel codice dell'utente che ha avviato l'operazione asincrona.  
  
-   asyncOpType (stringa) Ottiene il nome del tipo di operazione asincrona che ha generato l'errore.  
  
 Per altre informazioni sugli errori con le operazioni asincrone, vedere:  
  
-   [Come gestire gli errori con suggerimenti](https://msdn.microsoft.com/en-us/library/windows/apps/hh700337.aspx)  
  
-   [Risoluzione degli errori di Windows Runtime](http://msdn.microsoft.com/en-us/1ef7d7df-82ac-441d-8ad0-54ab1318de64)