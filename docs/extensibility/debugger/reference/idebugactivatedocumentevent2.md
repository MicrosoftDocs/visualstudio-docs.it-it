---
title: IDebugActivateDocumentEvent2 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugActivateDocumentEvent2
helpviewer_keywords:
- IDebugActivateDocumentEvent2 interface
ms.assetid: 6f37edd7-a48c-4b41-b160-dff9be63a284
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ce8307776a3dda9f086cdb77d2880228f14a62b2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugactivatedocumentevent2"></a>IDebugActivateDocumentEvent2
Il motore di debug (DE) usa questa interfaccia per richiedere un documento da caricare.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugActivateDocumentEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Quando è necessario aprire un file di origine, la Germania implementa questa interfaccia. Questa interfaccia è implementata solo dai motori di debug che utilizzano o fanno parte di interpreti di script. Il [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaccia deve essere implementata sullo stesso oggetto di questa interfaccia (utilizza il SDM [QueryInterface](/cpp/atl/queryinterface) per l'accesso di `IDebugEvent2` interfaccia).  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 La Germania crea e invia l'oggetto evento quando è necessario aprire un file di origine. L'evento viene inviato tramite il [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) funzione di callback fornita dal suo SDM quando è collegato al programma sottoposto a debug.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugActivateDocumentEvent2`.  
  
|Metodi|Descrizione|  
|-------------|-----------------|  
|[GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)|Ottiene il documento da attivare.|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)|Ottiene il contesto del documento che descrive la posizione all'interno del documento.|  
  
## <a name="remarks"></a>Note  
 Uno scenario tipico in cui viene utilizzata questa interfaccia è che se si verifica un errore di analisi nel codice di script in una pagina HTML, lo script DE invia questa interfaccia per il SDM in modo che sia possibile visualizzare il documento con l'errore di analisi.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)