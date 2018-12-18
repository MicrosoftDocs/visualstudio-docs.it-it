---
title: IEnumDebugCodeContexts2 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugCodeContexts2
helpviewer_keywords:
- IEnumDebugCodeContexts2
ms.assetid: 72915146-215f-4c99-a034-131b2b474e0e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dc6ff9a173bcfbb87606fe493697857d7ec2b323
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="ienumdebugcodecontexts2"></a>IEnumDebugCodeContexts2
Questa interfaccia consente di enumerare i contesti di codice associati, la sessione di debug o con un particolare programma o il documento.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IEnumDebugCodeContexts2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Il motore di debug (DE) implementa questa interfaccia per rappresentare un elenco di contesti di codice per una posizione di testo specifico in un programma, o un elenco di contesti di codice per un contesto di un documento specifico.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Chiamare [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) per ottenere l'interfaccia che rappresenta un elenco di contesti di codice per una posizione di un testo specifico nel documento di origine del programma.  
  
 Chiamare [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md) per ottenere l'interfaccia che rappresenta un elenco di tutti i contesti di codice in un documento di origine specifico.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IEnumDebugCodeContexts2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[avanti](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)|Recupera un numero di contesti di codice in una sequenza di enumerazione specificato.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-skip.md)|Ignora un numero di contesti di codice in una sequenza di enumerazione specificato.|  
|[Reimpostazione](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-reset.md)|Reimposta una sequenza di enumerazione all'inizio.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione come enumerazione corrente.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-getcount.md)|Ottiene il numero di contesti di codice in un enumeratore.|  
  
## <a name="remarks"></a>Note  
 Chiamate di Visual Studio [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) per popolare un elenco di contesti di codice l'utente può scegliere quando visualizzare o impostare l'istruzione successiva il disassembly per un file di origine. Più contesti di codice possono verificarsi, ad esempio, quando sono presenti più istanze di un modello di stile di C++.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)   
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)