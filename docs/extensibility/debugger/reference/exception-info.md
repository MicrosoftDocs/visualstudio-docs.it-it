---
description: Descrive un'eccezione o un errore di Run-Time generato dal programma di cui è in corso il debug.
title: EXCEPTION_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EXCEPTION_INFO
helpviewer_keywords:
- EXCEPTION_INFO structure
ms.assetid: d046957a-b97d-420b-b46b-c67cbaef709e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1ec97b56cc7fca8c2185d7180a8d34e87b084b11
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059470"
---
# <a name="exception_info"></a>EXCEPTION_INFO
Descrive un'eccezione o un errore di Run-Time generato dal programma di cui è in corso il debug.

## <a name="syntax"></a>Sintassi

```cpp
typedef struct tagEXCEPTION_INFO {
    IDebugProgram2* pProgram;
    BSTR            bstrProgramName;
    BSTR            bstrExceptionName;
    DWORD           dwCode;
    EXCEPTION_STATE dwState;
    GUID            guidType;
} EXCEPTION_INFO;
```

```csharp
public struct EXCEPTION_INFO {
    public IDebugProgram2 pProgram;
    public string         bstrProgramName;
    public string         bstrExceptionName;
    public uint           dwCode;
    public uint           dwState;
    public Guid           guidType;
};
```

## <a name="members"></a>Members
`pProgram`\
Oggetto [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) che rappresenta il programma in cui si è verificata l'eccezione.

`bstrProgramName`\
Nome del programma in cui si è verificata l'eccezione.

`bstrExceptionName`\
Nome dell'eccezione.

`dwCode`\
Codice di identificazione per l'eccezione o l'errore di run-time.

`dwState`\
Valore dell'enumerazione [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md) che definisce lo stato dell'eccezione.

`guidType`\
Identificatore della lingua del GUID, `guidLang` ovvero o `guidEng` .

## <a name="remarks"></a>Commenti
Questa struttura viene passata come parametro ai metodi [seexception](../../../extensibility/debugger/reference/idebugengine2-setexception.md) e [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md) . Questa struttura viene passata anche al metodo [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) da compilare.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg. h

Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)
- [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)
- [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)
