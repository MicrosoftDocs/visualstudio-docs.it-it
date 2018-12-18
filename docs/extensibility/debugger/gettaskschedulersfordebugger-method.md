---
title: Metodo GetTaskSchedulersForDebugger | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- GetTaskSchedulersForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d5d0b78a4f115d1ba07848db914289c35034d465
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="gettaskschedulersfordebugger-method"></a>Metodo GetTaskSchedulersForDebugger
Recupera una matrice di tutti <xref:System.Threading.Tasks.TaskScheduler> gli oggetti che sono attualmente attivi.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib (in mscorlib. dll)  
  
 Poiché è possibile accedere a questo membro interno di .NET Framework, la sintassi seguente viene fornita in comune Intermediate Language (CIL).  
  
## <a name="syntax"></a>Sintassi  
  
```  
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed  
```  
  
## <a name="return-value"></a>Valore restituito  
 Una matrice di tutti <xref:System.Threading.Tasks.TaskScheduler> gli oggetti che sono attualmente attivi in questo <xref:System.AppDomain>.  
  
## <a name="remarks"></a>Note  
 Questo metodo non è thread-safe e non deve essere utilizzato contemporaneamente altre istanze di <xref:System.Threading.Tasks.TaskScheduler>. Si deve essere chiamato da un debugger solo quando il debugger ha sospeso tutti gli altri thread.  
  
## <a name="see-also"></a>Vedere anche  
 [Classe TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md)