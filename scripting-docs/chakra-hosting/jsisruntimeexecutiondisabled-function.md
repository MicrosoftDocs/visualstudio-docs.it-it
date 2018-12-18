---
title: Funzione JsIsRuntimeExecutionDisabled | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsIsRuntimeExecutionDisabled
helpviewer_keywords:
- JsIsRuntimeExecutionDisabled function
ms.assetid: 77490280-fb84-4614-a1f0-6ac31e3bd607
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f4827205a33d337445faf9b0e9812133f0de3e97
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="jsisruntimeexecutiondisabled-function"></a>Funzione JsIsRuntimeExecutionDisabled
Restituisce un valore che indica se l'esecuzione di script è disabilitata nel runtime.  
  
## <a name="syntax"></a>Sintassi  
  
```vb  
STDAPI_(JsErrorCode) JsIsRuntimeExecutionDisabled(    _In_ JsRuntimeHandle runtime,    _Out_ bool *isDisabled);  
```  
  
#### <a name="parameters"></a>Parametri  
 `runtime`  
 Specifica il controllo da parte del runtime in caso di disabilitazione dell'esecuzione.  
  
 `isDisabled`  
 `true` se l'esecuzione è disabilitata, in caso contrario, `false`.  
  
## <a name="return-value"></a>Valore restituito  
 `JsNoError` se l'operazione ha esito positivo; in caso contrario, un codice di errore.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jsrt.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti (Runtime JavaScript)](../chakra-hosting/reference-javascript-runtime.md)