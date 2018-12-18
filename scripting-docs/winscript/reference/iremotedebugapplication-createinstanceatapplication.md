---
title: IRemoteDebugApplication::CreateInstanceAtApplication | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IRemoteDebugApplication.CreateInstanceAtApplication
apilocation: pdm.dll
helpviewer_keywords: IRemoteDebugApplication::CreateInstanceAtApplication
ms.assetid: d669ec80-2182-400d-87cc-7c1753315e5c
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a2185987f6b635dae4d537231fca3327d0aed003
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplicationcreateinstanceatapplication"></a>IRemoteDebugApplication::CreateInstanceAtApplication
Consente la creazione di oggetti nel processo dell'applicazione dal codice che è out-of-process per l'applicazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT CreateInstanceAtApplication(  
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
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md)