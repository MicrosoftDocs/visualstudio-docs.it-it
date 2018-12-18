---
title: IDebugGenericParamField::GetIndex | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugGenericParamField::GetIndex
ms.assetid: 8e0bdb26-1247-44d9-8d80-ec6e35187fb4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7dc623eca2221c0ca9c073e830683739d048f84b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebuggenericparamfieldgetindex"></a>IDebugGenericParamField::GetIndex
Recupera l'indice del parametro generico.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetIndex(  
   DWORD* pIndex  
);  
```  
  
```csharp  
int GetIndex(  
   out uint pIndex  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pIndex`  
 [out] Valore di indice del parametro generico.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Ad esempio, per Dictionary(K,V), è l'indice 0 K, V indice 1.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come implementare questo metodo per un **CDebugGenericParamFieldType** oggetto che espone il [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md) interfaccia.  
  
```cpp  
HRESULT CDebugGenericParamFieldType::GetIndex(DWORD* pIndex)  
{  
    HRESULT hr = S_OK;  
  
    METHOD_ENTRY( CDebugGenericParamFieldType::GetIndex );  
  
    IfFalseGo(pIndex, E_INVALIDARG );  
    IfFailGo( this->LoadProps() );  
    *pIndex = m_index;  
  
Error:  
  
    METHOD_EXIT( CDebugGenericParamFieldType::GetIndex, hr );  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)