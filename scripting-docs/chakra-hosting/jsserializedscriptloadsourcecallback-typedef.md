---
title: Typedef JsSerializedScriptLoadSourceCallback | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9406c488-76ac-49e5-b305-39751f3412ea
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0ff3bc206cf3779023a13166f30e8f4f719e7ebe
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="jsserializedscriptloadsourcecallback-typedef"></a>Typedef JsSerializedScriptLoadSourceCallback
Chiamata di runtime per caricare codice sorgente dello script serializzato.     Il chiamante deve mantenere il buffer dello script valido fino a `JsSerializedScriptUnloadCallback`.  
  
## <a name="syntax"></a>Sintassi  
  
```  
typedef bool (CALLBACK * JsSerializedScriptLoadSourceCallback)(  
  _In_ JsSourceContextsourceContext,  
  _Outptr_result_z_ const wchar_t** scriptBuffer  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `sourceContext`  
 Contesto passato a `JsParseSerializedScriptWithCallback` o a `JsRunSerializedScriptWithCallback`.  
  
 `scriptBuffer`  
 Script restituito.  
  
## <a name="remarks"></a>Note  
  
> [!WARNING]
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jsrt.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti (Runtime JavaScript)](../chakra-hosting/reference-javascript-runtime.md)