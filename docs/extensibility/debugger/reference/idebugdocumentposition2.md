---
title: IDebugDocumentPosition2 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDocumentPosition2
helpviewer_keywords:
- IDebugDocumentPosition2 interface
ms.assetid: 0e838ced-12bb-4efc-b811-2b7c034b77b0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d685a59dd9404f48cfbdf9ae72e1fa07ba0d0625
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugdocumentposition2"></a>IDebugDocumentPosition2
Questa interfaccia rappresenta una posizione in un file di origine astratta.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugDocumentPosition2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Visual Studio è in genere implementa questa interfaccia. Un motore di debug (DE) necessario implementare questa interfaccia anche se è necessario fornire il proprio codice sorgente (come quando la Germania implementa il [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interface).  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Questa interfaccia viene passata come argomento di [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md). Viene indicato anche come parte di un [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) union (in particolare, un [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) struttura) che a sua volta fa parte di [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) struttura, che viene utilizzata per creare un punto di interruzione in sospeso.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugDocumentPosition2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetFileName](../../../extensibility/debugger/reference/idebugdocumentposition2-getfilename.md)|Ottiene il nome del file del file di origine che contiene la posizione del documento.|  
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)|Ottiene il documento contenitore.|  
|[IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)|Determina se questa posizione è contenuta nel documento specificato.|  
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)|Ottiene l'intervallo per la posizione del documento.|  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)