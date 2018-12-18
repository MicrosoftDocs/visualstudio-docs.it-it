---
title: IDebugProgramNode2::DetachDebugger_V7 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramNode2::DetachDebugger
helpviewer_keywords:
- IDebugProgramNode2::DetachDebugger
- IDebugProgramNode2::DetachDebugger_V7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3a79c073048fe30a4abed069487ad09943253475
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogramnode2detachdebuggerv7"></a>IDebugProgramNode2::DetachDebugger_V7

> [!Note]
> DEPRECATO. NON USARE.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT DetachDebugger_V7 (
   void 
);
```

```csharp
int DetachDebugger_V7 ();
```

## <a name="return-value"></a>Valore restituito

Un'implementazione deve sempre restituire `E_NOTIMPL`.

## <a name="remarks"></a>Note

> [!WARNING]
> A partire da Visual Studio 2005, questo metodo non viene più usato e deve sempre restituire `E_NOTIMPL`.

Questo metodo viene chiamato quando il debugger viene chiuso in modo imprevisto. Quando questo metodo viene chiamato, la Germania deve essere ripreso il programma come se l'utente è disconnesso da esso. Nessun evento di debug più deve essere inviato. Il programma deve essere in uno stato in cui è associabile da un'altra istanza del debugger.

## <a name="see-also"></a>Vedere anche

[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)