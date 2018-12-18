---
title: IDebugSourceServerModule | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugSourceServerModule interface
ms.assetid: 38213060-451d-46e6-8b4a-efc123e01a2c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5210b819d78bcec1cac5179ac679cf201279e9fc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugsourceservermodule"></a>IDebugSourceServerModule
Rappresenta le informazioni sul server di origine che è contenuti in un file PDB.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugSourceServerModule : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Questa interfaccia è implementata dai motori di debugger e usata dal debugger dell'interfaccia utente.  
  
## <a name="methods"></a>Metodi  
 Nella tabella seguente sono illustrati i metodi di `IDebugSourceServerModule`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetSourceServerData](../../../extensibility/debugger/reference/idebugsourceservermodule-getsourceserverdata.md)|Recupera una matrice di informazioni sul server di origine.|  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll