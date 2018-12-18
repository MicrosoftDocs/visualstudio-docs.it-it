---
title: Interfaccia IApplicationDebugger | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IApplicationDebugger interface
ms.assetid: 27f6f8f5-2bf3-49bc-8abb-dfca98935aba
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a16cd1bc891c7d682cc1097cd1b6cb5efd5438db
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iapplicationdebugger-interface"></a>Interfaccia IApplicationDebugger
L'interfaccia primaria esposto da un debugger. Oltre ai metodi ereditati da `IUnknown`, `IApplicationDebugger` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IApplicationDebugger::QueryAlive](../../winscript/reference/iapplicationdebugger-queryalive.md)|Indica se il debugger è reattivo.|  
|[IApplicationDebugger::CreateInstanceAtDebugger](../../winscript/reference/iapplicationdebugger-createinstanceatdebugger.md)|Consente la creazione di oggetti nel processo del debugger per codice che è out-of-process al debugger.|  
|[IApplicationDebugger::onDebugOutput](../../winscript/reference/iapplicationdebugger-ondebugoutput.md)|Gestisce un evento di output di debug.|  
|[IApplicationDebugger::onHandleBreakPoint](../../winscript/reference/iapplicationdebugger-onhandlebreakpoint.md)|Gestisce l'evento punto di interruzione.|  
|[IApplicationDebugger::onClose](../../winscript/reference/iapplicationdebugger-onclose.md)|Gestisce un evento di chiusura dell'applicazione di debug.|  
|[IApplicationDebugger::onDebuggerEvent](../../winscript/reference/iapplicationdebugger-ondebuggerevent.md)|Gestisce l'evento applicazione personalizzata.|