---
description: Determina l'esistenza di un attributo personalizzato per questo campo e, se esistente, restituisce le informazioni sugli attributi.
title: IDebugCustomAttributeQuery2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2
helpviewer_keywords:
- IDebugCustomAttributeQuery interface
- IDebugCustomAttributeQuery2 interface
ms.assetid: 7cfa23e4-a05a-47a3-af6c-bd40c655014b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 62461cbdbfe373f6c3d45569564e611efdd6f452
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102160225"
---
# <a name="idebugcustomattributequery2"></a>IDebugCustomAttributeQuery2
Determina l'esistenza di un attributo personalizzato per questo campo e, se esistente, restituisce le informazioni sugli attributi.

## <a name="syntax"></a>Sintassi

```
IDebugCustomAttributeQuery2 : IDebugCustomAttributeQuery
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un provider di simboli implementa questa interfaccia sullo stesso oggetto che implementa [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) per supportare gli attributi personalizzati.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Usare [QueryInterface](/cpp/atl/queryinterface) per ottenere questa interfaccia dall'interfaccia [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) .

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 La tabella seguente illustra i metodi dell'interfaccia **IDebugCustomAttributeQuery** .

|Metodo|Descrizione|
|------------|-----------------|
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)|Determina se un attributo personalizzato esiste per nome.|
|[GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md)|Ottiene le informazioni sugli attributi per l'attributo personalizzato specificato.|

 Oltre ai metodi **IDebugCustomAttributeQuery** , `IDebugCustomAttributeQuery2` implementa il metodo seguente:

|Metodo|Descrizione|
|------------|-----------------|
|[EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)|Ottiene un enumeratore per tutti gli attributi personalizzati collegati a questo campo.|

## <a name="remarks"></a>Commenti
 Il metodo [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) può restituire un enumeratore per tutti gli attributi personalizzati definiti per questo campo.

## <a name="requirements"></a>Requisiti
 Intestazione: sh. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce del provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
