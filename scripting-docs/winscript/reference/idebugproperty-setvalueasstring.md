---
title: IDebugProperty::SetValueAsString | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugProperty.SetValueAsString
apilocation: scrobj.dll
helpviewer_keywords: IDebugProperty::SetValueAsString
ms.assetid: cad8d7b2-19a5-4a29-9000-cafdecdc238b
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 88a7cba4ec83c5428dd4da4a23ce554702177e76
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugpropertysetvalueasstring"></a>IDebugProperty::SetValueAsString
Imposta il valore di una proprietà da una stringa specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT SetValueAsString (  
   LPCOLESTR pszValue,  
   UINTnRadix,  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pszValue`  
 [in] Il valore da impostare.  
  
 `nRadix`  
 [in] Base per essere utilizzato per interpretare le informazioni numeriche.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un oggetto valido `HRESULT`, in genere `S_OK`.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugProperty](../../winscript/reference/idebugproperty-interface.md)