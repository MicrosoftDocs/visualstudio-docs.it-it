---
description: Questa interfaccia rappresenta una raccolta di oggetti che implementano l'interfaccia IDebugAddress.
title: IEnumDebugAddresses | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses
helpviewer_keywords:
- IEnumDebugAddresses interface
ms.assetid: 5f6f6751-e6d8-4c5a-8e81-414b6e5d8cc5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 29b927f9b614e95be51bd285e36ab1e01c09f568
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105083128"
---
# <a name="ienumdebugaddresses"></a>IEnumDebugAddresses
Questa interfaccia rappresenta una raccolta di oggetti che implementano l'interfaccia [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .

## <a name="syntax"></a>Sintassi

```
IEnumDebugAdresses : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Questa interfaccia viene implementata dal provider di simboli per fornire set di oggetti che implementano l'interfaccia [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) . Si noti che non si tratta di un'enumerazione COM standard a causa della presenza del metodo [GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md) .

## <a name="notes-for-callers"></a>Note per i chiamanti
 Questa interfaccia viene restituita da [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md) e [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md).

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine vtable
 Questa interfaccia implementa i metodi seguenti.

|Metodo|Descrizione|
|------------|-----------------|
|[Avanti](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md)|Recupera il set successivo di oggetti [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) dall'enumerazione.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugaddresses-skip.md)|Ignora un numero specificato di voci.|
|[Reimpostazione](../../../extensibility/debugger/reference/ienumdebugaddresses-reset.md)|Reimposta l'enumerazione sulla prima voce.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugaddresses-clone.md)|Recupera una copia dell'enumerazione corrente.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md)|Recupera il numero di voci nell'enumerazione.|

## <a name="remarks"></a>Commenti
 Questa interfaccia viene in genere utilizzata dal motore di debug per determinare l'indirizzo appropriato da assegnare all'analizzatore di espressioni.

## <a name="requirements"></a>Requisiti
 Intestazione: sh. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce del provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)
- [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)
