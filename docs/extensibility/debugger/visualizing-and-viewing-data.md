---
title: Visualizzazione e la visualizzazione dei dati | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], viewing data
- debugging [Debugging SDK], visualizing data
ms.assetid: 699dd0f5-7569-40b3-ade6-d0fe53e832bc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ebaa07c8fe70e1842334b0bf7c28eb7491fd9c44
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="visualizing-and-viewing-data"></a>Visualizzazione e la visualizzazione dei dati
I visualizzatori di tipo e i visualizzatori personalizzati presentare i dati in modo significativo rapidamente a uno sviluppatore. L'analizzatore di espressioni (Java EE) può supportare i visualizzatori di tipo di terze parti, nonché fornire i proprio visualizzatori personalizzati.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Determina quante i visualizzatori di tipo visualizzatori personalizzati sono associati e il tipo dell'oggetto chiamando il [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) metodo. Se è presente il Visualizzatore di almeno un tipo o il visualizzatore personalizzato, Visual Studio chiama il [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) metodo per recuperare un elenco dei visualizzatori e visualizzatori (in realtà, un elenco di `CLSID`s che implementano il i visualizzatori e visualizzatori) e li presenta all'utente.  
  
## <a name="supporting-type-visualizers"></a>I visualizzatori di tipo di supporto  
 Esistono una serie di interfacce che l'analizzatore di Espressioni deve implementare per supportare i visualizzatori di tipo. Queste interfacce possono essere suddivisi in due ampie categorie: quelli che elenca i visualizzatori di tipo e quelli a cui accedono i dati della proprietà.  
  
### <a name="listing-type-visualizers"></a>Visualizzatori di tipo elenco  
 L'analizzatore di Espressioni supporta elencare i visualizzatori di tipo nella propria implementazione di `IDebugProperty3::GetCustomViewerCount` e `IDebugProperty3::GetCustomViewerList`. Questi metodi passano la chiamata ai metodi corrispondenti [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) e [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md).  
  
 Il [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) viene ottenuto chiamando [CreateVisualizerService](../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). Questo metodo richiede il [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md) interfaccia, viene ottenuto dal [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) interfaccia passata al [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). `IEEVisualizerServiceProvider::CreateVisualizerService` richiede anche il [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) e [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) le interfacce che sono state passate a `IDebugParsedExpression::EvaluateSync`. L'interfaccia finale necessario per creare il `IEEVisualizerService` interfaccia è il [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md) interfaccia, che implementa l'analizzatore di Espressioni. Questa interfaccia consente modifiche da apportare alla proprietà da visualizzare. Tutti i dati di proprietà è incapsulato in un [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) interfaccia, viene inoltre implementata dal motore di esecuzione.  
  
### <a name="accessing-property-data"></a>L'accesso ai dati di proprietà  
 L'accesso ai dati di proprietà viene eseguita tramite il [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md) interfaccia. Per ottenere questa interfaccia, Visual Studio chiama [QueryInterface](/cpp/atl/queryinterface) sull'oggetto di proprietà per ottenere il [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md) interfaccia (implementato nello stesso oggetto che implementa il [ IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) interface) e quindi chiama il [GetPropertyProxy](../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) per ottenere il `IPropertyProxyEESide` interfaccia.  
  
 Tutti i dati passati in e dal `IPropertyProxyEESide` interfaccia è incapsulata nel [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md) interfaccia. Questa interfaccia rappresenta una matrice di byte e viene implementata da Visual Studio e l'analizzatore di Espressioni. Quando sono necessario modificare i dati di una proprietà, Visual Studio crea un `IEEDataStorage` oggetto che contiene i nuovi dati e le chiamate [CreateReplacementObject](../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) con tale oggetto dati per ottenere un nuovo `IEEDataStorage` oggetto, a sua volta, passato a [InPlaceUpdateObject](../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md) per aggiornare i dati della proprietà. `IPropertyProxyEESide::CreateReplacementObject` Consente l'analizzatore di Espressioni creare un'istanza di classe che implementa il `IEEDataStorage` interfaccia.  
  
## <a name="supporting-custom-viewers"></a>Supporto visualizzatori personalizzati  
 Il flag `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` è impostato `dwAttrib` campo il [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) struttura (restituito da una chiamata a [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)) per indicare che l'oggetto dispone di un visualizzatore personalizzato associato con esso. Quando questo flag è impostato, Visual Studio Ottiene il [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) interfaccia dal [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfaccia utilizzando [QueryInterface](/cpp/atl/queryinterface).  
  
 Se l'utente seleziona un visualizzatore personalizzato, Visual Studio crea il visualizzatore personalizzato utilizzando il visualizzatore `CLSID` fornito dal `IDebugProperty3::GetCustomViewerList` metodo. Visual Studio chiama quindi [disponibili DisplayValue](../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) per mostrare il valore per l'utente.  
  
 In genere, `IDebugCustomViewer::DisplayValue` presenta una visualizzazione di sola lettura dei dati. Per consentire le modifiche ai dati, l'analizzatore di Espressioni deve implementare un'interfaccia personalizzata che supporta la modifica dei dati in un oggetto di proprietà. Il `IDebugCustomViewer::DisplayValue` metodo Usa l'interfaccia personalizzata per supportare la modifica dei dati. Il metodo esegue la ricerca per l'interfaccia personalizzata `IDebugProperty2` interfaccia passato come il `pDebugProperty` argomento.  
  
## <a name="supporting-both-type-visualizers-and-custom-viewers"></a>Supporto entrambi digitare visualizzatori e visualizzatori personalizzati  
 Può supportare un EE i visualizzatori di tipo sia visualizzatori personalizzati disponibili nel [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) e [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) metodi. In primo luogo, l'analizzatore di Espressioni aggiunge il numero di visualizzatori personalizzati che fornisca il valore restituito dal [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) metodo. In secondo luogo, l'analizzatore di Espressioni aggiunge il `CLSID`s del proprio visualizzatori personalizzati per l'elenco restituito dal [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [Attività di debug](../../extensibility/debugger/debugging-tasks.md)   
 [Visualizzatore di tipi e visualizzatore personalizzato](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)