---
title: Typedef JsMemoryAllocationCallback | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 511babc7-3caa-4ee5-82a2-943bbd34db8d
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9672c23f48a2cb3e20de58012b267b30f4514d66
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="jsmemoryallocationcallback-typedef"></a>Typedef JsMemoryAllocationCallback
Routine implementata dall'utente per eventi di allocazione della memoria.  
  
## <a name="syntax"></a>Sintassi  
  
```  
typedef bool (CALLBACK * JsMemoryAllocationCallback)(  
   _In_opt_ void *callbackState,  
   _In_ JsMemoryEventType allocationEvent,  
   _In_ size_t allocationSize  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 callbackState  
 Stato passato a JsSetRuntimeMemoryAllocationCallback.  
  
 allocationEvent  
 Tipo di evento di allocazione.  
  
 allocationSize  
 Dimensione dell'allocazione.  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 La restituzione di per l'evento JsMemoryAllocate true permette al runtime di procedere con l'allocazione. La restituzione di false indica che la richiesta di allocazione è stata rifiutata. Il valore restituito sarà ignorato per gli altri eventi di allocazione.  
  
## <a name="remarks"></a>Note  
 Usare JsSetRuntimeMemoryAllocationCallback per registrare questo callback.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jsrt.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti (Runtime JavaScript)](../chakra-hosting/reference-javascript-runtime.md)