---
description: Recupera la stringa associata a questa proprietà e la archivia in un buffer fornito dall'utente.
title: 'IDebugProperty3:: GetStringChars | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::GetStringChars
helpviewer_keywords:
- IDebugProperty3::GetStringChars
ms.assetid: 832c37f3-85cb-4227-8ab2-f27a80eafe90
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 21baaa5e5eb7446636fcbab9038db87444d50017
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105083934"
---
# <a name="idebugproperty3getstringchars"></a>IDebugProperty3::GetStringChars
Recupera la stringa associata a questa proprietà e la archivia in un buffer fornito dall'utente.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetStringChars(
    ULONG  buflen,
    WCHAR* rgString,
    ULONG* pceltFetched
);
```

```csharp
int GetStringChars(
    uint       buflen,
    out string rgString,
    out uint   pceltFetched
);
```

## <a name="parameters"></a>Parametri
`buflen`\
in Numero massimo di caratteri che il buffer fornito dall'utente può memorizzare.

`rgString`\
out Restituisce la stringa.

 [Solo C++], `rgString` è un puntatore a un buffer che riceve i caratteri Unicode della stringa. Il buffer deve contenere almeno `buflen` caratteri (non byte).

`pceltFetched`\
out Dove viene restituito il numero di caratteri effettivamente archiviati nel buffer. (Può essere `NULL` in C++).

## <a name="return-value"></a>Valore restituito
Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
In C++ è necessario prestare attenzione per garantire che il buffer sia costituito da almeno `buflen` caratteri Unicode. Si noti che un carattere Unicode ha una lunghezza di 2 byte.

> [!NOTE]
> In C++, la stringa restituita non include un carattere null di terminazione. Se specificato, `pceltFetched` in viene specificato il numero di caratteri nella stringa.

## <a name="example"></a>Esempio

```cpp
CStringW RetrievePropertyString(IDebugProperty2 *pPropInfo)
{
    CStringW returnString = L"";
    CComQIPtr<IDebugProperty3> pProp3 = pPropInfo->pProperty;
    If (pProp3 != NULL) {
        ULONG dwStrLen = 0;
        HRESULT hr;
        hr = pProp3->GetStringCharLength(&dwStrLen);
        if (SUCCEEDED(hr) && dwStrLen > 0) {
            ULONG dwRead;
            CStrBufW buf(returnString,dwStrLen,CStrBuf::SET_LENGTH);
            hr = pProp3->GetStringChars(dwStrLen,
                                        reinterpret_cast<WCHAR*>(static_cast<CStringW::PXSTR>(buf)),
                                        &dwRead);
        }
    }
    return(returnString);
}
```

## <a name="see-also"></a>Vedere anche
- [GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
