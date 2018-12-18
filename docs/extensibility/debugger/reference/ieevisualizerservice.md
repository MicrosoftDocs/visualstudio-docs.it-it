---
title: IEEVisualizerService | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEEVisualizerService
helpviewer_keywords: IEEVisualizerService interface
ms.assetid: 3bdb124b-c582-47ba-b465-13c6a1cdb702
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 97701dede6a3e6b17911f6ab3c5e37dfdd90cc58
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ieevisualizerservice"></a>IEEVisualizerService
> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione analizzatori di espressioni CLR, vedere [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestiti esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Questa interfaccia implementa i metodi principali che forniscono funzionalità per il [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) e [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) interfacce.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IEEVisualizerService : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Visual Studio implementa questa interfaccia per consentire un analizzatore di espressioni (Java EE) per supportare i visualizzatori di tipo.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Le chiamate EE [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md) per ottenere questa interfaccia come parte del supporto per i visualizzatori di tipo.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)|Recupera il numero di cui questo servizio è in grado di visualizzatori personalizzati.|  
|[GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)|Recupera l'elenco di visualizzatori personalizzati.|  
|[GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)|Restituisce un oggetto proxy per una proprietà.|  
|[GetValueDisplayStringCount](../../../extensibility/debugger/reference/ieevisualizerservice-getvaluedisplaystringcount.md)|Recupera il numero di stringhe di valori da visualizzare per la proprietà specificata o il campo.|  
  
## <a name="remarks"></a>Note  
 L'IDE Usa il [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interfaccia per determinare se sono presenti eventuali visualizzatori personalizzati o digitare i visualizzatori per la proprietà. Tramite la creazione di un servizio del visualizzatore (con [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)), l'analizzatore di Espressioni può fornire la funzionalità per il `IDebugProperty3` e [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) (che supporta la visualizzazione e modifica di un il valore della proprietà) di interfacce e in tal modo supportano i visualizzatori di tipo.  
  
 Se un EE visualizzatori personalizzati implementa che a sua volta, l'analizzatore di Espressioni è possibile aggiungere il `CLSID`s di tali visualizzatori personalizzati alla fine dell'elenco restituito da [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md). In questo modo un EE supportare i visualizzatori di tipo sia un proprio visualizzatori personalizzati. Solo assicurarsi che [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) riflette l'aggiunta di eventuali visualizzatori personalizzati.  
  
 Vedere [Visualizzatore di tipo e il visualizzatore personalizzato](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) per una descrizione della differenza tra i visualizzatori e visualizzatori.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di valutazione di espressioni](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)   
 [Visualizzatore di tipi e visualizzatore personalizzato](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)