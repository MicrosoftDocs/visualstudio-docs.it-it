---
title: IPropertyProxyEESide | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IPropertyProxyEESide
helpviewer_keywords:
- IPropertyProxyEESide interface
ms.assetid: cf227cf8-39d9-4758-8f7e-a697aebb1926
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0f1dea4c3124cd532177618d84e2302a32e8bc4a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="ipropertyproxyeeside"></a>IPropertyProxyEESide
Questa interfaccia fornisce metodi per visualizzare i dati sull'oggetto associato. Questa interfaccia è parte del supporto per i visualizzatori di tipo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IPropertyProxyEESide : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Un analizzatore di espressioni implementa questa interfaccia per supportare i visualizzatori di tipo.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Chiamare [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) per ottenere questa interfaccia. Chiamare [QueryInterface](/cpp/atl/queryinterface) su un [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interfaccia per ottenere il [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) interfaccia.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Da questa interfaccia vengono implementati i metodi seguenti:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[InitSourceDataProvider](../../../extensibility/debugger/reference/ipropertyproxyeeside-initsourcedataprovider.md)|Inizializza un provider dell'origine dati in modo che i dati dell'oggetto accessibile.|  
|[GetManagedViewerCreationData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md)|Recupera le informazioni sull'assembly dell'oggetto.|  
|[GetInitialData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getinitialdata.md)|Ottiene i dati iniziali per l'oggetto.|  
|[CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)|Crea una copia di un archivio dati esistente.|  
|[InPlaceUpdateObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md)|Crea un riferimento a un archivio dati esistente.|  
|[ResolveAssemblyRef](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md)|Recupera informazioni su un assembly specifico nel contesto dell'assembly contenente l'oggetto.|  
  
## <a name="remarks"></a>Note  
 Un visualizzatore di tipo Usa questa interfaccia per accedere ai valori associati all'oggetto che fa parte di questa interfaccia. Si accede ai dati tramite il [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) interfaccia, che fornisce una visualizzazione di sola lettura dei dati.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Visualizzatore di tipo e il visualizzatore personalizzato](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)