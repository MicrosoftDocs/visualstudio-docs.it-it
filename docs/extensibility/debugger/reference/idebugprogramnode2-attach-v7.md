---
title: IDebugProgramNode2::Attach_V7 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramNode2::Attach
helpviewer_keywords:
- IDebugProgramNode2::Attach_V7
- IDebugProgramNode2::Attach
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e77acd4091abd7da5c9d302fb4c4dd6eb66af379
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogramnode2attachv7"></a>IDebugProgramNode2::Attach_V7

> [!Note]
> DEPRECATO. NON USARE.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Attach_V7 (
   IDebugProgram2*       pMDMProgram,
   IDebugEventCallback2* pCallback,
   DWORD                 dwReason
);
```

```csharp
int Attach_V7 (
   IDebugProgram2       pMDMProgram,
   IDebugEventCallback2 pCallback,
   uint                 dwReason
);
```

#### <a name="parameters"></a>Parametri

`pMDMProgram` [in] Il [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfaccia che rappresenta il programma a cui connettersi.

 `pCallback` [in] Il [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) interfaccia da utilizzare per inviare gli eventi di debug per il SDM.

 `dwReason` [in] Un valore di [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) enumerazione che specifica il motivo per il collegamento.

## <a name="return-value"></a>Valore restituito

Un'implementazione deve sempre restituire `E_NOTIMPL`.

## <a name="remarks"></a>Note

> [!WARNING]
> A partire da Visual Studio 2005, questo metodo non viene più usato e deve sempre restituire `E_NOTIMPL`. Vedere il [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) interfaccia per un approccio alternativo se il nodo programma deve indicare non è possibile collegare o se il nodo del programma è sufficiente impostare il programma `GUID`. In caso contrario, implementare il [collegamento](../../../extensibility/debugger/reference/idebugengine2-attach.md) metodo.

## <a name="prior-to-visual-studio-2005"></a>Prima di Visual Studio 2005

Questo metodo deve essere implementato solo se viene eseguita la Germania nello spazio degli indirizzi del programma sottoposto a debug. In caso contrario, questo metodo deve restituire `S_FALSE`.

Quando viene chiamato questo metodo, è necessario inviare la Germania il [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) oggetto evento, se questo non è già stato inviato per questa istanza del [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) interfaccia, nonché il [ IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) e [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) oggetti evento. Il [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) evento oggetto viene quindi inviato se il `dwReason` parametro `ATTACH_REASON_LAUNCH`.

La Germania, è necessario chiamare il [GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) metodo il [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) oggetto fornito dal [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) evento dell'oggetto e devono essere archiviati i GUID di tale programma nei dati dell'istanza per il `IDebugProgram2` oggetto implementato per la Germania.

## <a name="see-also"></a>Vedere anche

[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)  
[IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)  
[Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)  
[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)  
[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)  
[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)  
[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)  
[IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)  
[IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)  
[ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)