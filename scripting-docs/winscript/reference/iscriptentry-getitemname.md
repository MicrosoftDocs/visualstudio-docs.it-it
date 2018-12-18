---
title: IScriptEntry::GetItemName | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetItemName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetItemName
ms.assetid: 8f2562f1-8231-4a39-ad79-074f9ec3d403
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cdbb293afc6f58f8d9d9c1fe27bae467fd36792c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptentrygetitemname"></a>IScriptEntry::GetItemName
Restituisce il nome dell'elemento che identifica un `IScriptEntry` oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetItemName(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pbstr`  
 [out] L'indirizzo di un buffer che contiene il nome dell'elemento. Il nome dell'elemento viene utilizzato dall'host per identificare la voce.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Per `IScriptScriptlet` oggetti, impostare il nome dell'elemento utilizzando [IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md). Per le altre interfacce, impostare il nome dell'elemento utilizzando [IScriptEntry::SetItemName](../../winscript/reference/iscriptentry-setitemname.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IScriptEntry](../../winscript/reference/iscriptentry-interface.md)