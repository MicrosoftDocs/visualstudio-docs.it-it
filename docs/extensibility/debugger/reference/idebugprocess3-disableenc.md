---
title: IDebugProcess3::DisableENC | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProcess3::DisableENC
helpviewer_keywords: IDebugProcess3::DisableENC
ms.assetid: cffdbdac-4d76-4aeb-aa55-5d0410db99f1
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fba3718052b708b5c5d88306c022ed9c397a99cf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
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