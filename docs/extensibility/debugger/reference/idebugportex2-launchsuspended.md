---
title: IDebugPortEx2::LaunchSuspended | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPortEx2::LaunchSuspended
helpviewer_keywords:
- IDebugPortEx2::LaunchSuspended
ms.assetid: 34b2cf99-2e52-4757-8969-1d12ac517ec0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9f22afc50a1a2874d4853acbf9ff72cae622e790
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugportex2launchsuspended"></a>IDebugPortEx2::LaunchSuspended
Avvia un file eseguibile.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT LaunchSuspended(   
   LPCOLESTR        pszExe,  
   LPCOLESTR        pszArgs,  
   LPCOLESTR        pszDir,  
   BSTR             bstrEnv,  
   DWORD            hStdInput,  
   DWORD            hStdOutput,  
   DWORD            hStdError,  
   IDebugProcess2** ppPortProcess  
);  
```  
  
```csharp  
int LaunchSuspended(   
   string             pszExe,  
   string             pszArgs,  
   string             pszDir,  
   string             bstrEnv,  
   uint               hStdInput,  
   uint               hStdOutput,  
   uint               hStdError,  
   out IDebugProcess2 ppPortProcess  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pszExe`  
 [in] Il nome del file eseguibile da avviare. Può trattarsi di un percorso completo o relativo rispetto alla directory di lavoro specificata nella `pszDir` parametro.  
  
 `pszArgs`  
 [in] Gli argomenti da passare al file eseguibile. Può essere un valore null se non sono presenti argomenti.  
  
 `pszDir`  
 [in] Il nome della directory di lavoro utilizzata dal file eseguibile. Può essere un valore null se non è necessaria alcuna directory di lavoro.  
  
 `bstrEnv`  
 [in] Blocco di ambiente di stringhe con terminazione null, seguito da un terminatore NULL aggiuntivo.  
  
 `hStdInput`  
 [in] Handle per un flusso di input alternativo. Può essere 0 se il reindirizzamento non è necessario.  
  
 `hStdOutput`  
 [in] Handle per un flusso di output alternativo. Può essere 0 se il reindirizzamento non è necessario.  
  
 `hStdError`  
 [in] Handle per un flusso di output di errore alternativa. Può essere 0 se il reindirizzamento non è necessario.  
  
 `ppPortProcess`  
 [out] Restituisce un [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) oggetto che rappresenta il processo avviato.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo deve essere avviato il processo in modo che non viene sospesa e non è in esecuzione alcun codice. Il [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md) metodo viene chiamato per riprendere il processo.  
  
 Un programma può anche essere avviato da un motore di debug. Per informazioni dettagliate, vedere [avviando un programma](../../../extensibility/debugger/launching-a-program.md).  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)   
 [Avvio di un programma](../../../extensibility/debugger/launching-a-program.md)