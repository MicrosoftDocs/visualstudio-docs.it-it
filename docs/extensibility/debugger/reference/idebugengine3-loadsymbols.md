---
description: Carica (se necessario) i simboli per tutti i moduli di cui è in corso il debug da questo motore di debug.
title: 'IDebugEngine3:: LoadSymbols | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::LoadSymbols
helpviewer_keywords:
- IDebugEngine3::LoadSymbols
ms.assetid: c846a440-1d91-4d48-b8f1-82e902ae152b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 43651baac29b3904b9bc12d8d4b965ca1cd8e3ee
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066179"
---
# <a name="idebugengine3loadsymbols"></a>IDebugEngine3::LoadSymbols
Carica (se necessario) i simboli per tutti i moduli di cui è in corso il debug da questo motore di debug.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT LoadSymbols();
```

```csharp
int LoadSymbols();
```

## <a name="parameters"></a>Parametri
 No.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce il codice di errore.

## <a name="remarks"></a>Commenti
 Vengono caricati i simboli di debug per tutti i moduli a cui fa riferimento il motore di debug. I simboli vengono caricati solo se non sono già stati caricati. I simboli vengono cercati nei percorsi impostati da una chiamata a [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md).

## <a name="see-also"></a>Vedi anche
- [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
