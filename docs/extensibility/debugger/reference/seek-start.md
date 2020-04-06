---
title: proprietà SEEK_START . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SEEK_START
helpviewer_keywords:
- SEEK_START enumeration
ms.assetid: 55bd8901-626e-428b-a263-23b14417f4c6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ca1c38027123ca5147a6a7ab1fa6a3f92966409a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713598"
---
# <a name="seek_start"></a>SEEK_START
Specifica la posizione da cui iniziare la ricerca in un flusso di disassembly.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_SEEK_START { 
   SEEK_START_BEGIN       = 0x0001,
   SEEK_START_END         = 0x0002,
   SEEK_START_CURRENT     = 0x0003,
   SEEK_START_CODECONTEXT = 0x0004,
   SEEK_START_CODELOCID   = 0x0005
};
typedef DWORD SEEK_START;
```

```csharp
public enum enum_SEEK_START { 
   SEEK_START_BEGIN       = 0x0001,
   SEEK_START_END         = 0x0002,
   SEEK_START_CURRENT     = 0x0003,
   SEEK_START_CODECONTEXT = 0x0004,
   SEEK_START_CODELOCID   = 0x0005
};
```

## <a name="fields"></a>Campi
 `SEEK_START_BEGIN`\
 Inizia la ricerca all'inizio del documento corrente.

 `SEEK_START_END`\
 Inizia la ricerca alla fine del documento corrente.

 `SEEK_START_CURRENT`\
 Inizia la ricerca nella posizione corrente del documento corrente.

 `SEEK_START_CODECONTEXT`\
 Inizia la ricerca in corrispondenza del contesto di codice specificato del documento corrente.

 `SEEK_START_CODELOCID`\
 Inizia la ricerca in corrispondenza dell'identificatore di posizione del codice specificato. Gli identificatori di posizione del codice vengono ottenuti chiamando [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md).

## <a name="remarks"></a>Osservazioni
 Passato come argomento al metodo [Seek.](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)
- [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)
