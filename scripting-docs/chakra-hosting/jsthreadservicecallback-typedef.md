---
title: Typedef JsThreadServiceCallback | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: dbe67be5-418a-4f66-8b68-b38078a6d140
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c4b7ea4d0d5eaba17269a1777cdf96b5a2a5cda3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="jsthreadservicecallback-typedef"></a>Typedef JsThreadServiceCallback
Callback del servizio thread.  
  
## <a name="syntax"></a>Sintassi  
  
```  
typedef bool (CALLBACK *JsThreadServiceCallback)(  
   _In_ JsBackgroundWorkItemCallback callback,  
   _In_opt_ void *callbackData  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 callback  
 Callback per l'elemento di lavoro in background.  
  
 callbackData  
 Argomento di dati da passare al callback.  
  
## <a name="remarks"></a>Note  
 L'host può specificare un servizio thread in background quando si chiama JsCreateRuntime. Se specificato, gli elementi di lavoro in background verranno passati all'host con questo callback. È previsto che l'host inizi immediatamente l'esecuzione dell'elemento di lavoro in background e che restituisca true o false. Il runtime gestirà l'elemento di lavoro nel thread.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jsrt.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti (Runtime JavaScript)](../chakra-hosting/reference-javascript-runtime.md)