---
title: Funzione JsRunSerializedScript | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsRunSerializedScript
helpviewer_keywords: JsRunSerializedScript function
ms.assetid: 3fd3f6f1-eb3e-4751-92a5-c93b1035f3b2
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b770edbcaa4e7dc36f295407627c10a8b574b88b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="jsrunserializedscript-function"></a>Funzione JsRunSerializedScript
Esegue uno script serializzato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
STDAPI_(JsErrorCode) JsRunSerializedScript(  
   _In_z_ const wchar_t *script,  
   _In_ BYTE *buffer,  
   _In_ JsSourceContext sourceContext,  
   _In_z_ const wchar_t *sourceUrl,  
   _Out_ JsValueRef *result  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `script`  
 Codice di origine dello script serializzato.  
  
 `buffer`  
 Script serializzato.  
  
 `sourceContext`  
 Cookie che identifica lo script che può essere usato dai contesti di script sottoponibili a debug.  
  
 `sourceUrl`  
 Percorso di origine dello script.  
  
 `result`  
 Risultato dell'esecuzione dello script, se disponibile. Questo parametro può essere null.  
  
## <a name="return-value"></a>Valore restituito  
 Codice `JsNoError` se l'operazione ha avuto esito positivo; in caso contrario, un codice di errore.  
  
## <a name="remarks"></a>Note  
 Richiede un contesto di script attivo.  
  
 Il buffer non viene mantenuto in memoria dal motore di script, quindi il codice deve mantenerlo attivo finché potrebbe essere usato per eseguire script.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jsrt.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti (Runtime JavaScript)](../chakra-hosting/reference-javascript-runtime.md)