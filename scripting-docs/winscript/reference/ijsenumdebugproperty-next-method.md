---
title: 'Metodo ijsenumdebugproperty:: Next | Documenti Microsoft'
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsEnumDebugProperty.Next
apilocation: jscript9diag.dll
ms.assetid: 9fad1893-483a-440c-88c1-469494212300
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b8c85601709bb727549152ffdb01e15dbd84e510
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="ijsenumdebugpropertynext-method"></a>Metodo IJsEnumDebugProperty::Next
Legge le proprietà per questo oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT Next(  
   ULONG count,  
   IJsDebugProperty **ppDebugProperty,  
   ULONG *pActualCount  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `count`  
 [in] Il numero di proprietà da leggere.  
  
 `ppDebugProperty`  
 [out] Oggetto che rappresenta il Visualizzatore proprietà.  
  
 `pActualCount`  
 [out] Il numero effettivo di proprietà dell'oggetto.  
  
## <a name="return-value"></a>Valore restituito  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IJsEnumDebugProperty](../../winscript/reference/ijsenumdebugproperty-interface.md)