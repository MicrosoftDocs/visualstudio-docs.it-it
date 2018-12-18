---
title: Interfaccia IDebugApplication | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugApplication interface
ms.assetid: 5dfa941b-4cd9-46fa-a230-3f41df9ea205
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 07964292785634212099a0bfcf8174ebb55e8713
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplication-interface"></a>Interfaccia IDebugApplication
Espone i metodi di debug non remoti per l'utilizzo con gli host e motori di linguaggio.  
  
 Oltre ai metodi ereditati da `IRemoteDebugApplication`, `IDebugApplication` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugApplication::SetName](../../winscript/reference/idebugapplication-setname.md)|Imposta il nome dell'applicazione.|  
|[IDebugApplication::StepOutComplete](../../winscript/reference/idebugapplication-stepoutcomplete.md)|Notifica al gestore di debug di processo che un motore di lingua in modalità passo a passo sta per restituire al chiamante.|  
|[IDebugApplication::DebugOutput](../../winscript/reference/idebugapplication-debugoutput.md)|Fa sì che la stringa specificata da visualizzare tramite il debugger IDE.|  
|[IDebugApplication::StartDebugSession](../../winscript/reference/idebugapplication-startdebugsession.md)|Avvia il debugger predefinito IDE e connette una sessione di debug per questa applicazione, se non è ancora stato connesso.|  
|[IDebugApplication::HandleBreakPoint](../../winscript/reference/idebugapplication-handlebreakpoint.md)|Causa il blocco del thread corrente e invia una notifica del punto di interruzione nel debugger IDE.|  
|[IDebugApplication::Close](../../winscript/reference/idebugapplication-close.md)|Fa sì che l'applicazione per rilasciare tutti i riferimenti e immettere uno stato inattivo.|  
|[IDebugApplication::GetBreakFlags](../../winscript/reference/idebugapplication-getbreakflags.md)|Restituisce i flag di interruzione corrente per l'applicazione.|  
|[IDebugApplication::GetCurrentThread](../../winscript/reference/idebugapplication-getcurrentthread.md)|Restituisce il thread associato al thread attualmente in esecuzione.|  
|[IDebugApplication::CreateAsyncDebugOperation](../../winscript/reference/idebugapplication-createasyncdebugoperation.md)|Fornisce l'accesso asincrono a un'operazione di debug sincrono specificato.|  
|[IDebugApplication::AddStackFrameSniffer](../../winscript/reference/idebugapplication-addstackframesniffer.md)|Aggiunge un provider di enumeratore di frame dello stack per questa applicazione.|  
|[IDebugApplication::RemoveStackFrameSniffer](../../winscript/reference/idebugapplication-removestackframesniffer.md)|Rimuove un provider di enumeratore di stack frame da questa applicazione.|  
|[IDebugApplication::QueryCurrentThreadIsDebuggerThread](../../winscript/reference/idebugapplication-querycurrentthreadisdebuggerthread.md)|Determina se il thread corrente in esecuzione il thread del debugger.|  
|[IDebugApplication::SynchronousCallInDebuggerThread](../../winscript/reference/idebugapplication-synchronouscallindebuggerthread.md)|Fornisce un meccanismo per il chiamante eseguire il codice nel thread del debugger.|  
|[IDebugApplication::CreateApplicationNode](../../winscript/reference/idebugapplication-createapplicationnode.md)|Crea un nuovo nodo di applicazione associata a un provider di documento specifico.|  
|[IDebugApplication::FireDebuggerEvent](../../winscript/reference/idebugapplication-firedebuggerevent.md)|Viene generato un evento generico per il debugger `IApplicationDebugger` interfaccia.|  
|[IDebugApplication::HandleRuntimeError](../../winscript/reference/idebugapplication-handleruntimeerror.md)|Causa il blocco del thread corrente e invia una notifica dell'errore per il debugger IDE.|  
|[IDebugApplication::FCanJitDebug](../../winscript/reference/idebugapplication-fcanjitdebug.md)|Determina se un debugger di just-in-time (JIT) è registrato.|  
|[IDebugApplication::FIsAutoJitDebugEnabled](../../winscript/reference/idebugapplication-fisautojitdebugenabled.md)|Determina se un debugger JIT è registrato con host dumb auto-debug.|  
|[IDebugApplication::AddGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-addglobalexpressioncontextprovider.md)|Aggiunge un provider di contesto dell'espressione globale a questa applicazione.|  
|[IDebugApplication::RemoveGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-removeglobalexpressioncontextprovider.md)|Rimuove un provider di contesto dell'espressione globale da questa applicazione.|