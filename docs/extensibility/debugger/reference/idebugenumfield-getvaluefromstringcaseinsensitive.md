---
description: Questo metodo usa una ricerca senza distinzione tra maiuscole e minuscole per restituire il valore associato al nome di una costante di enumerazione.
title: 'IDebugEnumField:: GetValueFromStringCaseInsensitive | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive
helpviewer_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive method
ms.assetid: ef95b38e-d9b2-4fb5-a166-7c2e14641dc7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 80ded5237cfc0fe1b03ae5175ca0c92a188538ab
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065989"
---
# <a name="idebugenumfieldgetvaluefromstringcaseinsensitive"></a>IDebugEnumField::GetValueFromStringCaseInsensitive
Questo metodo usa una ricerca senza distinzione tra maiuscole e minuscole per restituire il valore associato al nome di una costante di enumerazione.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetValueFromStringCaseInsensitive(
   LPCOLESTR  pszValue,
   ULONGLONG* pvalue
);
```

```csharp
int GetValueFromStringCaseInsensitive(
   string    pszValue,
   out ulong pValue
);
```

## <a name="parameters"></a>Parametri
`pszValue`\
in Stringa che specifica il nome per il quale ottenere il valore. Si noti che per C++ si tratta di una stringa di caratteri wide.

`pValue`\
out Restituisce il valore numerico associato.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce `S_FALSE` , se il nome non fa parte dell'enumerazione o un codice di errore.

## <a name="remarks"></a>Commenti
 Questo metodo non fa distinzione tra maiuscole e minuscole. Se è necessaria una ricerca con distinzione tra maiuscole e minuscole, ad esempio in un linguaggio quale C++, in cui i nomi fanno distinzione tra maiuscole e minuscole, usare [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md).

## <a name="see-also"></a>Vedi anche
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
- [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)
