---
title: IEEVisualizerDataProvider | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEEVisualizerDataProvider
helpviewer_keywords: IEEVisualizerDataProvider interface
ms.assetid: 5fdfe6e3-b94e-4edb-acc5-41d8773d8ca5
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: edf2cfe689caa58e1c0402a91fa31237cb2c7215
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ieevisualizerdataprovider"></a>IEEVisualizerDataProvider
> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione analizzatori di espressioni CLR, vedere [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestiti esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Questa interfaccia fornisce la possibilità di modificare il valore di un oggetto tramite un visualizzatore di tipo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IEEVisualizerDataProvider : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 L'analizzatore di espressioni implementa questa interfaccia per supportare la modifica dei dati in un oggetto di proprietà tramite un visualizzatore di tipo.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Questa interfaccia viene utilizzata per creare il [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) oggetto tramite una chiamata a [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). Vedere [Visualizing e visualizzazione dei dati](../../../extensibility/debugger/visualizing-and-viewing-data.md) per altri dettagli.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[CanSetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-cansetobjectforvisualizer.md)|Determina se è possibile aggiornare l'oggetto (e, successivamente, il relativo valore) che è che rappresenta questo visualizzatore.|  
|[GetNewObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)|Forza una nuova valutazione dell'oggetto per il visualizzatore.|  
|[GetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getobjectforvisualizer.md)|Ottiene un oggetto esistente per questo visualizzatore (nessuna valutazione viene eseguita).|  
|[SetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-setobjectforvisualizer.md)|Aggiorna l'oggetto per il visualizzatore, cambiando il valore che viene presentato il visualizzatore.|  
  
## <a name="remarks"></a>Note  
 Il servizio Visualizzatore (rappresentati dal [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) l'interfaccia e restituito da [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)) mantiene un riferimento all'oggetto che implementa il `IEEVisualizerDataProvider` interfaccia . Di conseguenza, il `IEEVisualizerDataProvider` interfaccia non vanno implementata nello stesso oggetto che implementa il [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) se tale oggetto mantiene un riferimento di `IEEVisualizerService` oggetto: risultati un riferimento circolare e un deadlock si verifica quando gli oggetti vengono eliminati definitivamente. L'approccio consigliato consiste nell'implementare `IEEVisualizerDataProvider` su un oggetto separato a cui il `IDebugProperty2` delegati senza chiamare il metodo dell'oggetto `IUnknown::AddRef` su di esso.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di valutazione di espressioni](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [Visualizzazione di tipi e dati](../../../extensibility/debugger/visualizing-and-viewing-data.md)