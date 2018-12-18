---
title: Interfaccia IActiveScriptSiteDebugEx | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IActiveScriptSiteDebugEx Interface
ms.assetid: 76869378-1a7b-47bd-8cd0-acc31f91d58d
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2cf5849ff1fca282bace97774c6b7ac9e4510226
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitedebugex-interface"></a>Interfaccia IActiveScriptSiteDebugEx
Implementare questa interfaccia con il `IActiveScriptSiteDebug` interfaccia se si sta scrivendo un host che è necessario ottenere una notifica di errore di run-time in un'applicazione e, facoltativamente, connettersi all'applicazione per il debug. Il processo di Debug Manager fornisce una notifica tramite `IActiveScriptDebug` se Just In Time debugger di script non viene trovato nel computer. Se il debugger di script non Just-In-Time viene trovato, PDM fornisce una notifica tramite `IActiveScriptDebugEx` invece.  
  
 Per ottenere una notifica di errore di run-time, è necessario gestire l'host [ActiveScriptSiteDebug::OnScriptErrorDebug](http://msdn.microsoft.com/en-us/cf7639f9-a699-4571-9f3a-82ef52c0b5f4). In base a un'azione dell'utente, è possibile quindi decidere se si desidera collegare il debugger interno e tornare, o per restituire l'avvio del debugger nel OnScriptErrorDebug `pfEnterDebugger` parametro.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug](../../winscript/reference/iactivescriptsitedebugex-oncannotjitscripterrordebug.md)|Informa l'host su un errore in fase di esecuzione di script quando il processo di gestione esegue il Debug non viene trovato un debugger JIT esterno.|