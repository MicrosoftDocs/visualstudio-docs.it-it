---
description: Indica al programma o al nodo del programma quale motore di debug (DE) utilizzare per eseguire il debug del programma.
title: 'IDebugProgramEngines2:: semotore | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2::SetEngine
helpviewer_keywords:
- IDebugProgramEngines2::SetEngine
ms.assetid: c05857ee-89cf-455e-8f1e-300cce4a2eab
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e938cd63c88d0d58866b36528a1342983dc457f1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084181"
---
# <a name="idebugprogramengines2setengine"></a>IDebugProgramEngines2::SetEngine
Indica al programma o al nodo del programma quale motore di debug (DE) utilizzare per eseguire il debug del programma.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT SetEngine( 
   REFGUID guidEngine
);
```

```csharp
int SetEngine( 
   ref Guid guidEngine
);
```

## <a name="parameters"></a>Parametri
`guidEngine`\
in GUID dell'oggetto DE.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)
