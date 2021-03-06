---
description: Consente a un motore di debug di eseguire l'override del comportamento predefinito dell'interfaccia utente di Visual Studio quando si termina una sessione di debug.
title: IDebugProgramDestroyEventFlags2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgramDestroyEventFlags2 interface
ms.assetid: d384ff71-dc71-40b9-a871-801f8b6a3418
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6cb54b3a88255f9102f617298ff23c3e117d3cdd
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084233"
---
# <a name="idebugprogramdestroyeventflags2"></a>IDebugProgramDestroyEventFlags2
Consente a un motore di debug di eseguire l'override del comportamento predefinito dell' [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interfaccia utente quando si termina una sessione di debug.

## <a name="syntax"></a>Sintassi

```
IDebugProgramDestroyEventFlags2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Questa interfaccia viene implementata dai motori di debug. È utile per gli host che potrebbero creare ed eliminare più programmi durante il ciclo di vita di un processo.

## <a name="methods"></a>Metodi
 La tabella seguente illustra i metodi di `IDebugProgramDestroyEventFlags2` .

|Metodo|Descrizione|
|------------|-----------------|
|[GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)|Recupera i flag del programma Destroy.|

## <a name="remarks"></a>Commenti
 Il comportamento predefinito dell' [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interfaccia utente è tornare alla modalità progettazione dopo che tutti i programmi hanno inviato un evento di eliminazione del programma. Questa interfaccia consente a un motore di debug di modificare tale comportamento.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
