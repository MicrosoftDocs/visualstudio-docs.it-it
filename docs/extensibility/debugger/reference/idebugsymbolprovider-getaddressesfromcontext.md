---
description: Questo metodo esegue il mapping di un contesto di documento in una matrice di indirizzi di debug.
title: 'IDebugSymbolProvider:: GetAddressesFromContext | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetAddressesFromContext
helpviewer_keywords:
- IDebugSymbolProvider::GetAddressesFromContext method
ms.assetid: a3124883-a255-4543-a5ec-e1c7a97beb69
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e9748e2e2cf7f82724398afe25624f2d1762363c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087132"
---
# <a name="idebugsymbolprovidergetaddressesfromcontext"></a>IDebugSymbolProvider::GetAddressesFromContext
Questo metodo esegue il mapping di un contesto di documento in una matrice di indirizzi di debug.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetAddressesFromContext( 
   IDebugDocumentContext2* pDocContext,
   BOOL                    fStatmentOnly,
   IEnumDebugAddresses**   ppEnumBegAddresses,
   IEnumDebugAddresses**   ppEnumEndAddresses
);
```

```csharp
int GetAddressesFromContext(
   IDebugDocumentContext2  pDocContext,
   bool                    fStatmentOnly,
   out IEnumDebugAddresses ppEnumBegAddresses,
   out IEnumDebugAddresses ppEnumEndAddresses
);
```

## <a name="parameters"></a>Parametri
`pDocContext`\
in Contesto del documento.

`fStatmentOnly`\
in Se TRUE, limita gli indirizzi di debug a una singola istruzione.

`ppEnumBegAddresses`\
out Restituisce un enumeratore per gli indirizzi di debug iniziali associati all'istruzione o alla riga.

`ppEnumEndAddresses`\
out Restituisce un enumeratore [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md) per gli indirizzi di debug finali associati a questa istruzione o riga.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Un contesto di documento in genere indica un intervallo di righe di origine. Questo metodo fornisce gli indirizzi di debug iniziale e finale associati a queste righe. Alcuni linguaggi consentono istruzioni che si estendono su più righe o righe che contengono più di un'istruzione. Questo metodo fornisce un flag per limitare gli indirizzi di debug a una singola istruzione.

 È possibile che una singola istruzione disponga di più indirizzi di debug, come nel caso di modelli.

## <a name="see-also"></a>Vedi anche
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
