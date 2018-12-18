---
title: IScriptEntry::SetBody | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IScriptEntry.SetBody
apilocation: scrobj.dll
helpviewer_keywords: IScriptEntry::SetBody
ms.assetid: 719062e4-98e4-4a7b-946d-6e5dbbcc5225
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 06ee232aa730366e9a23e15cdc45f6734b9ef744
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptentrysetbody"></a>IScriptEntry::SetBody
Imposta il testo che si trova nel corpo di un `IScriptEntry` blocco di script o un `IScriptScriptlet` scriptlet.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT SetBody(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `psz`  
 [in] Per un `IScriptEntry` blocco di script, `psz` è il testo racchiuso tra i tag di script.  
  
 Per un `IScriptEntry` blocco funzione `psz` è il corpo della funzione.  
  
 Per un `IScriptScriptlet` oggetto (che deriva da `IScriptEntry`), `psz` è il testo dello script dello scriptlet.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IScriptEntry](../../winscript/reference/iscriptentry-interface.md)   
 [IScriptEntry::GetBody](../../winscript/reference/iscriptentry-getbody.md)