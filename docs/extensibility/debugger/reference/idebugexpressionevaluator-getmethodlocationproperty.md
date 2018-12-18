---
title: IDebugExpressionEvaluator::GetMethodLocationProperty | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty method
ms.assetid: 52c42a2e-f144-476b-8bef-442464c8fe8e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f10a26eca06aed24d53b70cd406fe3f24e2fe898
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugexpressionevaluatorgetmethodlocationproperty"></a>IDebugExpressionEvaluator::GetMethodLocationProperty
Questo metodo converte un percorso di metodo e l'offset in un indirizzo di memoria.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetMethodLocationProperty(   
   LPCOLESTR             upstrFullyQualifiedMethodPlusOffset,  
   IDebugSymbolProvider* pSymbolProvider,  
   IDebugAddress*        pAddress,  
   IDebugBinder*         pBinder,  
   IDebugProperty2**     ppProperty  
);  
```  
  
```csharp  
int GetMethodLocationProperty(  
   string               upstrFullyQualifiedMethodPlusOffset,   
   IDebugSymbolProvider pSymbolProvider,   
   IDebugAddress        pAddress,   
   IDebugBinder         pBinder,   
   out IDebugProperty2  ppProperty  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `upstrFullyQualifiedMethodPlusOffset`  
 [in] Il percorso di metodo e l'offset, espresso come stringa.  
  
 `pSymbolProvider`  
 [in] Il provider di simboli espresso come un [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) oggetto.  
  
 `pAddress`  
 [in] Un indirizzo all'interno del metodo, espresso come un [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) oggetto.  
  
 `pBinder`  
 [in] Lo strumento di associazione espresso come un [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) oggetto.  
  
 `ppProperty`  
 [out] Restituisce un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) interfaccia che rappresenta l'indirizzo di memoria.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 L'indirizzo restituito può essere utilizzato per impostare un punto di interruzione, ad esempio.  
  
 Nonostante il nome `upstrFullyQualifiedMethodPlusOffset`, questo parametro può essere passato un nome di metodo parziali. In tal caso, il metodo selezionato è quello che racchiude `pAddress`. Modalità di interpretazione di questo parametro è l'implementazione dell'analizzatore di espressioni e la lingua che supporta.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)