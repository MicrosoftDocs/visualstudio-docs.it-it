---
title: IDebugModule3 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugModule3
helpviewer_keywords:
- IDebugModule3 interface
ms.assetid: 44f8e96e-9c59-4ffc-9a08-9c908a0e4de7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0b74063aa73db8258b2986ac1310d02e36027bf6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugmodule3"></a>IDebugModule3
Questa interfaccia rappresenta un modulo che supporta percorsi alternativi di simboli e JustMyCode stati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugModule3 : IDebugModule2  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Il motore di debug (DE) implementa questa interfaccia per supportare le posizioni alternative di simboli e lavorare con gli stati JustMyCode (vedere il [glossario di Visual Studio Debugger](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md) per una definizione di "JustMyCode").  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Una chiamata a [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md) restituisce questa interfaccia. Invia il DE la [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) interfaccia per la gestione di debug della sessione (SDM) utilizzando il [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) (metodo). Inoltre, una chiamata a [QueryInterface](/cpp/atl/queryinterface) su un [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) interfaccia restituisce questa interfaccia.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Oltre ai metodi nel [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) interfaccia, implementa i metodi seguenti:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)|Restituisce un elenco di percorsi di ricerca per i simboli e i risultati di ogni percorso di ricerca.|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)|Carica e inizializza i simboli per il modulo corrente.|  
|[IsUserCode](../../../extensibility/debugger/reference/idebugmodule3-isusercode.md)|Restituisce flag che specifica se il modulo rappresenta il codice utente.|  
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugmodule3-setjustmycodestate.md)|Specifica se il modulo deve essere considerato codice utente o non.|  
  
## <a name="remarks"></a>Note  
 Visual Studio è il consumer tipico di questa interfaccia.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)   
 [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)