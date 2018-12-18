---
title: IDebugEngineLaunch2::LaunchSuspended | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngineLaunch2::LaunchSuspended
helpviewer_keywords: IDebugEngineLaunch2::LaunchSuspended
ms.assetid: 5dd2643e-c20a-470e-9024-2a423eb39856
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: b9c05a566c62df63ebabebab287188011e4f1ca5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugenginelaunch2launchsuspended"></a>IDebugEngineLaunch2::LaunchSuspended
Questo metodo avvia un processo tramite il motore di debug (DE).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT LaunchSuspended (   
   LPCOLESTR             pszMachine,  
   IDebugPort2*          pPort,  
   LPCOLESTR             pszExe,  
   LPCOLESTR             pszArgs,  
   LPCOLESTR             pszDir,  
   BSTR                  bstrEnv,  
   LPCOLESTR             pszOptions,  
   LAUNCH_FLAGS          dwLaunchFlags,  
   DWORD                 hStdInput,  
   DWORD                 hStdOutput,  
   DWORD                 hStdError,  
   IDebugEventCallback2* pCallback,  
   IDebugProcess2**      ppDebugProcess  
);  
```  
  
```csharp  
int LaunchSuspended(  
   string               pszServer,   
   IDebugPort2          pPort,   
   string               pszExe,   
   string               pszArgs,   
   string               pszDir,   
   string               bstrEnv,   
   string               pszOptions,   
   enum_LAUNCH_FLAGS    dwLaunchFlags,   
   uint                 hStdInput,   
   uint                 hStdOutput,   
   uint                 hStdError,  
   IDebugEventCallback2 pCallback,   
   out IDebugProcess2   ppProcess  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pszMachine`  
 [in] Il nome del computer in cui si desidera avviare il processo. Utilizzare un valore null per specificare il computer locale.  
  
 `pPort`  
 [in] Il [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interfaccia che rappresenta la porta a cui verrà eseguito il programma.  
  
 `pszExe`  
 [in] Il nome del file eseguibile da avviare.  
  
 `pszArgs`  
 [in] Gli argomenti da passare al file eseguibile. Può essere un valore null se non sono presenti argomenti.  
  
 `pszDir`  
 [in] Il nome della directory di lavoro utilizzata dal file eseguibile. Può essere un valore null se non è necessaria alcuna directory di lavoro.  
  
 `bstrEnv`  
 [in] Blocco di ambiente di stringhe con terminazione NULL, seguito da un terminatore NULL aggiuntivo.  
  
 `pszOptions`  
 [in] Le opzioni per il file eseguibile.  
  
 `dwLaunchFlags`  
 [in] Specifica il [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md) per una sessione.  
  
 `hStdInput`  
 [in] Handle per un flusso di input alternativo. Può essere 0 se il reindirizzamento non è necessario.  
  
 `hStdOutput`  
 [in] Handle per un flusso di output alternativo. Può essere 0 se il reindirizzamento non è necessario.  
  
 `hStdError`  
 [in] Handle per un flusso di output di errore alternativa. Può essere 0 se il reindirizzamento non è necessario.  
  
 `pCallback`  
 [in] Il [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) oggetto che riceve gli eventi del debugger.  
  
 `ppDebugProcess`  
 [out] Restituisce il valore risultante [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) oggetto che rappresenta il processo avviato.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 In genere, [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] avvia un programma tramite la [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) (metodo) e quindi connettere il debugger al programma sospeso. Tuttavia, esistono casi in cui potrebbe essere necessario avviare un programma (ad esempio, se il motore di debug fa parte di un interprete e il programma in fase di debug è un linguaggio interpretato), nel qual caso il motore di debug [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] utilizza il `IDebugEngineLaunch2::LaunchSuspended` (metodo) .  
  
 Il [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md) metodo viene chiamato per avviare il processo dopo il processo è stato avviato in uno stato sospeso.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)   
 [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)