---
title: IDebugComPlusSymbolProvider::GetAttributedClassesinModule Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider::GetAttributedClassesinModule
- GetAttributedClassesinModule
ms.assetid: d8b087f3-1d32-4570-9eb0-7e0f7b051bc8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 408aa2f373ab296394a0181014c16b1697fdf9ae
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733922"
---
# <a name="idebugcomplussymbolprovidergetattributedclassesinmodule"></a>IDebugComPlusSymbolProvider::GetAttributedClassesinModule
Recupera le classi con l'attributo specificato in un modulo specificato.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetAttributedClassesinModule (
    ULONG32            ulAppDomainID,
    GUID               guidModule,
    LPOLESTR           pstrAttribute,
    IEnumDebugFields** ppEnum
);
```

```csharp
int GetAttributedClassesinModule (
    uint                 ulAppDomainID,
    Guid                 guidModule,
    string               pstrAttribute,
    out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Parametri
`ulAppDomainID`\
[in] Identificatore del dominio applicazione.

`guidModule`\
[in] Identificatore univoco del modulo.

`pstrAttribute`\
[in] Stringa dell'attributo.

`ppEnum`\
[fuori] Restituisce un'enumerazione delle classi con attributi.

## <a name="return-value"></a>Valore restituito
In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrato come implementare questo metodo per un **CDebugSymbolProvider** oggetto che espone il [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) interfaccia.

```cpp
HRESULT CDebugSymbolProvider::GetAttributedClassesinModule(
    ULONG32 ulAppDomainID,
    GUID guidModule,
    __in_z LPOLESTR pstrAttribute,
    IEnumDebugFields** ppEnum
)
{
    HRESULT hr = S_OK;
    CComPtr<CModule> pModule;
    CComPtr<IMetaDataImport> pMetaData;
    Module_ID idModule(ulAppDomainID, guidModule);
    const void* pUnused;
    ULONG cbUnused;
    HCORENUM hEnum = 0;
    ULONG cTypeDefs = 0;
    ULONG cEnum;
    DWORD iTypeDef = 0;
    mdTypeDef* rgTypeDefs = NULL;
    IDebugField** rgFields = NULL;
    DWORD ctField = 0;
    CEnumDebugFields* pEnumFields = NULL;

    METHOD_ENTRY( CDebugSymbolProvider::GetAttributedClassesinModule );

    IfFalseGo( pstrAttribute && ppEnum , E_INVALIDARG );
    IfFailGo( GetModule( idModule, &pModule ) );
    pModule->GetMetaData( &pMetaData );

    IfFailGo( pMetaData->EnumTypeDefs( &hEnum,
                                       NULL,
                                       0,
                                       &cTypeDefs ) );

    IfFailGo( pMetaData->CountEnum( hEnum, &cEnum ) );
    pMetaData->CloseEnum(hEnum);
    hEnum = NULL;

    IfNullGo( rgTypeDefs = new mdTypeDef[cEnum], E_OUTOFMEMORY );
    IfNullGo( rgFields = new IDebugField * [cEnum], E_OUTOFMEMORY );

    IfFailGo( pMetaData->EnumTypeDefs( &hEnum,
                                       rgTypeDefs,
                                       cEnum,
                                       &cTypeDefs ) );

    for ( iTypeDef = 0; iTypeDef < cTypeDefs; iTypeDef++)
    {

        if (pMetaData->GetCustomAttributeByName( rgTypeDefs[iTypeDef],
                pstrAttribute,
                &pUnused,
                &cbUnused ) == S_OK)
        {
            if (CreateClassType( idModule, rgTypeDefs[iTypeDef], rgFields + ctField) == S_OK)
            {
                ctField++;
            }
            else
            {
                ASSERT(!"Failed to Create Attributed Class");
            }
        }
    }

    IfNullGo( pEnumFields = new CEnumDebugFields, E_OUTOFMEMORY );
    IfFailGo( pEnumFields->Initialize(rgFields, ctField) );
    IfFailGo( pEnumFields->QueryInterface( __uuidof(IEnumDebugFields),
                                           (void**) ppEnum ) );

Error:

    METHOD_EXIT( CDebugSymbolProvider::GetAttributedClassesinModule, hr );

    DELETERG( rgTypeDefs );

    for ( iTypeDef = 0; iTypeDef < ctField; iTypeDef++)
    {
        RELEASE( rgFields[iTypeDef] );
    }

    DELETERG( rgFields );
    RELEASE( pEnumFields );

    return hr;
}
```

## <a name="see-also"></a>Vedere anche
- [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
