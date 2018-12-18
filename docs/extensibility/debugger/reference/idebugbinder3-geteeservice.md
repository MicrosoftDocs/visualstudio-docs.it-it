---
title: IDebugBinder3::GetEEService | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBinder3::GetEEService
helpviewer_keywords:
- IDebugBinder3::GetEEService method
ms.assetid: eb07aa40-8cd9-4a52-a4c7-4affd2307a01
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 56c97e9fc7e5505578533c9e7b958a73dc8d2380
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugbinder3geteeservice"></a>IDebugBinder3::GetEEService
Questo metodo restituisce un servizio richiesto.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetEEService(  
   [in] GUID        vendor,  
   [in] GUID        language,  
   [in] GUID        iid,  
   [out] IUnknown** ppService  
);  
```  
  
```csharp  
Int GetEEService(  
   Guid       vendor,  
   Guid       language,  
   Guid       iid,  
   out object ppService  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `vendor`  
 [in] `GUID` di un fornitore (un valore null è accettabile).  
  
 `language`  
 [in] `GUID` di una lingua (un valore null è accettabile).  
  
 `iid`  
 [in] `IID` del servizio da ottenere.  
  
 `ppService`  
 [out] Interfaccia per il servizio richiesto.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Passare il `IID` per il [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md) interfaccia (`IID_IEEVisualizerServiceProvider`) per verificare se il servizio del Visualizzatore di tipo è disponibile. Se in tal caso, è possibile ottenere l'analizzatore di espressioni di [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) interfaccia per supportare i visualizzatori di tipo. Vedere [Visualizing e visualizzazione dei dati](../../../extensibility/debugger/visualizing-and-viewing-data.md) per informazioni dettagliate.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [Visualizzazione di tipi e dati](../../../extensibility/debugger/visualizing-and-viewing-data.md)