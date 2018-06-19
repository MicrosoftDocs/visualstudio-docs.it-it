---
title: IDiaLoadCallback | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback interface
ms.assetid: 2f18c64c-2cf0-43fc-a447-21e82702ca2a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fbde460fadf89b27745fd05729fda6736fb3d3d7
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
ms.locfileid: "31466153"
---
# <a name="idialoadcallback"></a>IDiaLoadCallback
Riceve i callback dal simbolo DIA procedura di individuazione, consentendo un'interfaccia utente per creare report sullo stato del tentativo di percorso.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDiaLoadCallback : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 I metodi seguenti sono esposte da questa interfaccia:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDiaLoadCallback::NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md)|Chiamato quando una directory di debug è stata trovata nel file .exe.|  
|[IDiaLoadCallback::NotifyOpenDBG](../../debugger/debug-interface-access/idialoadcallback-notifyopendbg.md)|Chiamata eseguita quando è stato aperto un file DBG candidato.|  
|[IDiaLoadCallback::NotifyOpenPDB](../../debugger/debug-interface-access/idialoadcallback-notifyopenpdb.md)|Chiamata eseguita quando è stato aperto un file con estensione pdb candidato.|  
|[IDiaLoadCallback::RestrictRegistryAccess](../../debugger/debug-interface-access/idialoadcallback-restrictregistryaccess.md)|Determina se le query del Registro di sistema consente di individuare i percorsi di ricerca di simboli.|  
|[IDiaLoadCallback::RestrictSymbolServerAccess](../../debugger/debug-interface-access/idialoadcallback-restrictsymbolserveraccess.md)|Determina se l'accesso viene consentito a un server di simboli per risolvere i simboli.|  
  
## <a name="remarks"></a>Note  
 L'applicazione client implementa questa interfaccia e fornisce un riferimento nella chiamata al [idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) metodo.  
  
 Per ulteriori restrizioni che possono essere imposto a un processo di caricamento, vedere il [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md) interfaccia.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Dia2.h  
  
 Libreria: diaguids.lib  
  
 DLL: MSDIA80  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)