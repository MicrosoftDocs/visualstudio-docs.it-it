---
title: IEnumDebugExtendedPropertyInfo::Clone | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugExtendedPropertyInfo.Clone
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugExtendedPropertyInfo::Clone
ms.assetid: dd645cf6-bfb3-486c-829e-bb91a6639665
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d873ba29ea2dc327cd6499613abb66d2a728008c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="ienumdebugextendedpropertyinfoclone"></a>IEnumDebugExtendedPropertyInfo::Clone
Crea un enumeratore che contiene lo stesso stato di enumerazione come enumerazione corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT Clone (  
   IEnumDebugExtendedPropertyInfo** ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppEnum`  
 [out] Restituisce l'oggetto duplicato `IEnumDebugExtendedPropertyInfo` interfaccia.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un oggetto valido `HRESULT`, in genere `S_OK`.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IEnumDebugExtendedPropertyInfo](../../winscript/reference/ienumdebugextendedpropertyinfo-interface.md)