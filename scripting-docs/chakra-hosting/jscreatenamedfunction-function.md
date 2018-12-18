---
title: Funzione JsCreateNamedFunction | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 72f40d06-ab82-4fed-a632-68af6b4126c2
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6a55f3df1d086394a7431b355f037b33e3f4a86c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="jscreatenamedfunction-function"></a>Funzione JsCreateNamedFunction
Crea una nuova funzione JavaScript con nome.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
STDAPI_(JsErrorCode) JsCreateNamedFunction(  
   _In_ JsValueRef name,  
   _In_ JsNativeFunction nativeFunction,  
   _In_opt_ void *callbackState,  
   _Out_ JsValueRef *function  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `name`  
 Nome di questa funzione che verrà usato per la diagnostica e la conversione in stringa.  
  
 `nativeFunction`  
 Metodo da chiamare quando viene richiamata la funzione.  
  
 `callbackState`  
 Stato fornito dall'utente che verrà passato al callback.  
  
 `function`  
 Nuovo oggetto della funzione.  
  
## <a name="return-value"></a>Valore restituito  
  
## <a name="remarks"></a>Note  
 Richiede un contesto di script attivo.  
  
 Questa API è supportata solo in modalità Edge.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jsrt.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti (Runtime JavaScript)](../chakra-hosting/reference-javascript-runtime.md)