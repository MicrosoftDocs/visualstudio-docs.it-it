---
title: Interfaccia IRemoteDebugApplication | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IRemoteDebugApplication interface
ms.assetid: 96bf2a3f-049f-46ba-86ad-57fc184343a2
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ea91afdc44b70a91846d7b1a3dc4c017c0c4c80e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplication-interface"></a>Interfaccia IRemoteDebugApplication
Rappresenta un'applicazione in esecuzione. Se è necessario che corrispondono a un processo del sistema operativo. In genere, un debugger è destinato a un'applicazione per il debug. In genere, il gestore di eseguire il Debug di processi implementa l'oggetto applicazione.  
  
 Oltre ai metodi ereditati da `IUnknown`, `IRemoteDebugApplication` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IRemoteDebugApplication::ResumeFromBreakPoint](../../winscript/reference/iremotedebugapplication-resumefrombreakpoint.md)|Continua un'applicazione che si trova in un punto di interruzione.|  
|[IRemoteDebugApplication::CauseBreak](../../winscript/reference/iremotedebugapplication-causebreak.md)|Fa sì che l'applicazione di interrompere il debugger al più presto.|  
|[IRemoteDebugApplication::ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md)|Si connette un debugger all'applicazione.|  
|[IRemoteDebugApplication::DisconnectDebugger](../../winscript/reference/iremotedebugapplication-disconnectdebugger.md)|Disconnette il debugger corrente dall'applicazione.|  
|[IRemoteDebugApplication::GetDebugger](../../winscript/reference/iremotedebugapplication-getdebugger.md)|Restituisce il debugger corrente è connesso all'applicazione.|  
|[IRemoteDebugApplication::CreateInstanceAtApplication](../../winscript/reference/iremotedebugapplication-createinstanceatapplication.md)|Fornisce un meccanismo per il debugger IDE, l'esecuzione out-of-process all'applicazione, per creare oggetti nel processo dell'applicazione.|  
|[IRemoteDebugApplication::QueryAlive](../../winscript/reference/iremotedebugapplication-queryalive.md)|Indica se l'applicazione è reattiva.|  
|[IRemoteDebugApplication::EnumThreads](../../winscript/reference/iremotedebugapplication-enumthreads.md)|Enumera tutti i thread noti da associare all'applicazione.|  
|[IRemoteDebugApplication::GetName](../../winscript/reference/iremotedebugapplication-getname.md)|Restituisce il nome del nodo dell'applicazione.|  
|[IRemoteDebugApplication::GetRootNode](../../winscript/reference/iremotedebugapplication-getrootnode.md)|Restituisce il nodo dell'applicazione in cui vengono aggiunti tutti i nodi associati all'applicazione.|  
|[IRemoteDebugApplication::EnumGlobalExpressionContexts](../../winscript/reference/iremotedebugapplication-enumglobalexpressioncontexts.md)|Enumera i contesti di espressione globale per tutte le lingue in esecuzione in questa applicazione.|