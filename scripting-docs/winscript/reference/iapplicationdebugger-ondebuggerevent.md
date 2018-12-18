---
title: IApplicationDebugger::onDebuggerEvent | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IApplicationDebugger.onDebuggerEvent
apilocation: scrobj.dll
helpviewer_keywords: IApplicationDebugger::onDebuggerEvent
ms.assetid: 82a5faaa-1222-4bf1-8569-10439dbdf16d
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 754c56b8474a5e21a05c1399540391197c373118
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iapplicationdebuggerondebuggerevent"></a>IApplicationDebugger::onDebuggerEvent
Gestisce l'evento applicazione personalizzata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT onDebuggerEvent(  
   REFIID     riid,  
   IUnknown*  punk  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `riid`  
 [in] L'identificatore di interfaccia per l'oggetto.  
  
 `punk`  
 [in] L'oggetto evento, che implementa l'interfaccia definita da `riid`.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_NOTIMPL`|Il metodo non è attualmente implementato.|  
  
## <a name="remarks"></a>Note  
 La semantica del `IUnknown` è completamente definita dall'applicazione/debugger.  
  
 In questo modo per le estensioni personalizzate del modello del debugger. non è attualmente implementata.  
  
 Questo metodo viene chiamato quando `IDebugApplication::FireDebuggerEvent` viene chiamato.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IApplicationDebugger](../../winscript/reference/iapplicationdebugger-interface.md)   
 [IDebugApplication::FireDebuggerEvent](../../winscript/reference/idebugapplication-firedebuggerevent.md)