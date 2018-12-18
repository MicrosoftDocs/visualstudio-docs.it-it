---
title: Funzione JsCreateDataView | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 161e59eb-d429-46f7-9a38-bbf2149ccf44
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e5150a9b858e09217ee7ac3c1f25efba36615f9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="jscreatedataview-function"></a>Funzione JsCreateDataView
Crea un oggetto `DataView` Javascript.  
  
## <a name="syntax"></a>Sintassi  
  
```  
JsErrorCode  JsCreateDataView(  
   _In_ JsValueRef arrayBuffer,  
   _In_ unsigned int byteOffset,  
   _In_ unsigned int byteLength,  
   _Out_ JsValueRef *result  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `arrayBuffer`  
 Oggetto `ArrayBuffer` esistente da usare come archivio per l'oggetto `DataView` del risultato.  
  
 `byteOffset`  
 Offset in byte a partire dall'inizio di `arrayBuffer` a cui deve fare riferimento l'elemento `DataView` del risultato.  
  
 `byteLength`  
 Numero di byte in ArrayBuffer a cui deve fare riferimento l'elemento DataView del risultato.  
  
 `result`  
 Nuovo oggetto DataView.  
  
## <a name="return-value"></a>Valore restituito  
 Codice `JsNoError` se l'operazione ha avuto esito positivo; in caso contrario, un codice di errore.  
  
## <a name="remarks"></a>Note  
 Richiede un contesto di script attivo.  
  
 Questa API è supportata solo in modalità Edge.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jsrt.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti (Runtime JavaScript)](../chakra-hosting/reference-javascript-runtime.md)