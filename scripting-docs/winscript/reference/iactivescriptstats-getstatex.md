---
title: IActiveScriptStats::GetStatEx | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptStats.GetStatEx
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptStats::GetStatEx
ms.assetid: f526f51d-8ab5-49ef-a8f7-ae0ac1cb46e4
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5cb8adf27811f3046de7b447e537443ef129a8c3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptstatsgetstatex"></a>IActiveScriptStats::GetStatEx
Restituisce una statistica di uno script personalizzato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetStatEx(  
   REFGUID  guid,  
   ULONG*   pluHi,  
   ULONG*   pluLo  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `guid`  
 [in] Specifica quale statistica da restituire. La semantica di statistiche corrisponde a un determinato GUID è interamente motore definito.  
  
 `pluHi`  
 [out] 32 bit alti di un intero senza segno a 64 bit che rappresenta la statistica.  
  
 `pluLo`  
 [out] 32 bit bassi di un intero senza segno a 64 bit che rappresenta la statistica.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_NOTIMPL`|Il metodo non è implementato.|  
  
## <a name="remarks"></a>Note  
 Questo metodo consente a un motore di script personalizzato restituire statistiche significative per un host personalizzato.  
  
> [!NOTE]
>  Questo metodo non è attualmente implementato.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptStats::GetStat](../../winscript/reference/iactivescriptstats-getstat.md)   
 [Interfaccia IActiveScriptStats](../../winscript/reference/iactivescriptstats-interface.md)