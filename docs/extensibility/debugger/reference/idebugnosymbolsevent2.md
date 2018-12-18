---
title: IDebugNoSymbolsEvent2 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugNoSymbolsEvent2 interface
ms.assetid: f6fb6388-47f6-4385-9ad5-95d62f9a7592
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bb7719ff66ac284d07da2ddfca25fe6898c93220
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugnosymbolsevent2"></a>IDebugNoSymbolsEvent2
Segnala il [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] dell'interfaccia utente per avvertire l'utente che non sono possibile trovare l'eseguibile avviato simboli del debugger.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugNoSymbolsEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Implementata dai motori di debug e utilizzato per il [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] dell'interfaccia utente del debugger.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll