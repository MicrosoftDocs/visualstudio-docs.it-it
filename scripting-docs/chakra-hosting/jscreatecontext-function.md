---
title: Funzione JsCreateContext | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsCreateContext
helpviewer_keywords: JsCreateContext function
ms.assetid: aceca043-2c73-4029-a06c-8ad6695109cf
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ee756158401468ee00007a764e18a0846f35a3dc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="jscreatecontext-function"></a>Funzione JsCreateContext
Crea un contesto di script per l'esecuzione di script.  
  
## <a name="syntax"></a>Sintassi  
  
```  
// Edge mode signature  
STDAPI_(JsErrorCode) JsCreateContext(  
   _In_ JsRuntimeHandle runtime,  
   _Out_ JsContextRef *newContext);  
  
// Legacy mode signature  
STDAPI_(JsErrorCode) JsCreateContext(  
   _In_ JsRuntimeHandle runtime,  
   _In_ IDebugApplication *debugApplication,  
   _Out_ JsContextRef *newContext  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `runtime`  
 Runtime in cui viene creato il contesto di script.  
  
 `debugApplication`  
 Applicazione di debug da usare per il debug. Questo parametro può essere null. In questo caso, il debug non è abilitato per il contesto.  
  
 `newContext`  
 Il contesto di script creato.  
  
## <a name="return-value"></a>Valore restituito  
 Codice `JsNoError` se l'operazione ha avuto esito positivo; in caso contrario, un codice di errore.  
  
## <a name="remarks"></a>Note  
 Ogni contesto di script ha un proprio oggetto globale isolato da tutti gli altri contesti di script.  
  
 Il parametro `debugApplication` non è supportato in modalità Edge. Per altre informazioni sull'uso dell'API in modalità Edge, vedere [Scelta del motore Edge o del motore Legacy](../chakra-hosting/targeting-edge-vs-legacy-engines-in-jsrt-apis.md).  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jsrt.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti (Runtime JavaScript)](../chakra-hosting/reference-javascript-runtime.md)