---
description: Recupera le informazioni sul visualizzatore per questo tipo di proprietà per creare un'istanza di tale visualizzatore.
title: 'IPropertyProxyEESide:: GetManagedViewerCreationData | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
helpviewer_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
ms.assetid: c4eb4d60-8816-4d52-bc8d-dffd4f066499
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fc0ab85a3000db2090e9679b0ae065b9280f20cf
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105082504"
---
# <a name="ipropertyproxyeesidegetmanagedviewercreationdata"></a>IPropertyProxyEESide::GetManagedViewerCreationData
Recupera le informazioni sul visualizzatore per questo tipo di proprietà per creare un'istanza di tale visualizzatore.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetManagedViewerCreationData(
   BSTR*                  assemName,
   IEEDataStorage**       assemBytes,
   IEEDataStorage**       assemPdb,
   BSTR*                  className,
   ASSEMBLYLOCRESOLUTION* alr,
   BOOL*                  replacementOk
);
```

```csharp
int GetManagedViewerCreationData(
   out string                     assemName,
   out IEEDataStorage             assemBytes,
   out IEEDataStorage             assemPdb,
   out string                     className,
   out enum_ASSEMBLYLOCRESOLUTION alr,
   out int                        replacementOk
);
```

## <a name="parameters"></a>Parametri
`assemName`\
out Restituisce il nome dell'assembly che contiene questo oggetto.

`assemBytes`\
out Restituisce un oggetto [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) contenente i byte dell'assembly di questo oggetto (si tratta di un valore null se non sono disponibili byte).

`assemPdb`\
out Restituisce un `IEEDataStorage` oggetto contenente le informazioni sull'archivio simboli per questo oggetto. si tratta di un valore null se non è disponibile alcun archivio dei simboli.

`className`\
out Restituisce il nome della classe contenente questo oggetto.

`alr`\
out Restituisce un valore dall'enumerazione [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md) che indica la posizione dell'assembly.

`replacementOk`\
out Restituisce un valore diverso da zero ( `TRUE` ) se il valore di questo oggetto può essere modificato; zero ( `FALSE` ) se l'oggetto è di sola lettura.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Questo metodo viene usato dai visualizzatori di tipi per creare un'istanza di un visualizzatore gestito.

## <a name="see-also"></a>Vedi anche
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
