---
title: IDebugDefaultPort2 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDefaultPort2
helpviewer_keywords:
- IDebugDefaultPort2 interface
ms.assetid: 7b3452af-9a96-4c4c-9946-4339b72d3d7b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c6d131ab24cc57af1846f89b61afa2d89ae2cacb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugdefaultport2"></a>IDebugDefaultPort2
Questa interfaccia fornisce diversi metodi per l'accesso ai server di una porta e le funzionalità di notifica.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugDefaultPort2 : IDebugPort2  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Visual Studio implementa questa interfaccia per rappresentare la porta di debug per l'accesso ai programmi. Un fornitore di porta personalizzato può anche implementare questa interfaccia se gestisce il debug remoto.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Un argomento a metodi di [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) interfaccia fornisce questa interfaccia. La chiamata [QueryInterface](/cpp/atl/queryinterface) su un [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interfaccia anche possibile ottenere questa interfaccia.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Oltre ai metodi definiti in [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md), questa interfaccia implementa i metodi seguenti:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md)|Ottiene l'interfaccia di notifica di porta da questa porta.|  
|[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)|Ottiene l'interfaccia per il server che ospita questa porta.|  
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugdefaultport2-queryislocal.md)|Determina se questa porta è in esecuzione nel computer locale.|  
  
## <a name="remarks"></a>Note  
 Il nome "`IDebugDefaultPort2`" è un po' di impropria poiché non rappresenta una porta predefinita. Impossibile chiamare "IDebugPort3".  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)