---
title: Interfaccia IRemoteDebugApplication110 | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplication110 Interface
ms.assetid: 785ab46a-8827-41cb-806a-132e6b2c8f47
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d384cea22b79b2a7ca9af3424d053fb3062d79a3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplication110-interface"></a>Interfaccia IRemoteDebugApplication110
Utilizzato per fornire nuove funzionalità che possono essere chiamate dai debugger di script e i chiamanti in-process.  
  
> [!IMPORTANT]
>  Questa interfaccia è implementata da PDM v11.0 e versione successiva. Rilevata in activdbg100.h.  
  
## <a name="methods"></a>Metodi  
 L'interfaccia `IRemoteDebugApplication110` espone i metodi riportati di seguito.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IRemoteDebugApplication110::SetDebuggerOptions](../../winscript/reference/iremotedebugapplication110-setdebuggeroptions.md)|Chiamato per aggiornare le opzioni del debugger. Il valore predefinito di opzioni a 0 (SDO_NONE).|  
|[IRemoteDebugApplication110::GetCurrentDebuggerOptions](../../winscript/reference/iremotedebugapplication110-getcurrentdebuggeroptions.md)|Restituisce il set corrente delle opzioni che sono abilitati.|  
|[IRemoteDebugApplication110::GetMainThread](../../winscript/reference/iremotedebugapplication110-getmainthread.md)|Restituisce il thread principale per gli host che chiamano SetSite.|