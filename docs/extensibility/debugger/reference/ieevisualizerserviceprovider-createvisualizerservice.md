---
title: IEEVisualizerServiceProvider::CreateVisualizerService | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService
helpviewer_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService method
ms.assetid: f366f7c9-358d-46c8-993f-32ff86539833
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f59d86e94be5c0295786b747f6b57753aa087b07
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="ieevisualizerserviceprovidercreatevisualizerservice"></a>IEEVisualizerServiceProvider::CreateVisualizerService
Questo metodo crea un servizio del visualizzatore.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT CreateVisualizerService(  
   IDebugBinder*              binder,  
   IDebugSymbolProvider*      pSymProv,  
   IDebugAddress*             pAddress,  
   IEEVisualizerDataProvider* dataProvider,  
   IEEVisualizerService**     ppService  
);  
```  
  
```csharp  
int CreateVisualizerService(  
   IDebugBinder binder,  
   IDebugSymbolProvider      pSymProv,  
   IDebugAddress             pAddress,  
   IEEVisualizerDataProvider dataProvider,  
   out IEEVisualizerService  ppService  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `binder`  
 [in] Il [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) oggetto passato a [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md).  
  
 `pSymProv`  
 [in] Il [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) oggetto passato a `IDebugParsedExpression::EvaluateSync`.  
  
 `pAddress`  
 [in] Il [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) oggetto passato a `IDebugParsedExression::EvaluateSync`.  
  
 `dataProvider`  
 [in] Oggetto che implementa il [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) interfaccia (fornito dall'analizzatore di espressioni).  
  
 `ppService`  
 [out] Il servizio creato.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Il `binder`, `pSymProv`, e `pAddress` i parametri sono stati passati al `IDebugParsedExpression::EvaluateSync` metodo. `CreateVisualizerService` deve essere chiamata solo da `IDebugParsedExpression::EvaluateSync` come parte del supporto dell'analizzatore di espressioni per i visualizzatori di tipo.  
  
## <a name="see-also"></a>Vedere anche  
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)