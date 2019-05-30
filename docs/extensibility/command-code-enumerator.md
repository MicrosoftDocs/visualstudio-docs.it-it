---
title: Enumeratore di codice di comando | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command code enumerator
- source control plug-ins, command code enumeration
ms.assetid: 5d2c360c-59e4-4da8-bcb4-dd07c7441e40
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f4ec14c15bbd0aa6340e30e3156e714ba5f9e074
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66334960"
---
# <a name="command-code-enumerator"></a>Enumeratore di codice di comando
Questo enumeratore viene utilizzato nelle opzioni per la [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) e il [SccPopulateList](../extensibility/sccpopulatelist-function.md)per indicare il comando per il quale vengono specificate le opzioni.

## <a name="syntax"></a>Sintassi

```
enum SCCCOMMAND {
   SCC_COMMAND_GET,
   SCC_COMMAND_CHECKOUT,
   SCC_COMMAND_CHECKIN,
   SCC_COMMAND_UNCHECKOUT,
   SCC_COMMAND_ADD,
   SCC_COMMAND_REMOVE,
   SCC_COMMAND_DIFF,
   SCC_COMMAND_HISTORY,
   SCC_COMMAND_RENAME,
   SCC_COMMAND_PROPERTIES,
   SCC_COMMAND_OPTIONS
};
```

## <a name="members"></a>Membri
SCC_COMMAND_GET corrispondente per il [SccGet](../extensibility/sccget-function.md).

SCC_COMMAND_CHECKOUT corrispondente per il [SccCheckout](../extensibility/scccheckout-function.md).

SCC_COMMAND_CHECKIN corrispondente per il [SccCheckin](../extensibility/scccheckin-function.md).

SCC_COMMAND_UNCHECKOUT corrispondente per il [SccUncheckout](../extensibility/sccuncheckout-function.md).

SCC_COMMAND_ADD corrispondente per il [SccAdd](../extensibility/sccadd-function.md).

SCC_COMMAND_REMOVE corrispondente per il [SccRemove](../extensibility/sccremove-function.md).

SCC_COMMAND_DIFF corrispondente per il [SccDiff](../extensibility/sccdiff-function.md).

SCC_COMMAND_HISTORY corrispondente per il [SccHistory](../extensibility/scchistory-function.md).

SCC_COMMAND_RENAME corrispondente per il [SccRename](../extensibility/sccrename-function.md).

SCC_COMMAND_PROPERTIES corrispondente per il [SccProperties](../extensibility/sccproperties-function.md).

SCC_COMMAND_OPTIONS corrispondente per il [SccSetOption](../extensibility/sccsetoption-function.md).

## <a name="see-also"></a>Vedere anche
- [Plug-in controllo codice sorgente](../extensibility/source-control-plug-ins.md)
- [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)
- [SccPopulateList](../extensibility/sccpopulatelist-function.md)
