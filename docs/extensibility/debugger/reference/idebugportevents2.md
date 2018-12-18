---
title: IDebugPortEvents2 | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPortEvents2
helpviewer_keywords: IDebugPortEvents2 interface
ms.assetid: 2c017094-3ba2-4067-83f9-147df1d96bce
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0a5782f0a50ac37b45c4b7e3402bcdded96b4683
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugportevents2"></a>IDebugPortEvents2
Questa interfaccia notifica a un listener (in genere debug Gestione sessione [SDM] o un motore di debug) del processo e il programma di creazione e l'eliminazione su una porta specifica. Queste informazioni possono essere utilizzate per presentare una visualizzazione in tempo reale dei processi e i programmi in esecuzione sulla porta.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugPortEvents2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Visual Studio è in genere implementa questa interfaccia per ricevere notifiche su programma creazione e distruzione. Un motore di debug è anche possibile implementare questa interfaccia per l'ascolto degli eventi di questo tipo porta.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Tutti [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interfacce è possibile eseguire query per un <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interfaccia. Il <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.FindConnectionPoint%2A> metodo per `IDebugPortEvents2` viene chiamato il <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interfaccia da ottenere un <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interfaccia. Infine, il <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> metodo il <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interfaccia viene chiamata per inviare gli eventi tramite il [evento](../../../extensibility/debugger/reference/idebugportevents2-event.md) (metodo).  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente mostra il metodo di `IDebugPortEvents2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)|Invia gli eventi che descrivono la creazione e l'eliminazione dei processi e dei programmi sulla porta.|  
  
## <a name="remarks"></a>Note  
 `IDebugPortEvents2`viene inoltre utilizzato dal suo SDM per eseguire il debug di programmi in esecuzione in un processo che è già in corso il debug.  
  
 Gli eventi porta vengono passati al SDM tramite questa interfaccia.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)