---
title: Funzione JsRunScript | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsRunScript
helpviewer_keywords:
- JsRunScript function
ms.assetid: 8d6b8c9a-af3a-4e21-a330-5a6b535423a3
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a4cefe561fce5b479c0f520693f5813cbd7594b9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="jsrunscript-function"></a>Funzione JsRunScript
Esegue uno script.  
  
## <a name="syntax"></a>Sintassi  
  
```  
STDAPI_(JsErrorCode) JsRunScript(  
   _In_z_ const wchar_t *script,  
   _In_ JsSourceContext sourceContext,  
   _In_z_ const wchar_t *sourceUrl,  
   _Out_ JsValueRef *result  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `script`  
 Script da eseguire.  
  
 `sourceContext`  
 Cookie che identifica lo script che può essere usato dai contesti di script sottoponibili a debug.  
  
 `sourceUrl`  
 Percorso di origine dello script.  
  
 `result`  
 Risultato dello script, se disponibile. Questo parametro può essere null.  
  
## <a name="return-value"></a>Valore restituito  
 Codice `JsNoError` se l'operazione ha avuto esito positivo; in caso contrario, un codice di errore.  
  
## <a name="remarks"></a>Note  
 Richiede un contesto di script attivo.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jsrt.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti (Runtime JavaScript)](../chakra-hosting/reference-javascript-runtime.md)