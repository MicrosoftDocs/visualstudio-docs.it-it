---
title: IDebugEngineProgram2::Stop | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngineProgram2::Stop
helpviewer_keywords:
- IDebugEngineProgram2::Stop
ms.assetid: 6e1c3d56-fb67-4a5b-80f9-8ee5131972bf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ab5bec65dc3f53681d40743bea694295ff69944b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugengineprogram2stop"></a>IDebugEngineProgram2::Stop
Arresta tutti i thread in esecuzione in questo programma.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT Stop(   
   void   
);  
```  
  
```csharp  
int Stop();  
```  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo viene chiamato quando viene eseguito il debug di questo programma in un ambiente multi-programma. Quando viene ricevuto un evento di arresto da un altro programma, questo metodo viene chiamato su questo programma. L'implementazione di questo metodo deve essere asincrona; ovvero, non tutti i thread devono essere deve essere arrestato prima di questo metodo restituisce. L'implementazione di questo metodo può essere semplice come chiamare il [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) metodo su questo programma.  
  
 In risposta a questo metodo viene inviato alcun evento di debug.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)