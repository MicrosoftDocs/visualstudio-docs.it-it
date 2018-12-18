---
title: Interfaccia IDebugApplicationThread110 | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThread110 Interface
ms.assetid: 25bc351f-3451-4387-9302-078f6292ddff
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aee30ae68319810f58bf31f8d0eb32cf8f30d34c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationthread110-interface"></a>Interfaccia IDebugApplicationThread110
Fornisce altre funzionalità per il [interfaccia IDebugApplicationThread](../../winscript/reference/idebugapplicationthread-interface.md) interfaccia.  
  
> [!IMPORTANT]
>  Questa interfaccia è implementata da PDM v11.0 e versione successiva. Rilevata in activdbg100.h.  
  
## <a name="methods"></a>Metodi  
 L'interfaccia `IDebugApplicationThread110` espone i metodi riportati di seguito.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugApplicationThread110::AsynchronousCallIntoThread](../../winscript/reference/idebugapplicationthread110-asynchronouscallintothread.md)|Effettua una chiamata asincrona nel thread principale.|  
|[IDebugApplicationThread110::GetActiveThreadRequestCount](../../winscript/reference/idebugapplicationthread110-getactivethreadrequestcount.md)|Conteggio del numero di richieste di thread da thread del PDM cambio meccanismi attualmente in elaborazione. In genere 0 o 1, ma 's possibili per il valore è superiore se una chiamata thread avvia l'elaborazione, ma genera una chiamata sincrona da thread o in caso contrario sospende il thread (ad esempio, per l'attivazione di un evento IDebugApplicationEvents rilasciato del debugger thread)|  
|[IDebugApplicationThread110::IsSuspendedForBreakPoint](../../winscript/reference/idebugapplicationthread110-issuspendedforbreakpoint.md)|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md) è stato chiamato su questo thread e non è ancora stata completata.|  
|[IDebugApplicationThread110::IsThreadCallable](../../winscript/reference/idebugapplicationthread110-isthreadcallable.md)|Il thread è in uno stato in grado di elaborare le chiamate effettuate tramite il thread del PDM cambio meccanismi (ad esempio SynchronousCallInThread).|