---
title: IDebugProperty3::SetValueAsStringWithError | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProperty3::SetValueAsStringWithError
helpviewer_keywords: IDebugProperty3::SetValueAsStringWithError
ms.assetid: b378368f-4a45-4b2f-8e3d-3bff7a18ab17
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a86b6827e38885fd6940d382b351a8aa0941e0bc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugproperty3setvalueasstringwitherror"></a>IDebugProperty3::SetValueAsStringWithError
Imposta il valore di questa proprietà e restituisce un messaggio di errore, se necessario.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT SetValueAsStringWithError(  
   LPCOLESTR pszValue,  
   DWORD     dwRadix,  
   DWORD     dwTimeout,  
   BSTR*     errorString  
);  
```  
  
```csharp  
int SetValueAsStringWithError(  
   string     pszValue,  
   uint       dwRadix,  
   uint       dwTimeout,  
   out string errorString  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pszValue`  
 [in] Valore da impostare.  
  
 `dwRadix`  
 [in] La radice del valore da impostare.  
  
 `dwTimeout`  
 [in] Il periodo di tempo di attesa per il valore da impostare (`INFINITE` l'attesa è illimitata).  
  
 `errorString`  
 [out] Se si è verificato un errore di impostazione del valore, questo contiene il motivo dell'errore.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Il valore in ingresso può essere un'espressione da valutare.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come implementare questo metodo per un **CProperty** oggetto che espone il [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interfaccia.  
  
```cpp  
HRESULT CProperty::SetValueAsStringWithError(   
    LPCOLESTR in_szValue,  
    DWORD in_RADIX,  
    DWORD in_TIMEOUT,   
    BSTR * out_ERRORTEXT  
)  
{  
    // precondition  
    REQUIRE( NULL != in_szValue );  
  
    if (NULL == in_szValue)  
        return E_INVALIDARG;  
  
    INVARIANT( this );  
    if (!this->ClassInvariant())  
        return E_UNEXPECTED;  
  
    if (NULL == m_pPropertyContext->m_pCEE->m_LanguageSpecificUseCases.pfSetValue)  
        return S_OK;  
  
    // function body  
    DEBUG_PROPERTY_INFO dpInfo,dpInfo2;  
    HRESULT HR = this->GetPropertyInfo(DEBUGPROP_INFO_FULLNAME | DEBUGPROP_INFO_ATTRIB | DEBUGPROP_INFO_TYPE | DEBUGPROP_INFO_VALUE_AUTOEXPAND,  
                                       in_RADIX,  
                                       in_TIMEOUT,  
                                       NULL,  
                                       0,  
                                       &dpInfo);  
  
    if (ENSURE( S_OK == HR ))  
    {  
        REQUIRE( NULL != dpInfo.bstrFullName );  
        REQUIRE( NULL != dpInfo.bstrType );  
  
        REQUIRE( NULL == dpInfo.bstrName );  
        REQUIRE( NULL == dpInfo.bstrValue );  
        REQUIRE( NULL == dpInfo.pProperty );  
  
        BSTR bstrError = NULL;  
  
        UINT ichError = 0;  
        IDebugProperty2* pProperty = NULL;  
        IDebugParsedExpression* pParsedExpression = NULL;  
  
        CComBSTR bstrValue = dpInfo.bstrFullName;  
        bstrValue += L" = ";  
        bstrValue += in_szValue;  
        HR = this->m_pPropertyContext->m_pCEE->  
                Parse(bstrValue, 0, in_RADIX, &bstrError, &ichError, &pParsedExpression);  
        if (S_OK == HR)  
        {  
            REQUIRE( NULL == bstrError );  
            HR = pParsedExpression->EvaluateSync(EVAL_NOEVENTS | EVAL_RETURNVALUE,  
                                                 in_TIMEOUT,  
                                                 m_pPropertyContext->m_pSymbolProvider,  
                                                 m_pPropertyContext->m_pAddress,  
                                                 m_pPropertyContext->m_pBinder,  
                                                 NULL,  
                                                 &pProperty);  
  
            dpInfo2.dwAttrib = DBG_ATTRIB_VALUE_ERROR;  
            if (pProperty)  
            {  
                pProperty->GetPropertyInfo(DEBUGPROP_INFO_ATTRIB | DEBUGPROP_INFO_VALUE,10,in_TIMEOUT,NULL,0,&dpInfo2);  
            }  
            if (DBG_ATTRIB_VALUE_ERROR & dpInfo2.dwAttrib)  
            {  
                HR = E_FAIL;  
                bstrError = dpInfo2.bstrValue;  
            }  
            else  
            {  
                ::SysFreeString(dpInfo.bstrValue);  
            }  
            EXTERNAL_RELEASE(pProperty);  
            EXTERNAL_RELEASE(pParsedExpression);          
        }  
  
        if (bstrError)  
        {  
            if(out_ERRORTEXT)  
            {  
                *out_ERRORTEXT = bstrError;  
                bstrError = NULL;  
            }  
            else  
            {  
                ::SysFreeString(bstrError);  
            }  
        }  
        ::SysFreeString(dpInfo.bstrFullName);  
        ::SysFreeString(dpInfo.bstrType);  
    }  
  
    // postcondition  
    INVARIANT( this );  
  
    return HR;  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)