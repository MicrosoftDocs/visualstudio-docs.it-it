---
description: Specifica il motivo per cui il motore di debug (DE) deve connettersi a un nodo del programma.
title: ATTACH_REASON | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ATTACH_REASON
helpviewer_keywords:
- ATTACH_REASON enumeration
ms.assetid: 159fb70b-a344-4ba6-9115-b7eaa16e228f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9da162dd2c477d5b901be6c622e2456f44d26a35
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085429"
---
# <a name="attach_reason"></a>ATTACH_REASON
Specifica il motivo per cui il motore di debug (DE) deve connettersi a un nodo del programma.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_ATTACH_REASON {
    ATTACH_REASON_LAUNCH = 0x0001,
    ATTACH_REASON_USER   = 0x0002,
    ATTACH_REASON_AUTO   = 0x0003
};
typedef DWORD ATTACH_REASON;
```

```csharp
public enum enum_ATTACH_REASON {
    ATTACH_REASON_LAUNCH = 0x0001,
    ATTACH_REASON_USER   = 0x0002,
    ATTACH_REASON_AUTO   = 0x0003
};
```

## <a name="fields"></a>Campi
`ATTACH_REASON_AUTO`\
Connetti perché il processo è attualmente in modalità di debug.

`ATTACH_REASON_LAUNCH`\
Connettersi perché il processo è stato avviato.

`ATTACH_REASON_USER`\
Connessione a causa di una richiesta dell'utente.

## <a name="remarks"></a>Commenti
Questi valori vengono usati come parametro per i metodi di [connessione](../../../extensibility/debugger/reference/idebugengine2-attach.md) e di [associazione](../../../extensibility/debugger/reference/idebugprogramex2-attach.md) .

## <a name="requirements"></a>Requisiti
Intestazione: msdbg. h

Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [Attach](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)
