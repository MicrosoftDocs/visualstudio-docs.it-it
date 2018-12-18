---
title: IPropertyProxyProvider | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IPropertyProxyProvider
helpviewer_keywords:
- IPropertyProxyProvider interface
ms.assetid: 52e9f7fc-6fe0-4d23-890b-5673dca8c3cb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d6d983027a88fd0e116abc7e284eb890eb33261a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="ipropertyproxyprovider"></a>IPropertyProxyProvider
Questa interfaccia fornisce un'interfaccia proxy per visualizzare e modificare i dati di un oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IPropertyProxyProvider : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 L'analizzatore di espressioni (Java EE) implementa questa interfaccia sullo stesso oggetto che implementa il [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interfaccia come parte del supporto del motore di esecuzione di visualizzatori di tipo.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Chiamare [QueryInterface](/cpp/atl/queryinterface) su un `IDebugProperty3` interfaccia per ottenere questa interfaccia.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Il `IPropertyProxyProvider` interfaccia implementa il metodo seguente:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)|Recupera un'interfaccia proxy di proprietà per visualizzare i dati su un oggetto.|  
  
## <a name="remarks"></a>Note  
 Sebbene l'analizzatore di Espressioni implementa questa interfaccia, l'implementazione di [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) viene generalmente gestita dagli [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md). Vedere [Visualizing e visualizzazione dei dati](../../../extensibility/debugger/visualizing-and-viewing-data.md) per informazioni dettagliate su come ottenere l'interfaccia IEEVisualizerService.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)   
 [Visualizzatore di tipo e il visualizzatore personalizzato](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)   
 [Visualizzazione di tipi e dati](../../../extensibility/debugger/visualizing-and-viewing-data.md)