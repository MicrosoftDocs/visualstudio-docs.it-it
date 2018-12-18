---
title: IDebugProcess3::DisableENC | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProcess3::DisableENC
helpviewer_keywords:
- IDebugProcess3::DisableENC
ms.assetid: cffdbdac-4d76-4aeb-aa55-5d0410db99f1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2da464c82332f6fc4f9bcd57ee8197e111e9fa0a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprocess3disableenc"></a>IDebugProcess3::DisableENC
Questo metodo in modo esplicito Disabilita modifica e continuazione su questo processo e tutti i programmi che contiene. Un fornitore di porta personalizzato deve sempre restituire `E_NOTIMPL`.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT DisableENC(  
   EncUnavailableReason reason  
);  
```  
  
```csharp  
   EncUnavailableReason reason  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `reason`  
 [in] Un valore di [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md) enumerazione.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce il codice di errore.  
  
> [!NOTE]
>  Un fornitore di porta personalizzato deve sempre restituire `E_NOTIMPL`.  
  
## <a name="remarks"></a>Note  
 Una volta modifica e continuazione è disabilitata per un processo, è possibile abilitare di nuovo solo riavviando il processo.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)