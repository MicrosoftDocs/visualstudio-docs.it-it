---
title: IEnumDebugPorts2 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugPorts2
helpviewer_keywords:
- IEnumDebugPorts2
ms.assetid: 1754eef3-cf62-42e0-b218-1911acba77d4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 07018391b51424b65bf1e8b9040f637f6f22213e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="ienumdebugports2"></a>IEnumDebugPorts2
Questa interfaccia consente di enumerare le porte di un fornitore di computer o la porta.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IEnumDebugPorts2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Un fornitore di porta personalizzato implementa questa interfaccia per rappresentare un elenco delle porte create dal fornitore. Visual Studio implementa questa interfaccia per supportare il proprio fornitore di porta.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Chiamare [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) per ottenere l'interfaccia che rappresenta un elenco delle porte create per il fornitore della porta. Chiamare [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md) per ottenere l'interfaccia che rappresenta un elenco di porte che sono state salvate su disco.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IEnumDebugPorts2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[avanti](../../../extensibility/debugger/reference/ienumdebugports2-next.md)|Recupera un numero di porte in una sequenza di enumerazione specificato.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugports2-skip.md)|Ignora un numero di porte in una sequenza di enumerazione specificato.|  
|[Reimpostazione](../../../extensibility/debugger/reference/ienumdebugports2-reset.md)|Reimposta una sequenza di enumerazione all'inizio.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugports2-clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione come enumerazione corrente.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugports2-getcount.md)|Ottiene il numero di porte in un enumeratore.|  
  
## <a name="remarks"></a>Note  
 Visual Studio Usa questa interfaccia per popolare un elenco di porte usate per la connessione a processi.  
  
 In genere, un motore di debug non utilizza questa interfaccia.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)   
 [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)