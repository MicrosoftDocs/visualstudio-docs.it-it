---
title: ICanHandleException::CanHandleException | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ICanHandleException.CanHandleException
apilocation:
- scrobj.dll
helpviewer_keywords:
- ICanHandleException::CanHandleException
ms.assetid: 0fc703bf-9518-487e-af20-00e073b640f1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 15612330f160f694202bb2158f970e0633fe53bd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="icanhandleexceptioncanhandleexception"></a>ICanHandleException::CanHandleException
Determina se il chiamante del motore di script può gestire un'eccezione specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT CanHandleException(  
   EXCEPINFO*  pExcepInfo,  
   VARIANT*    pvar  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pExcepInfo`  
 [in] Puntatore a un `EXCEPINFO` struttura contenente le informazioni che verranno segnalate se non viene trovato alcun gestore eccezioni.  
  
 `pvar`  
 [in] Un valore associato all'eccezione, ad esempio il valore generato da un `throw` istruzione. Questo parametro può essere `NULL`.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il chiamante può gestire l'eccezione|  
|`E_FAIL`|Il chiamante non è possibile gestire l'eccezione.|  
  
## <a name="remarks"></a>Note  
 Se una chiamata a `IDispatchEx::InvokeEx`, o un metodo simile, genera un'eccezione, il motore di script di verifica di un chiamante nella catena di chiamante dello script che supporta il `ICanHandleException` l'interfaccia e indica che è possibile gestire l'eccezione. Se nessun chiamante può gestire l'eccezione, il motore di script si interrompe.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia ICanHandleException](../../winscript/reference/icanhandleexception-interface.md)   
 [IDispatchEx::InvokeEx](../../winscript/reference/idispatchex-invokeex.md)