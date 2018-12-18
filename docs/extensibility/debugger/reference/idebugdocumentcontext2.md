---
title: IDebugDocumentContext2 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDocumentContext2
helpviewer_keywords:
- IDebugDocumentContext2
ms.assetid: 2a446c71-8100-4c09-a1cc-fd446bd74030
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 06ff06086c0f293f70af7d9570cf72df4be85608
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugdocumentcontext2"></a>IDebugDocumentContext2
Questa interfaccia rappresenta una posizione in un documento di file di origine.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugDocumentContext2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Il motore di debug (DE) implementa l'interfaccia specificata come parte del supporto per il debug livello code di origine. Oltre a una posizione nel codice sorgente, questa interfaccia fornisce metodi per il confronto dei contesti e spostarsi tra un documento di codice sorgente.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Metodi in diverse interfacce, generalmente il [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) e [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) interfacce, tornare a questa interfaccia.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugDocumentContext2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)|Ottiene il documento che contiene il contesto di questo documento.|  
|[GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)|Ottiene il nome del documento che contiene il contesto di questo documento visualizzabile.|  
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)|Recupera un elenco di tutti i contesti di codice associato al contesto di documento.|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugdocumentcontext2-getlanguageinfo.md)|Ottiene la lingua associata a questo contesto di documento.|  
|[GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Ottiene l'intervallo di istruzione del file di questo contesto di documento.|  
|[GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)|Ottiene l'intervallo di origine del file di questo contesto di documento.|  
|[Compare](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)|Confronta questo contesto di documento in una matrice specificata di contesti di documento.|  
|[Ricerca](../../../extensibility/debugger/reference/idebugdocumentcontext2-seek.md)|Sposta il contesto del documento da un determinato numero di istruzioni o le righe.|  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)