---
title: Funzione JsEnumerateHeap | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsEnumerateHeap
helpviewer_keywords: JsEnumerateHeap function
ms.assetid: 3e518e0b-b959-4686-899c-83e6b1946c9d
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 48d7698218df49b8ffd680cf26df370c2f97b7c0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="jsenumerateheap-function"></a>Funzione JsEnumerateHeap
Enumera l'heap del contesto corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
STDAPI_(JsErrorCode) JsEnumerateHeap(  
   _Out_ IActiveScriptProfilerHeapEnum **enumerator  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `enumerator`  
 Enumeratore dell'heap.  
  
## <a name="return-value"></a>Valore restituito  
 Codice `JsNoError` se l'operazione ha avuto esito positivo; in caso contrario, un codice di errore.  
  
## <a name="remarks"></a>Note  
 Durante l'enumerazione dell'heap, il contesto corrente non può essere rimosso e tutte le chiamate per modificare lo stato del contesto non riescono fino a quando l'enumeratore dell'heap non viene rilasciato.  
  
 Richiede un contesto di script attivo.  
  
 Questa API è supportata nelle app desktop, ma non nelle app di Windows Store.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jsrt.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti (Runtime JavaScript)](../chakra-hosting/reference-javascript-runtime.md)