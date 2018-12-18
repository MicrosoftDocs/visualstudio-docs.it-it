---
title: IScriptEntry::GetRange | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IScriptEntry.GetRange
apilocation: scrobj.dll
helpviewer_keywords: IScriptEntry::GetRange
ms.assetid: 3ac18f0a-b470-4f4d-b8f5-2da3fdef74f1
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0ae0ee34298e03fdd2e9c6bc841d9fbe90967e8f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptentrygetrange"></a>IScriptEntry::GetRange
Restituisce la posizione iniziale e una lunghezza di una voce.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetRange(  
   ULONG              *pichMin  
   ULONG              *pcch  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pichMin`  
 [out] Per `IScriptEntry` oggetti che specificano un blocco di script, restituisce 0.  
  
 Per `IScriptEntry` oggetti che specificano un oggetto funzione, restituisce la posizione di inizio della funzione nel blocco di script corrente.  
  
 Per `IScriptScriptlet` gli oggetti, restituisce 0.  
  
 `pcch`  
 [out] Per `IScriptEntry` oggetti che specificano un blocco di script, restituisce la lunghezza del testo.  
  
 Per `IScriptEntry` oggetti che specificano un oggetto funzione, restituisce la lunghezza della definizione della funzione.  
  
 Per `IScriptScriptlet` gli oggetti, restituisce la lunghezza della voce.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IScriptEntry](../../winscript/reference/iscriptentry-interface.md)