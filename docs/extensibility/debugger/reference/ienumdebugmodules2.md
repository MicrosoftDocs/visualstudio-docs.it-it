---
title: IEnumDebugModules2 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugModules2
helpviewer_keywords:
- IEnumDebugModules2
ms.assetid: 4fe28074-a960-41ad-b74d-b57f04c0c0ad
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dd3ca02776aae4a7b4cd22485eba9827f4731d5d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="ienumdebugmodules2"></a>IEnumDebugModules2
Questa interfaccia enumera un elenco dei moduli.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IEnumDebugModules2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Il motore di debug (DE) implementa questa interfaccia per rappresentare un elenco di moduli caricati per un programma.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Chiamate di Visual Studio [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) per ottenere questa interfaccia.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IEnumDebugModules2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[avanti](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md)|Recupera un numero specificato di moduli in una sequenza di enumerazione.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugmodules2-skip.md)|Ignora un numero specificato di moduli in una sequenza di enumerazione.|  
|[Reimpostazione](../../../extensibility/debugger/reference/ienumdebugmodules2-reset.md)|Reimposta una sequenza di enumerazione all'inizio.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugmodules2-clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione come enumerazione corrente.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugmodules2-getcount.md)|Ottiene il numero di moduli.|  
  
## <a name="remarks"></a>Note  
 Visual Studio Usa questa interfaccia principalmente per aggiornare il **moduli** finestra.  
  
 Ai fini di debug in Visual Studio, un programma è una sequenza logica di istruzioni di codice che possono attraversare i limiti di modulo, pertanto la necessità di un elenco di moduli per una singola [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfaccia. Il primo modulo nell'elenco contiene in genere il punto di ingresso iniziale per il programma associato.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)