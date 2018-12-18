---
title: IScriptEntry::SetText | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IScriptEntry.SetText
apilocation:
- scrobj.dll
helpviewer_keywords:
- ISetEntry::SetText
ms.assetid: 4605481b-7707-43d1-ab78-a9207d0cf6fe
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 62f1d113dc23dca85db02bf23b2c79551108f3b6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptentrysettext"></a>IScriptEntry::SetText
Imposta il testo che corrisponde a un `IScriptEntry` blocco di script o il codice sorgente che è contenuto in un `IScriptScriptlet` gestore dell'evento.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT SetText(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `psz`  
 [in] Il testo del `IScriptEntry` blocco di script o del codice sorgente del `IScriptScriptlet` gestore dell'evento.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IScriptEntry](../../winscript/reference/iscriptentry-interface.md)