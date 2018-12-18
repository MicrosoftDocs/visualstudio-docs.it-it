---
title: Interfaccia IDebugApplicationThread | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThread interface
ms.assetid: f869c328-4409-4b74-a6c3-9e63fc58c63d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6e731ba866504c9a3c3c9ad081a90a12b161355d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationthread-interface"></a>Interfaccia IDebugApplicationThread
Consente di motori di linguaggio e host per fornire la sincronizzazione dei thread e per mantenere informazioni sullo stato di debug specifico del thread. Questa interfaccia estende il `IRemoteDebugApplicationThread` interfaccia per fornire l'accesso non remoti per il thread.  
  
 Oltre ai metodi ereditati da `IRemoteDebugApplicationThread`, `IDebugApplicationThread` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugApplicationThread::SynchronousCallIntoThread](../../winscript/reference/idebugapplicationthread-synchronouscallintothread.md)|Fornisce un meccanismo per il chiamante può eseguire codice nel thread dell'applicazione.|  
|[IDebugApplicationThread::QueryIsCurrentThread](../../winscript/reference/idebugapplicationthread-queryiscurrentthread.md)|Determina se il thread è il thread attualmente in esecuzione.|  
|[IDebugApplicationThread::QueryIsDebuggerThread](../../winscript/reference/idebugapplicationthread-queryisdebuggerthread.md)|Determina se il thread è il thread del debugger.|  
|[IDebugApplicationThread::SetDescription](../../winscript/reference/idebugapplicationthread-setdescription.md)|Imposta la descrizione di questo thread.|  
|[IDebugApplicationThread::SetStateString](../../winscript/reference/idebugapplicationthread-setstatestring.md)|Imposta la descrizione dello stato del thread.|