---
title: IDebugApplication::FireDebuggerEvent | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.FireDebuggerEvent
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::FireDebuggerEvent
ms.assetid: fd1f602e-fc15-4158-a6e7-497ff5b4a509
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c4cb02390602b6b93b8c233f245ede395833d67e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationfiredebuggerevent"></a>IDebugApplication::FireDebuggerEvent
Viene generato un evento generico per il debugger `IApplicationDebugger` interfaccia.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT FireDebuggerEvent(  
   REFGUID    riid,  
   IUnknown*  punk  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `riid`  
 [in] Un GUID per l'oggetto.  
  
 `punk`  
 [in] Oggetto evento da passare al debugger.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_NOTIMPL`|Il metodo non è attualmente implementato.|  
  
## <a name="remarks"></a>Note  
 La semantica del GUID e `IUnknown` sono completamente definita dall'applicazione/debugger.  
  
 In questo modo per le estensioni personalizzate del modello del debugger. non è attualmente implementata.  
  
 Questo metodo determina `IApplicationDebugger::onDebuggerEvent` da chiamare.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugApplication](../../winscript/reference/idebugapplication-interface.md)   
 [IApplicationDebugger::onDebuggerEvent](../../winscript/reference/iapplicationdebugger-ondebuggerevent.md)