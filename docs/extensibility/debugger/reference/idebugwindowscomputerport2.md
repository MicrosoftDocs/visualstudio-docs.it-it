---
title: IDebugWindowsComputerPort2 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugWindowsComputerPort2 interface
ms.assetid: 25f327b8-0303-4268-88d1-74df630436aa
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9d7482adf6405d04522cbc3137be25c7a5e18b2a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugwindowscomputerport2"></a>IDebugWindowsComputerPort2
Consente di eseguire query per informazioni relative al computer di destinazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugWindowsComputerPort2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Questa interfaccia viene implementata dagli oggetti porta del gestore di sessione di debug.  
  
## <a name="methods"></a>Metodi  
 Nella tabella seguente sono illustrati i metodi di `IDebugWindowsComputerPort2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetComputerInfo](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md)|Recupera le informazioni relative al computer in cui il debugger in esecuzione.|  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll