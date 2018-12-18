---
title: Interfaccia IRemoteDebugApplicationEx | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplicationEx Interface
ms.assetid: 8e16164d-dbb2-4488-9507-25ae34f343dc
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3360cea0d1649348a795356ad827b32b6f8ebc19
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplicationex-interface"></a>Interfaccia IRemoteDebugApplicationEx
Rappresenta un'applicazione in esecuzione. Se è necessario che corrispondono a un processo del sistema operativo. In genere, un debugger è destinato a un'applicazione per il debug. In genere, il gestore di eseguire il Debug di processi implementa l'oggetto applicazione.  
  
 Oltre ai metodi ereditati da `IUnknown`, `IRemoteDebugApplicationEx` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IRemoteDebugApplicationEx:GetHostPid](../../winscript/reference/iremotedebugapplicationex-gethostpid.md)|Restituisce l'ID di processo per l'applicazione host.|  
|GetHostMachineName|Restituisce il nome del computer in cui è in esecuzione l'applicazione host.|  
|[IRemoteDebugApplicationEx:SetLocale](../../winscript/reference/iremotedebugapplicationex-setlocale.md)|Imposta la lingua per la localizzazione del debugger.|  
|[IRemoteDebugApplicationEx:ForceStepMode](../../winscript/reference/iremotedebugapplicationex-forcestepmode.md)|Forza il debugger in modalità passo a passo.|  
|[IRemoteDebugApplicationEx:RevokeBreak](../../winscript/reference/iremotedebugapplicationex-revokebreak.md)|Revoca di un comando di interruzione.|  
|SetProxyBlanketAndAddRef|Aggiorna le informazioni di sicurezza COM su un proxy per un oggetto debugger per garantire la compatibilità con il debug remoto da sistemi operativi basati su Windows 95.|  
|ReleaseFromSetProxyBlanket|AddRef versioni da SetProxyBlanketAndAddRef.|