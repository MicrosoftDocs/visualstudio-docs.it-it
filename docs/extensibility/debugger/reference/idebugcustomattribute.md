---
description: Questa interfaccia rappresenta un attributo personalizzato e può fornire il nome, l'elemento padre e il tipo di classe dell'attributo.
title: IDebugCustomAttribute | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute
helpviewer_keywords:
- IDebugCustomAttribute interface
ms.assetid: c5ae41e9-00b9-4cca-871d-b8de9ef390d1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5b96f4330371e8fb18b75a6ad6f17d61cccd3812
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105095433"
---
# <a name="idebugcustomattribute"></a>IDebugCustomAttribute
Questa interfaccia rappresenta un attributo personalizzato e può fornire il nome, l'elemento padre e il tipo di classe dell'attributo.

## <a name="syntax"></a>Sintassi

```
IDebugCustomAttribute : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un provider di simboli implementa questa interfaccia per supportare gli attributi personalizzati associati a un simbolo. Viene in genere implementato nel relativo oggetto.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Una chiamata a [Next](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md) restituisce questa interfaccia. Una chiamata al metodo [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md) restituisce l'interfaccia [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) .

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 La tabella seguente illustra i metodi di `IDebugCustomAttribute` .

|Metodo|Descrizione|
|------------|-----------------|
|[GetParentField](../../../extensibility/debugger/reference/idebugcustomattribute-getparentfield.md)|Ottiene il campo a cui è associato l'attributo corrente.|
|[GetAttributeTypeField](../../../extensibility/debugger/reference/idebugcustomattribute-getattributetypefield.md)|Ottiene il tipo di classe di attributi personalizzati.|
|[GetName](../../../extensibility/debugger/reference/idebugcustomattribute-getname.md)|Ottiene il nome dell'attributo personalizzato.|
|[GetAttributeBytes](../../../extensibility/debugger/reference/idebugcustomattribute-getattributebytes.md)|Ottiene le informazioni sugli attributi come BLOB di byte.|

## <a name="remarks"></a>Commenti
 Un attributo personalizzato è una struttura per C# che fornisce metadati personalizzati associati a una classe o a un metodo specifico.

## <a name="requirements"></a>Requisiti
 Intestazione: sh. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce del provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
