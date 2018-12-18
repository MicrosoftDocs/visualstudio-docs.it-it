---
title: Typedef JsPromiseContinuationCallback | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 51a3fd02-9668-4cf7-bb0b-e1fd03b2528f
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 762391cb66e5298bd70beb3238720d3717554ae0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="jspromisecontinuationcallback-typedef"></a>Typedef JsPromiseContinuationCallback
Callback di continuazione della promessa.  
  
## <a name="syntax"></a>Sintassi  
  
```  
typedef void (CALLBACK *JsPromiseContinuationCallback)(  
  _In_ JsValueRef task,  
  _In_opt_ void *callbackState  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `task`  
  `callbackState`  
  
## <a name="remarks"></a>Note  
 L'host può specificare un callback di continuazione della promessa in `JsSetPromiseContinuationCallback`. Se uno script crea un'attività da eseguire successivamente, con l'attività verrà chiamato il callback di continuazione della promessa e l'attività dovrà essere inserita in una coda FIFO in modo che venga eseguita al termine dell'esecuzione dello script corrente.  
  
 Questa API è supportata solo in modalità Edge.  
  
## <a name="requirements"></a>Requisiti  
 jsrt.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti (Runtime JavaScript)](../chakra-hosting/reference-javascript-runtime.md)