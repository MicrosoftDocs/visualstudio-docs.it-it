---
title: Costanti debug | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 76b572ee-bad0-404e-9fd4-841c9af35642
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e2c50181dc9f40d8665d6caca407232231682d63
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="debug-constants"></a>Costanti DEBUG
Le costanti debug restituiscono valori costanti che sono proprietà dell'oggetto `Debug`.  
  
## <a name="debug-object-constants"></a>Costanti debug dell'oggetto  
 Nella tabella seguente sono elencati i valori costanti che sono proprietà del [oggetto Debug](../../javascript/reference/debug-object-javascript.md).  
  
|Costante|Descrizione|Valore|  
|--------------|-----------------|-----------|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_ASSIGN_DELEGATE`|L'elemento di lavoro sincrono ha assegnato un callback o una continuazione da eseguire tramite un'operazione asincrona.|0|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_JOIN`|L'elemento di lavoro sincrono ha soddisfatto parte di un'operazione asincrona di join.|1|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_CHOOSEANY`|L'elemento di lavoro sincrono ha soddisfatto un'operazione asincrona di scelta.|2|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_CANCEL`|L'elemento di lavoro sincrono è stato annullato.|3|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_ERROR`|L'elemento di lavoro sincrono ha generato un errore in un'operazione asincrona.|4|  
|`Debug.MS_ASYNC_OP_STATUS_SUCCESS`|Operazione asincrona completata.|1|  
|`Debug.MS_ASYNC_OP_STATUS_CANCELED`|Operazione asincrona annullata.|2|  
|`Debug.MS_ASYNC_OP_STATUS_ERROR`|L'operazione asincrona ha restituito un errore.|3|  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione debug. mstraceasyncoperationcompleted](../../javascript/reference/debug-mstraceasyncoperationcompleted-function.md)   
 [Funzione Debug.msUpdateAsyncCallbackRelation](../../javascript/reference/debug-msupdateasynccallbackrelation-function.md)