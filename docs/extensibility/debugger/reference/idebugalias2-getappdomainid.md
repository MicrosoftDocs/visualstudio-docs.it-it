---
description: Recupera l'identificatore per il dominio dell'applicazione.
title: 'IDebugAlias2:: GetAppDomainId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetAppDomainId
- IDebugAlias2::GetAppDomainId
ms.assetid: 23581aaa-5a53-4859-b264-eca49fc44bcd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ee1caec6968f9a67a15a31c8064b7795a37a6829
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059106"
---
# <a name="idebugalias2getappdomainid"></a>IDebugAlias2::GetAppDomainId
Recupera l'identificatore per il dominio dell'applicazione.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetAppDomainId (
   ULONG32* pappDomainId
);
```

```csharp
int GetAppDomainId (
   out uint pappDomainId
);
```

## <a name="parameters"></a>Parametri
`pappDomainId`\
out Restituisce l'identificatore del dominio dell'applicazione.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 L'identificatore di dominio dell'applicazione cambia ogni volta che l'applicazione viene riavviata e viene creato un nuovo dominio applicazione.

## <a name="see-also"></a>Vedi anche
- [IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)
