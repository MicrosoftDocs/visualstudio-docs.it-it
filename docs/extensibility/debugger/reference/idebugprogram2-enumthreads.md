---
title: IDebugProgram2::EnumThreads | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::EnumThreads
helpviewer_keywords:
- IDebugProgram2::EnumThreads
ms.assetid: 0f2a8c51-1315-4c96-8aa1-6a937dc2a769
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9b261ca6973d938f8530ea75788d6ba6779ea9f0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62870489"
---
# <a name="idebugprogram2enumthreads"></a>IDebugProgram2::EnumThreads
Recupera un elenco dei thread in esecuzione del programma.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT EnumThreads( 
   IEnumDebugThreads2** ppEnum
);
```

```csharp
int EnumThreads( 
   out IEnumDebugThreads2 ppEnum
);
```

#### <a name="parameters"></a>Parametri
 `ppEnum`

 [out] Restituisce un [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md) oggetto che contiene un elenco dei thread.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)