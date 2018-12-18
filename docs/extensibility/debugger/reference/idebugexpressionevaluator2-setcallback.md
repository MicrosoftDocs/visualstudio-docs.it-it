---
title: IDebugExpressionEvaluator2::SetCallback | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugExpressionEvaluator2::SetCallback
- SetCallback
ms.assetid: 31e3a99e-e784-44a3-8b19-cc5ef31ed546
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f4b7c0333ff5328f4bdfd2411356074dc39d567c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugexpressionevaluator2setcallback"></a>IDebugExpressionEvaluator2::SetCallback
Consente l'analizzatore di espressioni (Java EE) specificare l'interfaccia di callback che verrà utilizzato il motore del debugger (DE) per leggere le impostazioni di metrica.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT SetCallback (  
   IDebugSettingsCallback2* pCallback  
);  
```  
  
```csharp  
int SetCallback (  
   IDebugSettingsCallback2 pCallback  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pCallback`  
 [in] Interfaccia da utilizzare per il callback di impostazioni.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo fornisce un'interfaccia al gestore di sessione di debug che un analizzatore di espressioni è possibile utilizzare per leggere le impostazioni di metrica. È utile nel debug remoto per continuare a leggere le metriche di [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] computer.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come implementare questo metodo per un **CEE** oggetto che espone il [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md) interfaccia.  
  
```cpp  
HRESULT CEE::SetCallback(IDebugSettingsCallback2* in_pCallback)  
{  
    // precondition  
    INVARIANT( this );  
  
    // function body  
    if (NULL != this->m_LanguageSpecificUseCases.pfSetCallback)  
    {  
        EEDomain::fSetCallback DomainVal =  
        {  
            in_pCallback  
        };  
  
        BOOL bSuccess = (*this->m_LanguageSpecificUseCases.pfSetCallback)(DomainVal);  
        ENSURE( bSuccess );  
    }  
  
    // postcondition  
    INVARIANT( this );  
  
    return S_OK;  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)