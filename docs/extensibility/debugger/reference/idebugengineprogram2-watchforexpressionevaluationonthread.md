---
title: IDebugEngineProgram2::WatchForExpressionEvaluationOnThread | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
helpviewer_keywords: IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
ms.assetid: 01d05e77-8cac-4d1b-b19f-25756767ed27
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e40af42d1dd639b80ffac3e2f3cf9c4501782b45
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugengineprogram2watchforexpressionevaluationonthread"></a>IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
Consente o non consente la valutazione dell'espressione a cui si verificano sul thread specificato, anche se il programma è stato arrestato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT WatchForExpressionEvaluationOnThread(   
   IDebugProgram2*       pOriginatingProgram,  
   DWORD                 dwTid,  
   DWORD                 dwEvalFlags,  
   IDebugEventCallback2* pExprCallback,  
   BOOL                  fWatch  
);  
```  
  
```csharp  
int WatchForExpressionEvaluationOnThread(   
   IDebugProgram2       pOriginatingProgram,  
   uint                  dwTid,  
   uint                  dwEvalFlags,  
   IDebugEventCallback2 pExprCallback,  
   int                   fWatch  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pOriginatingProgram`  
 [in] Un [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) oggetto che rappresenta il programma che si sta valutando un'espressione.  
  
 `dwTid`  
 [in] Specifica l'identificatore del thread.  
  
 `dwEvalFlags`  
 [in] Una combinazione di flag dal [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) enumerazione che specificano la modalità è necessario eseguire la valutazione.  
  
 `pExprCallback`  
 [in] Un [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) oggetto da utilizzare per inviare gli eventi di debug che si verificano durante la valutazione dell'espressione.  
  
 `fWatch`  
 [in] Se diverso da zero (`TRUE`), consente la valutazione dell'espressione nel thread identificato da `dwTid`; in caso contrario, zero (`FALSE`) non consente la valutazione dell'espressione in tale thread.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Quando il gestore di debug di sessione (SDM) richiede un programma, identificato dal `pOriginatingProgram` parametro, per valutare un'espressione, invia una notifica a tutti gli altri programmi collegati chiamando questo metodo.  
  
 Valutazione dell'espressione in un programma potrebbe eseguire in un altro, a causa di valutazione della funzione o di valutazione di qualsiasi codice `IDispatch` proprietà. Per questo motivo, questo metodo consente di valutazione delle espressioni eseguire e completare anche se il thread potrebbe essere stato arrestato in questo programma.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)