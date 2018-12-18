---
title: IDebugDocument2 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDocument2
helpviewer_keywords:
- IDebugDocument2 interface
ms.assetid: 1bc58426-dbf5-4471-9aad-9d66cd80eef0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 36ac127e6cd6e25fd42c4859e723c883ecaffa82
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugdocument2"></a>IDebugDocument2
Questa interfaccia rappresenta un documento di origine.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugDocument2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] in genere implementa questa interfaccia. Un motore di debug (DE) può anche implementare questa interfaccia quando è necessario fornire il codice sorgente e l'origine non esiste nel disco.  In questi casi, è necessario implementare anche la Germania [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) e [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md) interfacce, nonché alcuni metodi aggiuntivi nel [ IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) e [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) interfacce.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Metodi di `IDebugDocumentContext2`, `IDebugDisassemblyStream2`, `IDebugDocumentPosition2`, e `IDebugActivateDocumentEvent2` interfacce restituire questa interfaccia.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugDocument2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)|Ottiene il nome del documento in uno dei formati diversi.|  
|[GetDocumentClassID](../../../extensibility/debugger/reference/idebugdocument2-getdocumentclassid.md)|Ottiene l'identificatore di classe del documento.|  
  
## <a name="remarks"></a>Note  
 Questa interfaccia è implementata solo quando la Germania fornisce il codice sorgente. Ad esempio, quando si esegue il debug di script in una pagina HTML, la Germania fornisce il codice sorgente perché l'origine venga scaricato o generato in modo dinamico e non esiste come un file su disco. Durante il debug lingue tradizionali, ad esempio C++, non è necessario implementare questa interfaccia.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)