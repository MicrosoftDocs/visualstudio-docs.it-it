---
title: IDebugProgramDestroyEventFlags2 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugProgramDestroyEventFlags2 interface
ms.assetid: d384ff71-dc71-40b9-a871-801f8b6a3418
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f6b57206159ce00fbb79e9f9af1a6353588df76c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogramdestroyeventflags2"></a>IDebugProgramDestroyEventFlags2
Consente di eseguire l'override del comportamento predefinito di un motore di debug di [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] dell'interfaccia utente quando si termina una sessione di debug.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugProgramDestroyEventFlags2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Questa interfaccia è implementata dai motori di debug. È utile per gli host che potrebbero creare e distruggere più programmi in base alla durata di un processo.  
  
## <a name="methods"></a>Metodi  
 Nella tabella seguente sono illustrati i metodi di `IDebugProgramDestroyEventFlags2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)|Recupera il programma destroy flag.|  
  
## <a name="remarks"></a>Note  
 Il comportamento predefinito del [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] dell'interfaccia utente è per tornare alla modalità progettazione dopo che tutti i programmi sono inviate a un programma evento eliminazione. Questa interfaccia consente a un motore di debug per modificare questo comportamento.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll