---
description: Questo metodo restituisce un elenco di visualizzatori di tipi di cui questo servizio è a conoscenza.
title: 'IEEVisualizerService:: GetCustomViewerList | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerService::GetCustomViewerList
helpviewer_keywords:
- IEEVisualizerService::GetCustomViewerList method
ms.assetid: 249d26ca-914f-43af-a400-8162477223f4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 99db28a8d0efef7ffec97ecab818f4ede6b153fe
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086885"
---
# <a name="ieevisualizerservicegetcustomviewerlist"></a>IEEVisualizerService::GetCustomViewerList
Questo metodo restituisce un elenco di visualizzatori di tipi di cui questo servizio è a conoscenza.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetCustomViewerList(
   ULONG                celtSkip,
   ULONG                celtRequested,
   DEBUG_CUSTOM_VIEWER* rgViewers,
   ULONG*               pceltFetched
);
```

```csharp
int GetCustomViewerList(
   uint                  celtSkip,
   uint                  celtRequested,
   DEBUG_CUSTOM_VIEWER[] rgViewers,
   out uint              pceltFetched
);
```

## <a name="parameters"></a>Parametri
`celtSkip`\
in Numero di visualizzatori da ignorare.

`celRequested`\
in Numero di visualizzatori da recuperare (specifica anche le dimensioni della `rgViewers` matrice).

`rgViewers`\
[in, out] Matrice di strutture di [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) da compilare.

`pceltFetched`\
out Numero di visualizzatori effettivamente recuperati.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) passa la richiesta a questo metodo come parte del supporto per i visualizzatori di tipi. Se l'analizzatore di espressioni fornisce anche visualizzatori personalizzati per lo stesso tipo, è possibile aggiungere in modo appropriato le strutture [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) per i visualizzatori personalizzati all'elenco. Assicurarsi che [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) rifletta i visualizzatori aggiuntivi.

 Per informazioni dettagliate sulle differenze tra visualizzatori e visualizzatori, vedere Visualizzatore di [tipi e visualizzatore personalizzato](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) .

## <a name="see-also"></a>Vedi anche
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)
- [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)
- [Visualizzatore di tipi e visualizzatore personalizzato](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
