---
title: IDebugProviderProgramNode2 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProviderProgramNode2
helpviewer_keywords:
- IDebugProviderProgramNode2
ms.assetid: f0bca1cc-afbe-44cf-b5aa-d078aa685d24
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6057371838854755985d2ff570f11eefdeb3b222
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugproviderprogramnode2"></a>IDebugProviderProgramNode2
Questa interfaccia effettua il marshalling delle interfacce correlate al programma attraverso i limiti di processo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugProviderProgramNode2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Il motore di debug (DE) implementa questa interfaccia sullo stesso oggetto che implementa [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) per supportare le interfacce di marshalling attraverso i limiti di processo.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Chiamare [QueryInterface](/cpp/atl/queryinterface) su un `IDebugProgramNode2` interfaccia per ottenere questa interfaccia. Se non è possibile ottenere questa interfaccia, la Germania non supporta il marshalling delle interfacce.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Questa interfaccia implementa il metodo seguente:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[UnmarshalDebuggeeInterface](../../../extensibility/debugger/reference/idebugproviderprogramnode2-unmarshaldebuggeeinterface.md)|Ottiene un'interfaccia specificata nell'ambito dei processi.|  
  
## <a name="remarks"></a>Note  
 Questa interfaccia viene implementata quando la Germania viene eseguito in uno spazio di processo separato dal programma sottoposto a debug: ad esempio, quando la Germania è in esecuzione nello spazio di processo Visual Studio anziché lo spazio di processo del programma sottoposto a debug.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)