---
description: Crea un'istanza di un motore di debug nel server.
title: 'IDebugCoreServer3:: CreateInstanceInServer | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::CreateInstanceInServer
helpviewer_keywords:
- IDebugCoreServer3::CreateInstanceInServer
ms.assetid: 76f36bae-f6ab-413c-a8a9-8808bfeba05b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3511e67300725dc46e6d0e3978b2cb034b92d84e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058690"
---
# <a name="idebugcoreserver3createinstanceinserver"></a>IDebugCoreServer3::CreateInstanceInServer
Crea un'istanza di un motore di debug nel server.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT CreateInstanceInServer(
   LPCWSTR  szDll,
   WORD     wLangId,
   REFCLSID clsidObject,
   REFIID   riid,
   void**   ppvObject
);
```

```csharp
int CreateInstanceInServer(
   string     szDll,
   ushort     wLangID,
   ref Guid   clsidObject,
   ref Guid   riid,
   out IntPtr ppvObject
);
```

## <a name="parameters"></a>Parametri
`szDll`\
in Percorso della dll che implementa il CLSID specificato nel `clsidObject` parametro. Se è `NULL` , `CoCreateInstance` viene chiamata la funzione com.

`wLangId`\
in Impostazioni locali del motore di debug. Può essere 0 se il metodo [setlocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md) non deve essere chiamato.

`clsidObject`\
in CLSID del motore di debug da creare.

`riid`\
in ID di interfaccia dell'interfaccia specifica da recuperare dall'oggetto classe.

`ppvObject`\
[out] `IUnknown` interfaccia dall'oggetto di cui è stata creata un'istanza. Eseguire il cast o il marshalling di questo oggetto nell'interfaccia desiderata.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
- [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)
