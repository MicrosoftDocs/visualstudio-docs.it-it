---
title: IDebugPendingBreakpoint2::CanBind | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPendingBreakpoint2::CanBind
helpviewer_keywords:
- IDebugPendingBreakpoint2::CanBind method
- CanBind method
ms.assetid: 84a2b189-ccf1-467e-8fab-0c0da68f0b91
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e09bae8cfa6b4c2ba1b79ff74945e5256e23ed2c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
ms.locfileid: "31115723"
---
# <a name="idebugpendingbreakpoint2canbind"></a>IDebugPendingBreakpoint2::CanBind
Determina se è possibile associare il punto di interruzione in sospeso in un percorso di codice.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT CanBind (   
   IEnumDebugErrorBreakpoints2** ppErrorEnum  
);  
```  
  
```csharp  
int CanBind (   
   out IEnumDebugErrorBreakpoints2 ppErrorEnum  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppErrorEnum`  
 [out] Restituisce un [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md) oggetto che contiene un elenco di [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) oggetti potrebbe verificarsi errori.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK.` restituisce `S_FALSE` se non è possibile associare il punto di interruzione, nel qual caso vengono restituiti gli errori per il `ppErrorEnum` parametro. In caso contrario, verrà restituito un codice di errore. Restituisce `E_BP_DELETED` se il punto di interruzione è stato eliminato.  
  
## <a name="remarks"></a>Note  
 Questo metodo viene chiamato per determinare che cosa accadrebbe se è stato in sospeso punto di interruzione associato. Chiamare il [associare](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) metodo effettivamente associare il punto di interruzione in sospeso.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come implementare questo metodo per una semplice `CPendingBreakpoint` oggetto che espone il [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) interfaccia.  
  
```cpp  
HRESULT CPendingBreakpoint::CanBind(IEnumDebugErrorBreakpoints2** ppErrorEnum)    
{    
   HRESULT hr;    
   HRESULT hrT;    
  
   // Check for a valid pointer to an error breakpoint enumerator   
   // interface; otherwise, return hr = E_INVALIDARG.    
   if (ppErrorEnum)    
   {    
      // Verify that the pending breakpoint has not been deleted. If   
      // deleted, then return hr = E_BP_DELETED.    
      if (m_state.state != PBPS_DELETED)    
      {    
         // Verify that the breakpoint is a file/line breakpoint.    
         if (IsFlagSet(m_pBPRequest->m_bpRequestInfo.dwFields, BPREQI_BPLOCATION) &&  
             m_pBPRequest->m_bpRequestInfo.bpLocation.bpLocationType == BPLT_CODE_FILE_LINE)    
         {    
            hr = S_OK;    
         }    
         // If the breakpoint type is not a file/line breakpoint, then the   
         // result should be an error breakpoint.    
         else    
         {    
            // If the error breakpoint member variable does not have   
            // allocated memory.  
            if (!m_pErrorBP)    
            {    
               // Create, AddRef, and initialize a CErrorBreakpoint object.    
               if (CComObject<CErrorBreakpoint>::CreateInstance(&m_pErrorBP) == S_OK)    
               {    
                  m_pErrorBP->AddRef();    
                  m_pErrorBP->Initialize(this);    
               }    
            }    
  
            // Create a new enumerator of error breakpoints.    
             CComObject<CEnumDebugErrorBreakpoints>* pErrorEnum;    
            if (CComObject<CEnumDebugErrorBreakpoints>::CreateInstance(&pErrorEnum) == S_OK)    
            {    
               // Get the IDebugErrorBreakpoint2 information for the     
               // CErrorBreakpoint object.    
               CComPtr<IDebugErrorBreakpoint2> spErrorBP;    
               hrT = m_pErrorBP->QueryInterface(&spErrorBP);    
               assert(hrT == S_OK);    
               if (hrT == S_OK)    
               {    
                  // Initialize the new enumerator of error breakpoints   
                  // with the IDebugErrorBreakpoint2 information.      
                  IDebugErrorBreakpoint2* rgpErrorBP[] = { spErrorBP.p };    
                  hrT = pErrorEnum->Init(rgpErrorBP, &(rgpErrorBP[1]), NULL, AtlFlagCopy);    
                  if (hrT == S_OK)    
                  {    
                     // Verify that the passed IEnumDebugErrorBreakpoints2     
                     // interface can be successful queried by the  
                     // created CEnumDebugErrorBreakpoints object.    
                     hrT = pErrorEnum->QueryInterface(ppErrorEnum);    
                     assert(hrT == S_OK);    
                  }    
               }    
  
               // Otherwise, delete the CEnumDebugErrorBreakpoints object.    
               if (FAILED(hrT))    
               {    
                  delete pErrorEnum;    
               }    
            }    
  
            hr = S_FALSE;    
         }    
      }    
      else    
      {    
         hr = E_BP_DELETED;    
      }    
   }    
   else    
   {    
      hr = E_INVALIDARG;    
   }    
  
   return hr;    
}    
```  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)   
 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)   
 [Operazione di binding](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)