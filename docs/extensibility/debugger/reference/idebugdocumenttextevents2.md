---
title: IDebugDocumentTextEvents2 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDocumentTextEvents2
helpviewer_keywords:
- IDebugDocumentTextEvents2 interface
ms.assetid: a10cbb6b-11a8-4056-b42a-2ecebf0e690d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0f34bb09847659fdfc1dfcbd036aef2a47c8bd5b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugdocumenttextevents2"></a>IDebugDocumentTextEvents2
Questa interfaccia viene utilizzata per notificare le modifiche al documento di origine che vengono fornite dal motore di debug di Visual Studio.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugDocumentTextEvents2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 La Germania implementa questa interfaccia per supportare le modifiche al codice sorgente. Questa interfaccia viene implementata in genere sullo stesso oggetto che implementa il [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interfaccia.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Ottiene l'interfaccia tramite una chiamata al <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> metodo. Il <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interfaccia viene ottenuta da una chiamata al <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A> metodo. Il <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interfaccia viene ottenuta chiamando il [QueryInterface](/cpp/atl/queryinterface) metodo su un [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interfaccia.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugDocumentTextEvents2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[onDestroy](../../../extensibility/debugger/reference/idebugdocumenttextevents2-ondestroy.md)|Indica che è stato eliminato l'intero documento.|  
|[onInsertText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-oninserttext.md)|Notifica il pacchetto di debug che il testo è stato inserito nel documento.|  
|[onRemoveText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onremovetext.md)|Notifica il pacchetto di debug che il testo è stato rimosso dal documento.|  
|[onReplaceText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onreplacetext.md)|Notifica il pacchetto di debug che è stato sostituito il testo nel documento.|  
|[onUpdateTextAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes.md)|Notifica il pacchetto di debug che sono stati aggiornati gli attributi di testo nel documento.|  
|[onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)|Notifica al destinatario dell'evento che sono stati aggiornati gli attributi del documento.|  
  
## <a name="remarks"></a>Note  
 Solo i motori di debug che forniscono i propri documenti potrebbero sfruttare il `IDebugDocumentTextEvent2` interfaccia. Un esempio di questo sarebbe un motore di debug di script. In corso l'interpretazione degli script, può essere generato il nuovo codice sorgente che non è presente in qualsiasi file su disco ed è noto solo per la Germania.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)