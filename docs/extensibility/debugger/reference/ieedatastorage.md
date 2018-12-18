---
title: IEEDataStorage | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEEDataStorage
helpviewer_keywords:
- IEEDataStorage interface
ms.assetid: 704e932d-2325-410e-89c4-ce88c6ec19da
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: aeb98c4c4d3b544616412b3cf5cf8a162fddbd6b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="ieedatastorage"></a>IEEDataStorage
Questa interfaccia rappresenta una matrice di byte.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IEEDataStorage : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 L'analizzatore di espressioni (Java EE) implementa questa interfaccia per rappresentare una matrice di byte (utilizzato per i visualizzatori di tipo per recuperare e modificare dati tramite il [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) interface). In genere, l'analizzatore di Espressioni implementa questa interfaccia per supportare i visualizzatori di tipo esterno.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 I metodi di `IPropertyProxyEESide` interfaccia tutte restituito questa interfaccia. Chiamare [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) per ottenere il [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) interfaccia. Chiamare [QueryInterface](/cpp/atl/queryinterface) su un [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interfaccia per ottenere il [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) interfaccia.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Il `IEEDataStorage` interfaccia implementa i metodi seguenti:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)|Recupera il numero specificato di byte di dati da un buffer specificato.|  
|[GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)|Recupera il numero di byte di dati disponibili.|  
  
## <a name="remarks"></a>Note  
 Questa interfaccia viene utilizzata da un visualizzatore di tipo per accedere a dati mantenuti da un oggetto specifico. I dati viene considerati come una matrice di byte, consentendo al Visualizzatore di tipo per modificarlo nel modo necessario presentare all'utente.  
  
 Un visualizzatore personalizzato inoltre possibile utilizzare questa interfaccia, se si desidera, sebbene in genere, un visualizzatore personalizzato utilizzerà un'interfaccia personalizzata, [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) o [GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md) (per orientato alla stringa di dati).  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [Visualizzatore di tipi e visualizzatore personalizzato](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)