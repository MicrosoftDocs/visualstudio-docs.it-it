---
title: IEEVisualizerServiceProvider | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEEVisualizerServiceProvider
helpviewer_keywords:
- IEEVisualizerServiceProvider interface
ms.assetid: 859d1a51-1c65-4c8b-ae74-3b74b181ebcd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 564251aa26bf21157e4f3792095190ede23703c8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="ieevisualizerserviceprovider"></a>IEEVisualizerServiceProvider
> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione analizzatori di espressioni CLR, vedere [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestiti esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Questa interfaccia consente di accedere a un metodo che è possibile creare un servizio del visualizzatore, che viene utilizzato per gestire le attività del Visualizzatore di tipo per l'ambiente IDE.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IEEVisualizerServiceProvider : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Visual Studio implementa questa interfaccia per creare un oggetto servizio del visualizzatore, che a sua volta è utilizzato per fornire l'ID di classe (`CLSID`s) di visualizzatori di tipo all'IDE di Visual Studio.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 L'analizzatore di espressioni (Java EE) chiama [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md) per ottenere questa interfaccia.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)|Crea il servizio del Visualizzatore|  
  
## <a name="remarks"></a>Note  
 Il `IEEVisualizerServiceProvider` ottenuta durante l'implementazione dell'interfaccia [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). Il servizio del visualizzatore che consente di creare questa interfaccia viene utilizzato per fornire funzionalità a un [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interfaccia, l'analizzatore di Espressioni è responsabile dell'implementazione. L'analizzatore di Espressioni è inoltre responsabile per l'implementazione di un [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) interfaccia che consente i visualizzatori di tipo visualizzare e modificare un valore della proprietà.  
  
 Vedere [Visualizing e visualizzazione dei dati](../../../extensibility/debugger/visualizing-and-viewing-data.md) per informazioni dettagliate sulle modalità di interazione di queste interfacce.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di valutazione di espressioni](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [Visualizzazione di tipi e dati](../../../extensibility/debugger/visualizing-and-viewing-data.md)