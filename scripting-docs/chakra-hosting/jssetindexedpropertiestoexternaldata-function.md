---
title: Funzione JsSetIndexedPropertiesToExternalData | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: cee2d86d-ed42-4acb-86ef-95a67e63d0d6
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7180c5e233cfd5e448bc9f0d3eb1895e5dfd4aa8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="jssetindexedpropertiestoexternaldata-function"></a>Funzione JsSetIndexedPropertiesToExternalData
Imposta le proprietà indicizzate di un oggetto ai dati esterni. I dati esterni verranno usati come archivio di backup per le proprietà indicizzate dell'oggetto, a cui accedere come matrice tipizzata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
STDAPI_(JsErrorCode) JsSetIndexedPropertiesToExternalData(  
   _In_ JsValueRef object,  
   _In_ void* data,  
   _In_ JsTypedArrayType arrayType,  
   _In_ unsigned int elementLength  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `object`  
 Oggetto su cui eseguire l'operazione.  
  
 `data`  
 Dati esterni da usare come archivio di backup per le proprietà indicizzate dell'oggetto.  
  
 `arrayType`  
 Tipo di elemento di matrice nei dati esterni.  
  
 `elementLength`  
 Numero di elementi di matrice nei dati esterni.  
  
## <a name="return-value"></a>Valore restituito  
 Codice `JsNoError` se l'operazione ha avuto esito positivo; in caso contrario, un codice di errore.  
  
## <a name="remarks"></a>Note  
 Richiede un contesto di script attivo.  
  
 Questa API è supportata solo in modalità Edge.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jsrt.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti (Runtime JavaScript)](../chakra-hosting/reference-javascript-runtime.md)