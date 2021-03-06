---
description: Crea una copia di un oggetto dati specifico dell'analizzatore di espressioni (EE).
title: 'IPropertyProxyEESide:: CreateReplacementObject | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::CreateReplacementObject
helpviewer_keywords:
- IPropertyProxyEESide::CreateReplacementObject
ms.assetid: 0cfe79b8-c3f1-48b0-a225-e39dee2c92fe
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 460052ceb9f2f90a5123f4cc646682919f96dc94
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105082582"
---
# <a name="ipropertyproxyeesidecreatereplacementobject"></a>IPropertyProxyEESide::CreateReplacementObject
Crea una copia di un oggetto dati specifico dell'analizzatore di espressioni (EE).

## <a name="syntax"></a>Sintassi

```cpp
HRESULT CreateReplacementObject(
   IEEDataStorage*  dataIn,
   IEEDataStorage** dataOut
);
```

```csharp
int CreateReplacementObject(
   IEEDataStorage     dataIn,
   out IEEDataStorage dataOut
);
```

## <a name="parameters"></a>Parametri
`dataIn`\
in Oggetto [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) che contiene i dati da copiare.

`dataOut`\
[out] Restituisce un nuovo oggetto `IEEDataStorage`.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 A questo metodo viene assegnato un oggetto [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) che rappresenta una matrice di byte. Questo oggetto dati in ingresso non è in genere implementato da EE. Tuttavia, l'oggetto restituito da questo metodo viene sempre implementato da EE, che consente all'EE di implementare l' `IEEDataStorage` interfaccia su qualsiasi classe desiderata.

 Si noti che i dati forniti dall'oggetto in ingresso `IEEDataStorage` devono essere gli stessi dati nell'oggetto in uscita `IEEDataStorage` .

## <a name="see-also"></a>Vedi anche
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
