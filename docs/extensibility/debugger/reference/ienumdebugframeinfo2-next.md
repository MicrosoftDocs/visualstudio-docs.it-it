---
title: IEnumDebugFrameInfo2::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFrameInfo2::Next
helpviewer_keywords:
- IEnumDebugFrameInfo2::Next
ms.assetid: 64a64eeb-5dea-4119-8a22-03771015d1e5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 361b936cf2072e2105edfb02f66f4e0524b2b98e
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56705138"
---
# <a name="ienumdebugframeinfo2next"></a>IEnumDebugFrameInfo2::Next
Restituisce il set successivo di elementi dall'enumerazione.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Next(
   ULONG       celt,
   FRAMEINFO** rgelt,
   ULONG*      pceltFetched
);
```

```csharp
int Next(
   uint        celt,
   FRAMEINFO[] rgelt,
   ref uint    pceltFetched
);
```

#### <a name="parameters"></a>Parametri
 `celt`

 [in] Il numero di elementi da recuperare. Specifica inoltre la dimensione massima del `rgelt` matrice.

 `rgelt`

 [in, out] Matrice di [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) elementi da compilare.

 `pceltFetched`

 [out] Restituisce il numero di elementi effettivamente restituiti nella `rgelt`.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se inferiore al numero richiesto di elementi potrebbe essere restituiti; in caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)