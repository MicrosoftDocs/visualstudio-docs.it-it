---
title: IEnumDebugPrograms2 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugPrograms2
helpviewer_keywords:
- IEnumDebugPrograms2
ms.assetid: 7fbb8fb7-db64-4546-a364-dc668430c8af
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e1e95996a0548dcf81957dad60c3e6f73b3424c8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="ienumdebugprograms2"></a>IEnumDebugPrograms2
Questa interfaccia consente di enumerare i programmi in esecuzione nella sessione di debug corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IEnumDebugPrograms2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Il motore di debug (DE) implementa questa interfaccia per fornire un elenco dei programmi in fase di debug per la Germania.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Chiamate di Visual Studio [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) per ottenere questa interfaccia. [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md) non viene usato da Visual Studio.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IEnumDebugPrograms2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[avanti](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)|Recupera un numero specificato di programmi in una sequenza di enumerazione.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugprograms2-skip.md)|Ignora un numero specificato di programmi in una sequenza di enumerazione.|  
|[Reimpostazione](../../../extensibility/debugger/reference/ienumdebugprograms2-reset.md)|Reimposta una sequenza di enumerazione all'inizio.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugprograms2-clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione come enumerazione corrente.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprograms2-getcount.md)|Ottiene il numero di programmi in un enumeratore.|  
  
## <a name="remarks"></a>Note  
 Visual Studio Usa questa interfaccia per:  
  
-   Popolare il **moduli** finestra (chiamando [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) e chiamando quindi [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) in ogni programma).  
  
-   Popolare il **Connetti a processo** elenco (chiamando `IDebugProcess2::EnumPrograms` e chiamando quindi [QueryInterface](/cpp/atl/queryinterface) in ogni [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfaccia per ottenere un [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md) interface).  
  
-   Generare un elenco di DEs che è possibile eseguire il debug del processo ogni programma (con [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)).  
  
-   Applicare gli aggiornamenti di modifica e Continuazione per ogni programma (chiamando IDebugProcess2::EnumPrograms e chiamando quindi [GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)).  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)   
 [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)