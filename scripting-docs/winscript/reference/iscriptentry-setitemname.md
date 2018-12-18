---
title: IScriptEntry::SetItemName | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IScriptEntry.SetItemName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::SetItemName
ms.assetid: 9551a7ec-38f8-466a-9722-09367763f380
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 483d3cdc1c8b8de9342003a99427fc2c727ad67f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptentrysetitemname"></a>IScriptEntry::SetItemName
Imposta il nome dell'elemento che identifica un `IScriptEntry` oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT SetItemName(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `psz`  
 [in] L'indirizzo di un buffer che contiene il nome dell'elemento. Il nome dell'elemento viene utilizzato dall'host per identificare la voce.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_FAIL`|Il metodo non è riuscita.|  
  
## <a name="remarks"></a>Note  
 Per `IScriptEntry` oggetti, questo metodo restituisce `S_OK`.  
  
 Per `IScriptScriptlet` oggetti (che derivano da `IScriptEntry`), questo metodo restituisce `E_FAIL`. Per `IScriptScriptlet` oggetti, il nome dell'elemento è impostato [IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md) e non può essere modificato.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IScriptEntry](../../winscript/reference/iscriptentry-interface.md)   
 [IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)