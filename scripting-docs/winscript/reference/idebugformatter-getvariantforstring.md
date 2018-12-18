---
title: IDebugFormatter::GetVariantForString | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugFormatter.GetVariantForString
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugFormatter::GetVariantForString
ms.assetid: 2993431d-0ee2-4d8d-b62c-0a810a8bc391
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3f9f783c8fe1864999e017ff348853df5464c93f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugformattergetvariantforstring"></a>IDebugFormatter::GetVariantForString
Restituisce una variabile VARIANT contenente la stringa specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetVariantForString(  
   LPCOLESTR  pwstrValue,  
   VARIANT*   pvar  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pwstrValue`  
 [in] Stringa da archiviare in una variabile VARIANT.  
  
 `pvar`  
 [out] VARIANT contenente `pwstrValue`.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo restituisce una variabile VARIANT contenente la stringa specificata.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugFormatter](../../winscript/reference/idebugformatter-interface.md)