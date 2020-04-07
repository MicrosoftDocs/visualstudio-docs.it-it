---
title: proprietà PORT_SUPPLIER_DESCRIPTION_FLAGS . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- PORT_SUPPLIER_DESCRIPTION_FLAGS enumeration
ms.assetid: 5acee0ee-3a20-41c9-a7dc-0dadae6a5ba5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 26022098eb4233186a1442bde38fe4325accfdd1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713987"
---
# <a name="port_supplier_description_flags"></a>PORT_SUPPLIER_DESCRIPTION_FLAGS

Definisce i metadati che possono essere recuperati su un fornitore di porta.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_PORT_SUPPLIER_DESCRIPTION_FLAGS
{
    PSDFLAG_SHOW_WARNING_ICON = 0x1
};
typedef DWORD PORT_SUPPLIER_DESCRIPTION_FLAGS;
```

```csharp
public enum enum_PORT_SUPPLIER_DESCRIPTION_FLAGS
{
    PSDFLAG_SHOW_WARNING_ICON = 0x1
};
```

## <a name="fields"></a>Campi

`PSDFLAG_SHOW_WARNING_ICON`\
Se selezionata, l'icona di avviso verrà visualizzata nell'interfaccia utente.

## <a name="remarks"></a>Osservazioni

Questa enumerazione viene restituita dal [GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md) metodo.

## <a name="requirements"></a>Requisiti

Intestazione: Msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche

- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetDescrizione](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)
