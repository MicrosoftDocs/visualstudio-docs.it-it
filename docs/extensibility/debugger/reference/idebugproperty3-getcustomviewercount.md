---
title: IDebugProperty3::GetCustomViewerCount | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProperty3::GetCustomViewerCount
helpviewer_keywords:
- IDebugProperty3::GetCustomViewerCount
ms.assetid: dc5bb3e4-dc85-46e4-98fa-c6be8583b985
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cb04a772a9ca2a6bf63861c02e3c65870639da56
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugproperty3getcustomviewercount"></a>IDebugProperty3::GetCustomViewerCount
Ottiene il numero di visualizzatori personalizzati che potrebbero essere disponibili per questa proprietà.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetCustomViewerCount(  
   ULONG* pcelt  
);  
```  
  
```csharp  
int GetCustomViewerCount(  
   out uint pcelt  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pcelt`  
 [out] Il numero di visualizzatori personalizzati disponibili per questa proprietà.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Per supportare i visualizzatori di tipo, questo metodo inoltra la chiamata al [GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) metodo. Se l'analizzatore di espressioni supporta anche i visualizzatori personalizzati per questo tipo di proprietà, questo metodo aggiunge il numero di visualizzatori personalizzati per il valore restituito.  
  
 Per informazioni dettagliate sulle differenze tra i visualizzatori di tipo e i visualizzatori personalizzati, vedere [Visualizzatore di tipo e il visualizzatore personalizzato](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come implementare questo metodo per un **CProperty** oggetto che espone il [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interfaccia.  
  
```cpp  
STDMETHODIMP CProperty::GetCustomViewerCount(ULONG* pcelt)  
{  
    if (pcelt == NULL)  
    {  
        return E_POINTER;  
    }  
  
    if (GetVisualizerService())  
    {  
        return m_pIEEVisualizerService->GetCustomViewerCount(pcelt);  
    }  
    else  
    {  
        return E_NOTIMPL;  
    }  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)   
 [Visualizzatore di tipi e visualizzatore personalizzato](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)