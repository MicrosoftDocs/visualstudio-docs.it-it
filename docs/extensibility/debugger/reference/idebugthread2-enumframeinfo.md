---
description: Recupera un elenco degli stack frame per il thread.
title: 'IDebugThread2:: EnumFrameInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::EnumFrameInfo
helpviewer_keywords:
- IDebugThread2::EnumFrameInfo
ms.assetid: 17914a71-10ea-4b6f-8982-e364f87dca53
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7a47371bf9af89ef3f185698ca25a9df99cad4c6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053074"
---
# <a name="idebugthread2enumframeinfo"></a>IDebugThread2::EnumFrameInfo
Recupera un elenco degli stack frame per il thread.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT EnumFrameInfo ( 
   FRAMEINFO_FLAGS        dwFieldSpec,
   UINT                   nRadix,
   IEnumDebugFrameInfo2** ppEnum
);
```

```csharp
int EnumFrameInfo ( 
   enum_FRAMEINFO_FLAGS     dwFieldSpec,
   uint                     nRadix,
   out IEnumDebugFrameInfo2 ppEnum
);
```

## <a name="parameters"></a>Parametri
`dwFieldSpec`\
in Combinazione di flag dell'enumerazione [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) che specifica i campi delle strutture [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) da compilare. Specificare il `FIF_FUNCNAME_FORMAT` flag per formattare il nome della funzione in una singola stringa.

`nRadix`\
in Radice utilizzata per la formattazione di informazioni numeriche nell'enumeratore.

`ppEnum`\
out Restituisce un oggetto [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) che contiene un elenco di strutture [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) che descrivono la stack frame.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 I frame del thread vengono enumerati in ordine, con il frame corrente enumerato per primo e il frame meno recente enumerato per ultimo.

## <a name="see-also"></a>Vedi anche
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)
- [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
