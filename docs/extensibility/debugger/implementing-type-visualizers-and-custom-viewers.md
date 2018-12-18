---
title: Implementazione di tipo visualizzatori e visualizzatori personalizzati | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: abef18c0-8272-4451-b82a-b4624edaba7d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c56d093c2e6380b29c8c9a788ea34d148fbe64b4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="implementing-type-visualizers-and-custom-viewers"></a>Implementazione di tipo visualizzatori e visualizzatori personalizzati
> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione analizzatori di espressioni CLR, vedere [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestiti esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 I visualizzatori di tipo e i visualizzatori personalizzati consentono all'utente visualizzare i dati di un determinato tipo in modo da renderlo più descrittivo rispetto a un semplice dump esadecimale dei numeri. Un analizzatore di espressioni (Java EE) è possibile associare visualizzatori personalizzati a specifici tipi di dati o variabili. Questi visualizzatori personalizzati vengono implementati mediante l'analizzatore di Espressioni. L'analizzatore di Espressioni supporta anche i visualizzatori di tipo esterno, che potrebbero derivare da un altro fornitore di terze parti o anche l'utente finale.  
  
## <a name="discussion"></a>Discussione  
  
### <a name="type-visualizers"></a>Visualizzatori di tipo  
 Visual Studio richiede un elenco di visualizzatori di tipo e i visualizzatori personalizzati per ogni oggetto da visualizzare in una finestra Espressioni di controllo. Un analizzatore di espressioni (Java EE) fornisce tale elenco per ogni tipo per cui vuole supportare i visualizzatori di tipo e i visualizzatori personalizzati. Le chiamate a [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) e [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) avviare l'intero processo di accesso ai visualizzatori di tipo e i visualizzatori personalizzati (vedere [Visualizing e visualizzazione dei dati](../../extensibility/debugger/visualizing-and-viewing-data.md)per informazioni dettagliate sulla sequenza di chiamata).  
  
### <a name="custom-viewers"></a>Visualizzatori personalizzati  
 Visualizzatori personalizzati vengono implementati nel motore di esecuzione per un tipo di dati specifico e sono rappresentati di [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) interfaccia. Un visualizzatore personalizzato non è altrettanto flessibile come un visualizzatore di tipo, poiché è disponibile solo quando l'analizzatore di Espressioni che implementa tale particolare visualizzatore personalizzato è in esecuzione. Implementazione di un visualizzatore personalizzato è più semplice rispetto all'implementazione di supporto per i visualizzatori di tipo. Tuttavia, i visualizzatori di tipo di supporto offre la massima flessibilità per l'utente finale per la visualizzazione dati il propria. Il resto di questo argomento riguarda solo i visualizzatori di tipo.  
  
## <a name="interfaces"></a>Interfacce  
 L'analizzatore di Espressioni implementa le interfacce seguenti per supportare i visualizzatori di tipo, verrà utilizzato da Visual Studio:  
  
-   [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)  
  
-   [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md)  
  
-   [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md)  
  
-   [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md)  
  
-   [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)  
  
-   [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
 L'analizzatore di Espressioni utilizza le interfacce seguenti per supportare i visualizzatori di tipo:  
  
-   [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)  
  
-   [IEEVisualizerServiceProvider](../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)  
  
-   [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Scrittura di un analizzatore di espressioni CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Visualizzazione e la visualizzazione dei dati](../../extensibility/debugger/visualizing-and-viewing-data.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)