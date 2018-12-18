---
title: Funzione JsDisableRuntimeExecution | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsDisableRuntimeExecution
helpviewer_keywords:
- JsDisableRuntimeExecution function
ms.assetid: 4bd4670a-a9da-4f8c-b3fd-1fd366d915c3
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f44545f7c81344a2d22f0083087f77ac8074278c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="jsdisableruntimeexecution-function"></a>Funzione JsDisableRuntimeExecution
Sospende l'esecuzione di script e termina tutti gli script in esecuzione nel runtime.  
  
## <a name="syntax"></a>Sintassi  
  
```  
STDAPI_(JsErrorCode) JsDisableRuntimeExecution(  
   _In_ JsRuntimeHandle runtime  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `runtime`  
 Il runtime da sospendere.  
  
## <a name="return-value"></a>Valore restituito  
 Codice `JsNoError` se l'operazione ha avuto esito positivo; in caso contrario, un codice di errore.  
  
## <a name="remarks"></a>Note  
 Le chiamate a runtime sospesi non verranno eseguite correttamente finché `JsEnableRuntimeExecution` viene chiamata.  
  
 Questa API non deve essere chiamata su un thread che è attivo sul runtime. Nonostante il runtime venga impostato in uno stato sospeso, uno script in esecuzione non può essere sospeso contemporaneamente; lo script in esecuzione verrà terminato con un'eccezione non catturabile il prima possibile.  
  
 Sospendere l'esecuzione in un runtime che è già stato sospeso è un'operazione che non produce effetti.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jsrt.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti (Runtime JavaScript)](../chakra-hosting/reference-javascript-runtime.md)