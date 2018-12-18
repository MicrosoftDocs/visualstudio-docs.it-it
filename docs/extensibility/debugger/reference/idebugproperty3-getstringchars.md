---
title: IDebugProperty3::GetStringChars | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProperty3::GetStringChars
helpviewer_keywords:
- IDebugProperty3::GetStringChars
ms.assetid: 832c37f3-85cb-4227-8ab2-f27a80eafe90
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d2f7d5430326f57acf686b90f911445cc36dbf02
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugproperty3getstringchars"></a>IDebugProperty3::GetStringChars
Recupera la stringa associata a questa proprietà e lo archivia in un buffer fornito dall'utente.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetStringChars(  
   ULONG  buflen,  
   WCHAR* rgString,  
   ULONG* pceltFetched  
);  
```  
  
```csharp  
int GetStringChars(  
   uint       buflen,   
   out string rgString,   
   out uint   pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `buflen`  
 [in] Numero massimo di caratteri che può contenere il buffer fornito dall'utente.  
  
 `rgString`  
 [out] Restituisce la stringa.  
  
 [Solo C++], `rgString` è un puntatore a un buffer che riceve i caratteri Unicode della stringa. Questo buffer deve essere almeno `buflen` caratteri (non byte) nella dimensione.  
  
 `pceltFetched`  
 [out] In cui viene restituito il numero di caratteri effettivamente memorizzati nel buffer. (Può essere `NULL` in C++.)  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 In C++, è necessario prestare attenzione per assicurarsi che il buffer sia almeno `buflen` caratteri Unicode. Si noti che un carattere Unicode è 2 byte.  
  
> [!NOTE]
>  In C++, la stringa restituita non include un carattere di terminazione null. Se specificato, `pceltFetched` specifica il numero di caratteri nella stringa.  
  
## <a name="example"></a>Esempio  
 
```cpp  
CStringW RetrievePropertyString(IDebugProperty2 *pPropInfo)  
{  
    CStringW returnString = L"";  
    CComQIPtr<IDebugProperty3> pProp3 = pPropInfo->pProperty;  
    If (pProp3 != NULL) {  
        ULONG dwStrLen = 0;  
        HRESULT hr;  
        hr = pProp3->GetStringCharLength(&dwStrLen);  
        if (SUCCEEDED(hr) && dwStrLen > 0) {  
            ULONG dwRead;  
            CStrBufW buf(returnString,dwStrLen,CStrBuf::SET_LENGTH);  
            hr = pProp3->GetStringChars(dwStrLen,  
                                        reinterpret_cast<WCHAR*>(static_cast<CStringW::PXSTR>(buf)),  
                                        &dwRead);  
        }  
    }  
    return(returnString);
}
```    
  
## <a name="see-also"></a>Vedere anche  
 [GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)