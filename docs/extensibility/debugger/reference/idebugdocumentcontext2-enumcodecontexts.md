---
title: IDebugDocumentContext2::EnumCodeContexts . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::EnumCodeContexts
helpviewer_keywords:
- IDebugDocumentContext2::EnumCodeContexts
ms.assetid: 627af69c-5cce-4e1d-8233-5f4d8dbc62e5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1a12e0ebbbf5c964da69c6bf6b1e7233487d6528
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731842"
---
# <a name="idebugdocumentcontext2enumcodecontexts"></a>IDebugDocumentContext2::EnumCodeContexts
Recupera un elenco di tutti i contesti di codice associati a questo contesto del documento.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT EnumCodeContexts(
    IEnumDebugCodeContexts2** ppEnumCodeCxts
);
```

```csharp
int EnumCodeContexts(
    out IEnumDebugCodeContexts2 ppEnumCodeCxts
);
```

## <a name="parameters"></a>Parametri
`ppEnumCodeCxts`\

## <a name="return-value"></a>Valore restituito
In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
Un singolo contesto di documento può generare più contesti di codice quando il documento utilizza modelli o file di inclusione.

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrato come `CDebugContext` implementare questo metodo per un oggetto semplice che espone il [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) interfaccia.

```cpp
HRESULT CDebugContext::EnumCodeContexts(IEnumDebugCodeContexts2 **ppEnumCodeCxts)
{
    HRESULT hr;

    // Check for a valid IEnumDebugCodeContexts2 interface pointer.
    if (ppEnumCodeCxts)
    {
        *ppEnumCodeCxts = NULL;

        // Create a CEnumDebugCodeContexts object.
        CComObject<CEnumDebugCodeContexts>* pEnum;
        hr = CComObject<CEnumDebugCodeContexts>::CreateInstance(&pEnum);
        assert(hr == S_OK);
        if (hr == S_OK)
        {
            // Get an IID_IDebugCodeContext2 interface.
            CComPtr<IDebugCodeContext2> spCodeCxt;
            hr = QueryInterface(IID_IDebugCodeContext2,
                                (void**)&spCodeCxt);
            assert(hr == S_OK);
            if (hr == S_OK)
            {
                // Initialize the code context enumerator with the
                // IDebugCodeContext2 information.
                IDebugCodeContext2* rgpCodeContext[] = { spCodeCxt.p };
                hr = pEnum->Init(rgpCodeContext,
                                 &(rgpCodeContext[1]),
                                 NULL,
                                 AtlFlagCopy);
                assert(hr == S_OK);
                if (hr == S_OK)
                {
                // Set the passed IEnumDebugCodeContexts2 pointer equal to the pointer
                // value of the created CEnumDebugCodeContexts object.
                hr = pEnum->QueryInterface(ppEnumCodeCxts);
                assert(hr == S_OK);
                }
            }

            // Otherwise, delete the CEnumDebugCodeContexts object.
            if (FAILED(hr))
            {
                delete pEnum;
            }
        }
    }
    else
    {
        hr = E_INVALIDARG;
    }

    return hr;
}
```

## <a name="see-also"></a>Vedere anche
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)
