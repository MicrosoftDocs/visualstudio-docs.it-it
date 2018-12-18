---
title: IDebugProperty::GetPropertyInfo | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugProperty.GetPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugProperty::GetPropertyInfo
ms.assetid: b201c0c4-bff6-4285-880f-67be90584c5f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: edd878419c6f2b4fd0f882a070d80c98a96eba56
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugpropertygetpropertyinfo"></a>IDebugProperty::GetPropertyInfo
Ottiene il valore di un `IDebugProperty` che descrive un metodo o una proprietà indicizzata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetPropertyInfo (  
   DBGPROP_INFO_FLAGSdwFields,  
   UINT nRadix,  
   DebugPropertyInfo* pPropertyInfo  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwFields`  
 [in] Specifica il `DBGPROP_INFO_FLAGS` le costanti che determinano i campi per la compilazione `DebugPropertyInfo` struttura.  
  
 `nRadix`  
 [in] Base da utilizzare per la formattazione di eventuali informazioni numeriche.  
  
 `pPropertyInfo`  
 [out] Restituisce il `DebugPropertyInfo` struttura che descrive la proprietà.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un oggetto valido `HRESULT`, in genere `S_OK`.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugProperty](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)   
 [Struttura DebugPropertyInfo](../../winscript/reference/debugpropertyinfo-structure.md)