---
title: IDebugBeforeSymbolSearchEvent2 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugBeforeSymbolSearchEvent2 interface
ms.assetid: 679fd7b1-765a-41a8-a046-63240c09a499
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 790aa358a40c79c7d517935192fd0155150063a5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugbeforesymbolsearchevent2"></a>IDebugBeforeSymbolSearchEvent2
Il motore di debug (DE) invia questa interfaccia per la gestione di debug (SDM) per impostare lo stato di sessione barra messaggio durante il caricamento di simboli.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugBeforeSymbolSearchEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 La Germania implementa questa interfaccia quando è necessario impostare il messaggio sulla barra di stato durante il caricamento di simboli. Questa interfaccia è implementata solo dai motori di debug che utilizzano o fanno parte di interpreti di script. Il [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaccia deve essere implementata sullo stesso oggetto di questa interfaccia (utilizza il SDM **QueryInterface** per l'accesso di **IDebugEvent2** interfaccia).  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 La Germania crea e invia l'oggetto evento quando è necessario impostare il messaggio sulla barra di stato durante il caricamento di simboli. L'evento viene inviato tramite il [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) funzione di callback fornita dal suo SDM quando è collegato al programma sottoposto a debug.  
  
## <a name="methods"></a>Metodi  
 Nella tabella seguente sono illustrati i metodi di `IDebugBeforeSymbolSearchEvent2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetModuleName](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2-getmodulename.md)|Recupera il nome del modulo in fase di debug.|  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll