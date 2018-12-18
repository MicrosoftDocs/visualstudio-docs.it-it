---
title: IDebugBreakpointErrorEvent2::GetErrorBreakpoint | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBreakpointErrorEvent2::GetErrorBreakpoint
helpviewer_keywords:
- IDebugBreakpointErrorEvent2::GetErrorBreakpoint
ms.assetid: e5acfd19-ac17-47f3-a31a-b2aa8baca36d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b25504e8f15ecdfc1d4b00e3d8bfdf9ecb502916
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugbreakpointerrorevent2geterrorbreakpoint"></a>IDebugBreakpointErrorEvent2::GetErrorBreakpoint
Ottiene un [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) oggetto che descrive il motivo per cui non è stato associato un punto di interruzione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetErrorBreakpoint(   
   IDebugErrorBreakpoint2** ppErrorBP  
);  
```  
  
```csharp  
int GetErrorBreakpoint(   
   out IDebugErrorBreakpoint2 ppErrorBP  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppErrorBP`  
 [out] Restituisce un [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) oggetto che descrive l'avviso o errore.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Dopo il `IDebugErrorBreakpoint2` ottenere l'interfaccia, chiamare il [GetBreakpointResolution](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) metodo per ottenere un [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md) oggetto. Il [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) metodo può essere utilizzato per determinare una posizione non valida, un'espressione non valida o motivi per cui il punto di interruzione in sospeso non è stato associato, ad esempio di codice non ancora caricato e così via.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come implementare questo metodo per un **CBreakpointSetDebugEventBase** oggetto che espone il [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) interfaccia.  
  
```cpp  
STDMETHODIMP CBreakpointErrorDebugEventBase::GetErrorBreakpoint(  
    IDebugErrorBreakpoint2 **ppbp)  
{  
    HRESULT hRes = E_FAIL;  
  
    if ( ppbp )  
    {  
        if ( m_pError )  
        {  
            *ppbp = m_pError;  
  
            m_pError->AddRef();  
  
            hRes = S_OK;  
        }  
        else  
            hRes = E_FAIL;  
    }  
    else  
        hRes = E_INVALIDARG;  
  
    return ( hRes );  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)   
 [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)   
 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)