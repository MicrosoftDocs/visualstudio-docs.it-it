---
title: THREADPROPERTY_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADPROPERTY_FIELDS
helpviewer_keywords:
- THREADPROPERTY_FIELDS enumeration
ms.assetid: 5b88acb9-03ea-4c29-a788-f0087dccbe23
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 641687dbcfa6bf50ba9e848de589662d282d0c7b
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56715264"
---
# <a name="threadpropertyfields"></a>THREADPROPERTY_FIELDS
Specifica le informazioni su un thread deve essere recuperato.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_THREADPROPERTY_FIELDS { 
   TPF_ID           = 0x0001,
   TPF_SUSPENDCOUNT = 0x0002,
   TPF_STATE        = 0x0004,
   TPF_PRIORITY     = 0x0008,
   TPF_NAME         = 0x0010,
   TPF_LOCATION     = 0x0020,
   TPF_ALLFIELDS    = 0xffffffff
};
typedef DWORD THREADPROPERTY_FIELDS;
```

```csharp
public enum enum_THREADPROPERTY_FIELDS { 
   TPF_ID           = 0x0001,
   TPF_SUSPENDCOUNT = 0x0002,
   TPF_STATE        = 0x0004,
   TPF_PRIORITY     = 0x0008,
   TPF_NAME         = 0x0010,
   TPF_LOCATION     = 0x0020,
   TPF_ALLFIELDS    = 0xffffffff
};
```

## <a name="members"></a>Membri
 TPF_ID Initialize/usare la `dwThreadId` campo il [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) struttura.

 TPF_SUSPENDCOUNT Initialize/usare la `dwSuspendCount` campo il `THREADPROPERTIE`struttura S.

 TPF_STATE Initialize/usare la `dwThreadState` campo il `THREADPROPERTIE`struttura S.

 TPF_PRIORITY Initialize/usare la `bstrPriority` campo il `THREADPROPERTIE`struttura S.

 TPF_NAME Initialize/usare la `bstrName` campo il `THREADPROPERTIE`struttura S.

 TPF_LOCATION Initialize/usare la `bstrLocation` campo il `THREADPROPERTIE`struttura S.

 TPF_ALLFIELDS specifica tutti i campi.

## <a name="remarks"></a>Note
 Questi valori vengono passati come argomento per il [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) metodo per indicare quali campi della [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) struttura devono essere inizializzate.

 Questi valori possono essere usati anche nelle `dwFields` membro del `THREADPROPERTIES` struttura per indicare quali campi vengono usati e valido.

 Questi flag possono essere combinati con un bit per bit `OR`.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)
- [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)