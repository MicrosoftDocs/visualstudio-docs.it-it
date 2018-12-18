---
title: IApplicationDebugger::CreateInstanceAtDebugger | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IApplicationDebugger.CreateInstanceAtDebugger
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebugger::CreateInstanceAtDebugger
ms.assetid: 6763afac-c86a-4e88-9580-77108fb242fb
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f6495c2d8782d1128700bdfb6d4081b80ffae878
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iapplicationdebuggercreateinstanceatdebugger"></a>IApplicationDebugger::CreateInstanceAtDebugger
Consente la creazione di oggetti nel processo del debugger per codice che è out-of-process al debugger.  
  
> [!IMPORTANT]
>  Questo metodo non deve essere implementato, perché consente al codice non attendibile creare oggetti arbitrari in un thread del debugger attendibile.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT CreateInstanceAtDebugger(  
   REFCLSID    rclsid,  
   IUnknown*   pUnkOuter,  
   DWORD       dwClsContext,  
   REFIID      riid,  
   IUnknown**  ppvObject  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `rclsid`  
 [in] Classe (CLSID) di identificatore di oggetto da creare.  
  
 `pUnkOuter`  
 [in] Se `NULL`, l'oggetto non sia stata creata come parte di un'aggregazione. In caso contrario, `pUnkOuter` è un puntatore all'oggetto aggregato `IUnknown` interfaccia (il controllo `IUnknown`).  
  
 `dwClsContext`  
 [in] Contesto per l'esecuzione di codice eseguibile. I valori sono tratti dall'enumerazione `CLSCTX`.  
  
 `riid`  
 [in] L'identificatore di interfaccia utilizzata per comunicare con l'oggetto.  
  
 `ppvObject`  
 [out] Indirizzo della variabile puntatore che riceve il puntatore di interfaccia richiesto `riid`. Dopo la restituzione ha esito positivo, *`ppvObject` contiene il puntatore di interfaccia richiesto. In caso di errore, \* `ppvObject` contiene `NULL`.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo delega al `CoCreateInstance`.  
  
 Il metodo non è attualmente implementato.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IApplicationDebugger](../../winscript/reference/iapplicationdebugger-interface.md)