---
description: Recupera l'identificatore univoco per una metrica dell'analizzatore di espressioni in base al nome.
title: 'IDebugSettingsCallback2:: GetEEMetricGuid | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::GetEEMetricGuid
ms.assetid: 3d70c19a-595d-44f1-a7b3-a0cf8f15e371
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 45e858cf78e8b0acf7e50a95d73cd06523396bc1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071376"
---
# <a name="idebugsettingscallback2geteemetricguid"></a>IDebugSettingsCallback2::GetEEMetricGuid
Recupera l'identificatore univoco per una metrica dell'analizzatore di espressioni in base al nome.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetEEMetricGuid(
   REFGUID guidLang,
   REFGUID guidVendor,
   LPCWSTR pszMetric,
   GUID*   pguidValue
);
```

```csharp
HRESULT GetEEMetricGuid(
   ref Guid guidLang,
   ref Guid guidVendor,
   string   pszMetric,
   out Guid pguidValue
);
```

## <a name="parameters"></a>Parametri
`guidLang`\
in Identificatore univoco del linguaggio di programmazione.

`guidVendor`\
in Identificatore univoco del fornitore.

`pszMetric`\
in Nome della metrica.

`pguidValue`\
out Restituisce l'identificatore univoco della metrica.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)
